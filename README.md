# Remote SSH Commands

Simple GitHub Action to run a command on a remote server using SSH

# Required arguments

| Argument    | Description                                                                                                                                          |
|-------------|------------------------------------------------------------|
| `command`   | A list of commands to run on the destination server        |
| `host`      | The hostname of the server to connect to                   |
| `user`      | The username to use when connecting to the server          |
| `key`       | The private SSH key to use to authenticate to the server   |

## Example usage

```yml
name: Create Sandbox

on: pull_request

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest

    steps:
      - name: Install dependencies on server
        uses: trendyminds/github-actions-ssh@master
        with:
          command: |
            cd my-dir/
            composer install
            npm install
          host: ${{secrets.SSH_HOSTNAME}}
          user: ${{secrets.SSH_USERNAME}}
          key: ${{secrets.SSH_PRIVATE_KEY}}
          port: ${{secrets.SSH_PORT}}
          args: "-tt"
```
