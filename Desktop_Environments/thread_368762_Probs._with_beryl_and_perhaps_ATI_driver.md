---
title: "Probs. with beryl and perhaps ATI driver"
date: 2007-02-23
forum: Desktop Environments
---

### Post by casper1986 on 2007-02-23
Hi, I've just installed ubuntu 6.10 which works fine. Then I tried to install beryl, but I can't get anything to work in beryl, I wanted the cube but it just doesn't work.
In the advanced window manager i have 2 settings, either beryl or metacity. But when I click on beryl it just goes back to the metacity.!!

I guess it's because of my gfx, I have a ATI Readon 9600 se. And I downloaded some sort of driver in applications --> add/remove

Can anyone help plz?

---

### Post by casper1986 on 2007-02-23
Well now I've found a driver at the ATI homepage:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I've downloaded the file to my disk, but how do I install it?

---

### Post by cortsenc on 2007-02-23
I don't know but I think than only free-driver can get 3D acceleration.
I have the same problem, I have Radeon 9600 and I can't get a Beryl Desktop :(

I wish AMD convince ATI than open source drivers are the best choose

---

### Post by Savvy on 2007-02-23
There you go: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

:)

---

### Post by casper1986 on 2007-02-24
Thanks, well now I've tried the commands but when I get to the check part at last I get this:

casper@casper-desktop:~$ $fglrxinfo
casper@casper-desktop:~$ display: :0.0  screen: 0
bash: display:: command not found
casper@casper-desktop:~$ OpenGL vendor string: ATI Technologies Inc.
bash: OpenGL: command not found
casper@casper-desktop:~$ OpenGL renderer string: MOBILITY RADEON 9700
bash: OpenGL: command not found
casper@casper-desktop:~$ OpenGL version string: 2.0.6334 (8.34.8)
bash: syntax error near unexpected token `('
casper@casper-desktop:~$ 

How come it does this?

---

### Post by bjornolai on 2007-02-24
> **casper1986 said:**
> Thanks, well now I've tried the commands but when I get to the check part at last I get this:

casper@casper-desktop:~$ $fglrxinfo
casper@casper-desktop:~$ display: :0.0  screen: 0
bash: display:: command not found
casper@casper-desktop:~$ OpenGL vendor string: ATI Technologies Inc.
bash: OpenGL: command not found
casper@casper-desktop:~$ OpenGL renderer string: MOBILITY RADEON 9700
bash: OpenGL: command not found
casper@casper-desktop:~$ OpenGL version string: 2.0.6334 (8.34.8)
bash: syntax error near unexpected token `('
casper@casper-desktop:~$ 

How come it does this?

Remeber to be carefull here. Are you sure you couldn't get it to work with the ordinary fglrx driver? You have to download it and change some lines in xorg.conf. Be very carefull with this file.

You're following a guide now right. 
Anyhow, OpenGL ... are not commands you are supposed to input. They are the output you're supossed to get when running $ fglrx    You only write fglrx   the dollar sign just indicates that its a command you're supposed to run in console. 

Remember that beryl is alpha and not stable. However if you really want to do this i suggest trying this guide right here:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by pebo on 2007-02-24
I've recently installed beryl successfully using [this]("https://help.ubuntu.com/community/BerylOnEdgy") guide on my laptop (radeon 9700) and desktop (radeon 9200). Just followed it to the letter and no hitches. You need to use the open source driver

---

### Post by casper1986 on 2007-02-24
Well bjornolai the link you are reffering to is the instructions I've followed so far.

---

