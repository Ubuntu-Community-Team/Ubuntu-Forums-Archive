---
title: "What can I do: &quot;NO_PUBKEY 6AF0E1940624A220&quot;"
date: 2009-05-30
forum: General Help
---

### Post by fireflake78 on 2009-05-30
Every time I run "sudo apt-get update" in the Terminal, it says that that there is an error:

```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems

```

...and even when I run "apt-get update", it says this:

```

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Please give me a step-by-step set of instructions on how to fix this, as I am completely new to Ubuntu.

---

### Post by bacardiandwatermelon on 2009-05-30
For the keys..
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key number>[URL="http://ubuntuforums.org/showthread.php?t=1165924"]
[/URL]

```

When doing an update you need to run it as sudo...
```
sudo apt-get update
```

---

### Post by lindsay7 on 2009-05-30
gpg --keyserver subkeys.pgp.net --recv 6AF0E1940624A220


 gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

sudo apt-get update


type these commands in the terminal

---

### Post by Eskobar on 2009-09-03
Thanks for this..... worked pefectly!!!

---

