---
title: "Problems using Beryls 3D Cube"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by Yeeze on 2007-10-02
Hello,

I am new to Ubuntu, and I think its awesome!!!

Anyways, I installed Beryl and it runs fine, except of the cube...
When I turn on the Cube plugin, some animations stop working, mostly on normal windows, and either one of the <Shift>,<Control>,<Super> or <Alt> button automatically initiate the cube...
Means I am not able to write uppercase letters or use any shortcuts that use combinations containing one of those buttons!!

I already checked the shortcuts section of the Cube plug-in, but they are all set on combinations for example: <Control><Alt>Button1 to initiate rotation and so on...
I even tried setting another shortcut to the <Control> button, and beryl did not give me a warning that the short cut is already in use...

I think there must be a problem somewhere else, but I cannot seem to find it...

I did some changes in the xorg.conf file to get my mouse buttons working properly, but when I ran the cube with the original backup file, I created before I changed anything, the problems remained...

I am running Ubuntu Feisty 7.04, Gnome with beryl and the emerald theme manager...
The desktop wall seems to run just fine, and the window animations work perfect when the cube is disabled...


Anybody any Ideas?

Thx in advance!

---

### Post by Rupertronco on 2007-10-02
Go ahead and post your xorg.conf file just in case something might be wrong. Also what type of keyboard are you using?

Trying compiz-fusion wouldn't be a bad idea either (it's loads better than beryl)

---

### Post by Yeeze on 2007-10-02
I attached my xorg file...


To get the keyboard info, I entered in the command line 
```
$ dmesg | grep keyboard
```
and got the following:
```
[    1.106257] input: AT Translated Set 2 keyboard as /class/input/input1
```
Is that the information you whre looking for?


Ahh my beryl is:
beryl-core 0.3.0-svn

I am not shure but I think it is already the compiz-fusion...

---

### Post by Yeeze on 2007-10-03
Oh by the way, I am using an ATI Radeon 9800 graphics card...

I aslo tried reinstalling beryl...
But that did'nt help

Any body any Ideas?

---

### Post by Yeeze on 2007-10-13
up

So maybe this helps...

I am using a german keyboard, and I tried it with both the german and the us configuration, but I still get the cube when pressing <Shift>,<Control>,<Super> or <Alt>...

So if anybody could please help me, I searched everywhere, and in every language I can read, but did not find anybody having the same problem...!!

---

### Post by Yeeze on 2007-10-16
bump

Why can not anyone help me?
Did I not express my problem clearly enough?

---

### Post by Yeeze on 2007-10-21
Bump

---

### Post by drmatty on 2007-10-21
I have an ATI card and remember having problems initiating Beryl in Feisty. I'd recommend trying gutsy. There is automatic installation of ATI device drivers (third-party), and compiz-fusion works great after installing xorg. Hope this helps.

---

### Post by Yeeze on 2007-10-25
Thanks drmatty!

At the moment I am a little scared to upgrade to Gutsy, that this could break my system... 
But I think I will upgrade in the next weeks sometime, hope that the issue will be gone after upgrading =)

---

### Post by drmatty on 2007-10-25
I still haven't had any problems with Gutsy! don't forget to instal xorg after you install Gutsy to get compiz-fusion to work correctly. Good luck!:):)

---

### Post by Yeeze on 2007-10-27
Yeah, but I actually am using Beryl, you think beryl will also work as before, and could fix my problem?

---

