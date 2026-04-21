# Docker aliases for NEMESIS

These scripts add shell aliases for NEMESIS executables when NEMESIS is installed via Docker. After the aliases are loaded, the executables can be run normally from your working directory, for example:

```sh
Nemesis <runname.nam> test.prc &
```

Each alias runs the matching executable inside the `nemesis-app` Docker image and mounts the current directory as `/data`:

```sh
docker run --rm -i -v "$(pwd)":/data -w /data nemesis-app <executable>
```

## Links

- Docker Hub:
- NEMESIS GitHub: https://github.com/nemesiscode/radtrancode.git

## Executable list

The aliases are generated from:

```sh
nemesis_executables.txt
```

To add or remove an executable, edit that file and rerun the script for your shell.

## Bash

Run this from a Bash terminal:

```sh
./add_nemesis_docker_aliases.sh
source ~/.bashrc
```

This updates `~/.bashrc`.

To update a different file:

```sh
./add_nemesis_docker_aliases.sh /path/to/.bashrc
```

## zsh on macOS

Run this from a zsh terminal:

```sh
./add_nemesis_docker_aliases.zsh
source ~/.zshrc
```

This updates `~/.zshrc`.

To update a different file:

```sh
./add_nemesis_docker_aliases.zsh /path/to/.zshrc
```

## C shell or tcsh

Run this from a `csh` or `tcsh` terminal:

```csh
./add_nemesis_docker_aliases.csh
source ~/.cshrc
```

This updates `~/.cshrc`.

To update a different file:

```csh
./add_nemesis_docker_aliases.csh /path/to/.cshrc
```

## Docker image name

By default, the scripts use the Docker image name `nemesis-app`.

To use a different image name, set `NEMESIS_DOCKER_IMAGE` before running the script:

```sh
NEMESIS_DOCKER_IMAGE=my-image-name ./add_nemesis_docker_aliases.sh
```

For zsh:

```zsh
NEMESIS_DOCKER_IMAGE=my-image-name ./add_nemesis_docker_aliases.zsh
```

For C shell or tcsh:

```csh
setenv NEMESIS_DOCKER_IMAGE my-image-name
./add_nemesis_docker_aliases.csh
```

## Notes

The scripts write aliases inside a managed block in your shell startup file. Rerunning a script refreshes that block instead of adding duplicate aliases.
