# aws-vscode-dev-container

a vscode devcontainer for aws development

> Visual Studio Code Remote - Containers extension lets you use a Docker container as a full-featured development environment. It allows you to open any folder inside (or mounted into) a container and take advantage of Visual Studio Code's full feature set.

---

## Usage

To use this repo as a template for an AWS project

```sh
gh repo clone pfeilbr/aws-vscode-dev-container my-aws-project
cd my-aws-project
sam init
```

## Install into existing repo

```sh
mkdir -p .devcontainer
pushd .devcontainer
curl -O https://raw.githubusercontent.com/pfeilbr/aws-vscode-dev-container/master/.devcontainer/Dockerfile
curl -O https://raw.githubusercontent.com/pfeilbr/aws-vscode-dev-container/master/.devcontainer/devcontainer.json
popd
```

## Login with AWS SSO

* see <https://gist.github.com/pahud/ba133985e1cf3531c09b5ea553a72739>

```sh
mkdir ~/.bin && cd $_
wget https://raw.githubusercontent.com/pahud/vscode/main/.devcontainer/bin/aws-sso-credential-process && \
chmod +x aws-sso-credential-process


aws configure set credential_process ${HOME}/.bin/aws-sso-credential-process
touch ~/.aws/credentials && chmod 600 $_
aws configure sso --profile default
```

---

## Configuration

```sh
# aws credentials are mounted into the guest container via `~/.aws`s
# source=/home/ec2-user/.aws,target=/root/.aws
``

---

## TODO

* ...

---

## Files

* [`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json)
* [`.devcontainer/Dockerfile`](.devcontainer/Dockerfile)

---

## Resources

* [Developing inside a Container](https://code.visualstudio.com/docs/remote/containers)