---
title: "Blackbox with bbkeys"
date: 2006-09-23
forum: Desktop Environments
---

### Post by SirOracle on 2006-09-23
Hi
I have a fresh install of Ubuntu Dapper, and Ive installed Blackbox, (I followed this guide: [http://ubuntuforums.org/showthread.php?t=125084)](http://ubuntuforums.org/showthread.php?t=125084)).
But after some googling I found out that I have to install bbkeys to get to use keyboard-commands like ALT+TAB, ALT+F4 and so on. I installed bbkeys with the command "sudo apt-get install bbkeys", and it looked fine.

But when I try to start it, with the command bbkeys I get this:

atle@tubbe:~$ sudo bbkeys
Password:
bbkeys: KeyClient: ERROR: Couldn't load rc-file: [/home/atle/.bbkeysrc], falling back to default: [/etc/bbkeys/bbkeysrc]
bbkeys: keytree::addAction: keyCode for key: [F20] not found. can't add it. skipping.

bbkeys: ScreenHandler: in findSupportingWM.
bbkeys: ScreenHandler: first readSupportingWMCheck succeeded.
bbkeys: ScreenHandler: second readSupportingWMCheck worked.
bbkeys: ScreenHandler: Found compatible window manager: [Blackbox] for screen: [0].
bbkeys: ScreenHandler: Supported atoms: [45].
*** glibc detected *** free(): invalid pointer: 0x0808b388 ***
Aborted
atle@tubbe:~$ 

Some more information:
Ubuntu is running on VMware Workstation 5.5 and the host OS is Windows XP Professional. And it is all running on a Dell Latitude D610.

Does anyone know how to fix this, it is tiresome not to be able to use the keyboard-shortcuts.

---

### Post by SirOracle on 2006-09-26
Not many who use bbkeys here :(
Does anyone know any other keyboard-handlers (or what it is called) who work good then?

---

