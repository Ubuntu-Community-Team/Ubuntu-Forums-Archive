---
title: "Enemy Territory"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by Lure_Angler on 2006-07-21
Dear all,

I have a problem with installing Enemy Territory on my Ubuntu Dapper. 

I have downloaded it from the ID website the file et-linux-2.60.x86.run

I have made sure that my computer has driver support for my Nvidia 6200 128MB graphics card, using Easy Ubuntu. My system has 512 RAM, P4 2.53 GHz.

I was able to launch the .run from the terminal, using command sh filename, 

When the install is initiating, when it asked my for my password to install the game to root, I entered the usual password which works for ALL my admin tasks. However, it doesn't work. I enter, the window disappers for a while and then pops right back. 

If I press cancel and continue installing as the current user, the game doesn't work when I click on the 'et' file. What is does is to bring a dark screen for a couple of seconds and then revert back to Ubuntu. 

And I get this warining when I hit cancel to continue to instal:

       
       Gdk-WARNING **: locale not supported by Xlib, locale set to C


Can anyone help me out here. Any help is appreciated.

Thank you and God Bless.

Lure_Angler

---

### Post by abowman on 2006-07-21
Does glxgears work for you?
```

glxgears -printfps

```

---

### Post by abowman on 2006-07-21
I just did a search on google for that error message.  Try this and then run the installer again:
```

sudo apt-get install language-support-en

```

---

### Post by Lure_Angler on 2006-07-21
Dear all,

Thank you Abowman for your help. I was thinking, for future newbie's sake, I record down every single detail of my ordeal.

To Abowman:

Yes, the command you gave me works. I see 3 gears of different size and colours running.

I tried to get English language support and I got this in the terminal:

tc@Impeesa:~$ sudo apt-get install language-support-en
Password:
Reading package lists... Done
Building dependency tree... Done
language-support-en is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This is what the window asking for my pasword says:

The recommended install location (usr/local/games) requires root permission. Please enter the root password or press cancel to continue install as current user.

If I continue, press cancel and install, just after install and before I press the start button, I got this:

Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
Link points to "/tmp/ksocket-tc"
Link points to "/tmp/kde-tc"
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
Reusing existing ksycoca
Installing symlink /home/tc/etded -> /home/tc/enemy-territory//etded
Removing existing et symlink
Installing symlink /home/tc/et -> /home/tc/enemy-territory//et

When I click on the et file, everything worked. 

Thank you all and God Bless

---

