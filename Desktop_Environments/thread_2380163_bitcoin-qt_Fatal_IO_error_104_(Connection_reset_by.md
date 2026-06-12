---
title: "bitcoin-qt: Fatal IO error 104 (Connection reset by peer) on X server :54."
date: 2017-12-14
forum: Desktop Environments
---

### Post by Kirk Schnable on 2017-12-14
Hi all,

I have a virtual machine running Ubuntu 16.04.3 Server, MATE desktop, and x2go for remote access.  I recently set this VM up as a secure place to run my hot wallets for various blockchain coins.  I'm having some difficulty launching the Bitcoin Core wallet bitcoin-qt, and I'm not sure why.

I've tried the Linux binary from bitcoin.org, as well as the one off of the PPA ([https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin](https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin)) and they are both doing the same thing.

When I double click the program to launch it, nothing happens.

The PPA version yields this output when I try to run it from the terminal:
```
$ bitcoin-qt
 bitcoin-qt: Fatal IO error 104 (Connection reset by peer) on X server :54.
```

The official binary acts a bit differently, but same basic issue:
```
$ ./bitcoin-qt 
failed to get the current screen resources
The X11 connection broke: I/O error (code 1)
XIO:  fatal IO error 2 (No such file or directory) on X server ":54"
      after 383 requests (379 known processed) with 0 events remaining.
```

[IMG]https://iota.lt/d/cXxnz5CCEL/hklecMrd.png[/IMG]


Any suggestions on how I can troubleshoot further?

Thanks!

---

### Post by Kirk Schnable on 2017-12-21
I installed the XFCE desktop, however I am having the same issue there.  Could this be an issue with X2Go?  I'm not really sure what else to do to troubleshoot.

---

### Post by bben92 on 2018-08-14
Hello Kirk,

I have the same problem, on an Ubuntu Bionic server running Mate Desktop and X2Go, but with other applications (gns3-gui and wireshark). 
"[FONT=courier new]Gdk-Message : python: Fatal IO error 2 (Aucun fichier ou dossier de ce type) on X server :50.[/FONT]"

Did you solve your problem ? If so, how did you do ?

Thank you very much. 
Benoit.

---

