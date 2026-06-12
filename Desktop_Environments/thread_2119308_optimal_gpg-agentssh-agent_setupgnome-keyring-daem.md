---
title: "optimal gpg-agent/ssh-agent setup/gnome-keyring-daemon and eternal passphrase caching"
date: 2013-02-23
forum: Desktop Environments
---

### Post by Krusader47 on 2013-02-23
Problem: gnome-keyring-daemon stores passphrases eternally but is required for ubuntuone sync service! 
Solution (Ubuntu 12.04 LTS): 
First, remove xdg autostart scripts for gnome-keyring-manager gpg and ssh support below /etc/xdg/autostart. 
Then rewrite the following two files: 
/etc/X11/Xsession.d/90x11-common_ssh-agent: 

```
killall gpg-agent
killall ssh-agent
gpg-agent --daemon --enable-ssh-support --write-env-file "${HOME}/.gpg-agent-info"
. "${HOME}/.gpg-agent-info"
export GPG_AGENT_INFO
export SSH_AUTH_SOCK
```/etc/X11/Xsession.d/90gpg-agent: 

```
: ${GNUPGHOME=$HOME/.gnupg}
```
:KS

---

