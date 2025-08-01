# action-debug

Remote Access your GitHub Actions via Browser Based Terminal. Built using
[ttyd](https://github.com/tsl0922/ttyd) and
[Cloudflare tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/do-more-with-tunnels/trycloudflare/)

## TODO

- [ ] nixify + magic-nix-cache
  - why nixify? keep it groovy for macos and linux
- [ ] keep a non-nix way of doing it as well
  - does this require a new repo?
  - why? nix installation, nixpkgs fetching, eval takes time
- [ ] ngrok + tmate as the default option
  - why ngrok? tmate.io is
    [discontinued](https://github.com/tmate-io/tmate/issues/322#issuecomment-3083217834),
    need a way to expose a tcp port which cloudflared doesn't support
  - why tmate? because ttyd + browser can't be tmuxed
  - why still ttyd? backup/mobile
  - how is this method secure, ttyd method has a password?
    - https://github.com/mxschmitt/action-tmate
- [ ] navi cheats for gh cli commands for workflow_dispatch

## Features

- Debug your GitHub Actions by Remote Accessing your Github Action Runner
- Resume your Workflows afterwards

## Supported Operating Systems

- Linux
- macOS
- Windows

## Getting Started

```yaml
steps:
  - uses: phanirithvij/action-debug@main
```

The URL to access the terminal will be printed in Github Actions log.

The default credentials are:

| User: | Password: |
| ----- | --------- |
| admin | admin     |

## Set Credentials

Set credentials in "user:password" format

```yaml
steps:
  - uses: phanirithvij/action-debug@main
    with:
      credentials: "user:password" # Put one in github secrets
```

## Resume a workflow

If you want to resume a workflow, just create an empty file with the name
`continue` in the project directory by running `touch continue`.

## Credits

Intial version by https://github.com/fawazahmed0/action-debug licensed MIT.
