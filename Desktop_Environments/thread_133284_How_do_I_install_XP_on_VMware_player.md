---
title: "How do I install XP on VMware player"
date: 2006-02-19
forum: Desktop Environments
---

### Post by shade11 on 2006-02-19
I have been expirementing with VMware player and I wanted to see if I could install Windows XP home on it. I am not going to keep it but just see what it could do. And see how good it is. I have seen some guides and they seem too confusing. I know that it is possible I just don't know how. . . Can someone please tell me?

---

### Post by Protex on 2006-02-19
[http://www.ubuntuforums.org/showthread.php?t=84275&highlight=xp+vmware](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=xp+vmware)

Easiest guide I've found.

---

### Post by shade11 on 2006-02-19
It is too confusing. I dont get a single part about the floppy's and cabextract.

---

### Post by th2 on 2006-02-19
Well, VMware's player software can only run virtual machines that **already exist**.  You're best bet is as follows:

1.) Download VMware Workstation (get a trial key.... but if memory serves, you won't be needing it... just get one in case).

2.) Install the tar version (or RPM via Alien...).

3.) Configure it!

4.) Run VMware.

5.) Create a virtual machine meant for XP Home.... make the virtual hard disk as big as you want......

Note: Do a search on *.ISO on your hard drive, then find the ISO files for VMware tools... copy and paste every one (windows, linux, etc...) into your home directory.

6.) Don't do anything with that virtual machine yet... in other words, don't launch it.

7.) Uninstall VMware (see instruction manual for uninstalling VMware).

8.) Download VMware **Player** and install it.

9.) After configuring VMware Player, then grab that XP CD.

10.) Through the player, open the Windows XP virtual machine file....

11.) Then when the virtual machine launches, click virtual screen so the mouse is captured; then hit F2 to enter the virtual BIOS, and change the boot order to CD.

12.) Pop in your XP CD.

13.) When the virtual machine reboots, and......... you should be able to install XP Home from there....

Hope that helps...

---

### Post by Michael Steinberg on 2006-02-19
You probably would find the directions at

[https://wiki.ubuntu.com/VMwarePlayerAndQemu?highlight=%28vmware%29](https://wiki.ubuntu.com/VMwarePlayerAndQemu?highlight=%28vmware%29)

easier. Use the directions for the alternative path & install directly from the Windows CD.

---

