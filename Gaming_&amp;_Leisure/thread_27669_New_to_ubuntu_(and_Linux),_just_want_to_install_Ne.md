---
title: "New to ubuntu (and Linux), just want to install Nethack"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by captaincrisis on 2005-04-17
I'm sorry, I feel so stupid.  I have searched the forum and poked around "add/remove programs" but I cant work out how I download and install nethack through the proper package management system of ubuntu (if indeed I should be using that).

I tried "sudo apt-get install nethack".

If anybody has time to help I would be grateful.

:Embarassed:

---

### Post by Leif on 2005-04-17
The command you used is right, it just sounds like you need to enable some repositories - uncomment these lines in your /etc/apt/sources.list file :

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by captaincrisis on 2005-04-17
Thank you.  I followed your instructions (about uncommenting sources) and ubuntu came back suggesting that I needed to run apt-update.

I did "sudo apt-get update" and now things are working like I expected  - and most importantly of all Nethack is now installed!

Thanks again.

---

### Post by fng on 2005-04-18
Is there anyone here who allready got the amulet of Yendor?

---

### Post by captaincrisis on 2005-04-18
I did ascend once a long long time ago.  I have to admit it was Nethack 3.1.3 and there were a couple of save file abuses hidden in there.

I still love playing this great game though!

BTW does anybody know what to do to get the nethack mode of emacs working (nethack-el) - which would allow one of the other complaints I've seen here to be sorted:  remapping of the corsor keys.

I downloaded and installed it (nethack-el that is) but cant work out how to invoke it.  Feeling stupid again ....

---

### Post by rawr2010 on 2007-11-05
I play Nethack on a server and I just can't figure out how to make the right font happen. Im supposed to be using terminus and I've tried to install it but something is wrong. The instructions I have to go off of are as follows:

# X11:

    * Fonts
      All I ever use anymore is what my Debian GNU/Linux system calls vga which is actually -xos4-terminus-medium-r-normal--16-160-72-72-c-80-ibm-cp437 which is part of the xfonts-terminus-dos Debian (sarge, etch) package.
      The Terminus font home is here.
      Use the IBMgraphics nethack option with this font. 

This is one of the only things I can't do on my new Ubuntu system so any suggestions would be helpful. 

Hack the planet.

---

