---
title: "Installing ePSXE"
date: 2014-12-13
forum: Emulators
---

### Post by michael-piziak on 2014-12-13
I'm running Ubuntu 12.04 (64 bit).

I generally always install from the Software Center to be safe.  But I did install Snes9x from this web page and it worked out fine:  [http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html](http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html)

I would like to try ePSXE as an alternative PlayStation 1 emulator to go to for rom games that PCSX won't run. 

My question is, are the instructions at this website safe for me to run, or will it work, to install ePSXE ?

The code for terminal, at this website, is:
[B]

[B]cd /tmp
[B]wget -O libglib1.2ldbl_amd64.deb [http://goo.gl/ZEHVg](http://goo.gl/ZEHVg)
[B]sudo dpkg -i libglib1.2ldbl_amd64.deb
[B]wget -O libgtk1.2-common_all.deb [http://goo.gl/snRd1](http://goo.gl/snRd1)
[B]sudo dpkg -i libgtk1.2-common_all.deb
[B]wget -O libgtk1.2_amd64.deb [http://goo.gl/lxFZj](http://goo.gl/lxFZj)
[B]sudo dpkg -i libgtk1.2_amd64.deb

[/B][/B][/B][/B][/B][/B][/B][/B]The current latest version of ePSXe for Linux is 1.6.0, you can install it with these commands:[B][B][B][B][B][B][B][B]

[B]wget -O epsxe160lin.zip [http://goo.gl/RmKiF](http://goo.gl/RmKiF)
[B]sudo apt-get install unzip
[B]mkdir -p ~/ePSXe && unzip -q epsxe160lin.zip -d ~/ePSXe

[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]The ePSXe folder is located in your home. To start the emulator from the terminal, you can use this command:[B][B][B][B][B][B][B][B][B][B][B]

[B]~/ePSXe/epsxe


[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]p.s. Once installed, does one have to start it from terminal, or will it show up in the Dash and I can simply click it like I do other programs.

---

### Post by schragge on 2014-12-13
Well, have you tried the library links? They are all dead. Those are old libraries from hardy (8.04 LTS) probably repackaged for precise (12.04 LTS). Since they are not available anymore, you'll probably have to download source packages from [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) and compile them from source yourself.

Besides, the instruction is wrong in stating that the current latest version of ePSXe for Linux is 1.6.0. It's 1.9.0 according to the official website: [http://www.epsxe.com](http://www.epsxe.com)

So maybe you don't need the old libraries after all if 1.9.0 can work with newer versions.

Well, I've just downloaded 1.9.0 from the official site. It's statically linked 32-bit binary. So you definitely not need the libraries.

---

### Post by michael-piziak on 2014-12-14
> **schragge said:**
> Well, have you tried the library links? They are all dead. Those are old libraries from hardy (8.04 LTS) probably repackaged for precise (12.04 LTS). Since they are not available anymore, you'll probably have to download source packages from [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) and compile them from source yourself.

Besides, the instruction is wrong in stating that the current latest version of ePSXe for Linux is 1.6.0. It's 1.9.0 according to the official website: [http://www.epsxe.com](http://www.epsxe.com)

So maybe you don't need the old libraries after all if 1.9.0 can work with newer versions.

Well, I've just downloaded 1.9.0 from the official site. It's statically linked 32-bit binary. So you definitely not need the libraries.

Thanks for your reply.

I downloaded the linux version of epsxe and extracted it.  However, I can not get past that point.  If I double click epsxe, nothing happens.
If there is terminal code or something to get it installed or going, please do tell.

---

### Post by adec2 on 2014-12-16
goto the directory with epsxe in it and open a terminal there then type ./epsxe and the errors will be shown in the terminal on why it wont start

---

