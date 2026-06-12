---
title: "Compose key not working"
date: 2008-06-24
forum: Desktop Environments
---

### Post by stinkinrich88 on 2008-06-24
Hello,

I followed the instructions from this page: 

[https://help.ubuntu.com/community/ComposeKey]("https://help.ubuntu.com/community/ComposeKey")

I have set up my compose key to be shift+altgr (default - no boxes ticked) then I follow the instructions to use my compose key: I hold shift+altgr, release them both then type **o** then **/** (should give me ø) but all I get is **o/**. What am I doing wrong? p.s. I especially want an em-dash. 

Thanks!

p.s. I'm using a UK layout

---

### Post by stinkinrich88 on 2008-06-24
a bug then, I take it. Am I definitely using the key right (before I report it)? Hold shift+altgr then release then type o/.

---

### Post by stinkinrich88 on 2008-06-25
meh, bug reported: [https://bugs.launchpad.net/ubuntu/+bug/242885]("https://bugs.launchpad.net/ubuntu/+bug/242885")

---

### Post by billynomates on 2008-07-11
Try not releasing them before you press **o/**. 
Em-dash is [compose key][minus][minus][minus]

---

### Post by stinkinrich88 on 2008-07-12
yeah, I've tried that too. I've tried loads of different stuff, this must be a bug. I filed one here a while back: [https://bugs.launchpad.net/ubuntu/+bug/242885](https://bugs.launchpad.net/ubuntu/+bug/242885)

---

### Post by der_joachim on 2008-07-12
AFAIK your compose key cannot be Shift + some key. Otherwise, there would be no way to capitalize your accented characters. 

How does the keyboard section of your /etc/X11/xorg.conf look?

---

### Post by stinkinrich88 on 2008-07-12
I've set my menu key to compose now. Here is my xorg keyboard section:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

peculiarly it says my layout it "us"! But it's blatantly UK

---

### Post by 0x656b694d on 2008-10-02
Hi,

I had Compose key working until installed scim (accidentally) and than removed it.

All settings are kept the same as before. How do i get my Compose key back??

Thanks!

-Mike

---

### Post by fishexe on 2008-10-08
I've had a similar problem, and here's how I solved it:

I commented out the following in my ~/.gnomerc
#    XMODIFIERS="@im=SCIM"
#    export XMODIFIERS
#    GTK_IM_MODULE="xim"
#    export GTK_IM_MODULE

and replaced it with the following:
    GTK_IM_MODULE="scim"
    export GTK_IM_MODULE

and everything worked (of course I still have scim installed).  This also solved other SCIM problems, like the one where it types in the wrong window.  However, these lines could be in one of several files depending on how you originally set up SCIM, so if it's not in .gnomerc check .xsession, and then maybe use find if it's not there.

---

### Post by Jæd on 2008-10-15
I tried to set my compose key to right-alt, but it didn't actually do anything. So I set the compose key to right-ctrl. Now it works (I think there's a problem with my keyboard layout, so will need to fix that)

HTH

---

### Post by rabbit251 on 2008-11-10
I had the same problem as 0x656b694d. Is SCIM necessary for the compose key to work?

---

### Post by stinkinrich88 on 2008-11-10
rabbit, I'm pretty sure SCIM isn't needed. A fresh install of Intrepid resolved this issue for me. Well, I can do em-dashes but not the o/ thing... Anyway, I'm not sure but it doesn't look like intrepid uses SCIM.

---

### Post by 0x656b694d on 2008-11-10
Hi,

I reset the symbolic link (it pointed to scim-bridge):

/etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default-xim

now the Compose key works great.
Except qt4 applications (dynamically linked to qt 4.4.3) &#8212; a bug in Qt.

---

### Post by rabbit251 on 2008-11-11
Mike, can you be a bit more specific? Where do I find the symbolic link you're talking about? I'm on Hardy.

---

### Post by rabbit251 on 2008-11-11
Related thread: [http://ubuntuforums.org/showthread.php?t=937285](http://ubuntuforums.org/showthread.php?t=937285)

---

### Post by a_pirard on 2011-06-15
Just in case it would help someone...
After uninstalling SCIM because of many problems, the dead keys and compose key stopped working here too, even in new sessions.
I rebooted and the keys returned to normal. :)

---

