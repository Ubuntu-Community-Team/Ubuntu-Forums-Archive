---
title: "error when sudo apt-get upgrade"
date: 2009-06-05
forum: General Help
---

### Post by kmaster228 on 2009-06-05
hi all whenever i enter sudo apt-get upgrade it downloads packages for a while then gives me this error message:

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems

```
... please help thank you:popcorn:

---

### Post by xavierp94 on 2009-06-05
> **kmaster228 said:**
> hi all whenever i enter sudo apt-get upgrade it downloads packages for a while then gives me this error message:

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems

```... please help thank you:popcorn:
Go to the terminal in Ubuntu and type the following:
```
sudo apt-get update
```

---

### Post by pastalavista on 2009-06-05
To install pubkey for repository, open the terminal and enter

```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
```
 
and then...

```
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -
```

and once more ```
sudo apt-get update
```

---

