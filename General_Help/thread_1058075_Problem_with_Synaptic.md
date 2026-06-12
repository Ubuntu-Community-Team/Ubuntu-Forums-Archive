---
title: "Problem with Synaptic"
date: 2009-02-02
forum: General Help
---

### Post by mbohacek on 2009-02-02
I am new to this Ubuntu thing and recently change the look of it to look like mac following the directions from: 
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

Everything looks great but now when I try to open synaptic package manager it says:

E: The package libgtk2.0-common needs to be reinstalled, but I can't find an archive for it.

E: Internal error opening cache (1). Please report.

Anyone know how to fix this problem?

---

### Post by fooman on 2009-02-02
open a terminal (applications > accessories > terminal) and try typing or copy/paste this command:

```
sudo apt-get --reinstall install libgtk2.0-common
```then press enter followed by your password.

see if that helps.

---

### Post by mbohacek on 2009-02-03
I put that command in the Terminal and it says:

sudo apt-get --reinstall install libgtk2.0-common
sudo: unable to resolve host bo-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libgtk2.0-common needs to be reinstalled, but I can't find an archive for it.

What can I do from here?

---

### Post by wolfen69 on 2009-02-03
download libgtk2.0-common [here]("http://lug.mtu.edu/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.14.4-0ubuntu1_all.deb"). click to install.

---

