---
title: "Beryl Crashes"
date: 2007-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Soorena on 2007-04-15
Hi all I am really new to Linux and barely managed to install beryl. So I installed the Nvidia drivers and then beryl, but when I run beryl my whole system freezes and I can't do anything. I was stupid enough to add it to the start up programs so I was wondering If I can remove it somehow before the login loads everything. 

Remember I am really new to this!! Thanks.

---

### Post by aidanr on 2007-04-15
boot into recovery mode (hit escape when grub is loading) and type:
```
rm /home/[username]/.config/autostart/beryl-manager.desktop
```
replacing [username] with your username

make sure your /etc/X11/xorg.conf is set up correctly for beryl (post the contents of that file here if you're not sure)
and reinstall the nvidia drivers

---

### Post by Soorena on 2007-04-15
Thank You for replying. As I said I am really new to all this so can you bare with me and tell me how to do all that you said? 

Thanks

---

### Post by aidanr on 2007-04-15
ok, reboot the computer, when the computer is starting up you'll see a bit of text that says *grub loading*, when you see that hit escape and you will see the grub menu, use the arrow keys to select recovery mode (or single user mode) and hit enter to boot

then sit back for a minute while it boots, when it's finished booting you will be at a command prompt (you may be asked for a password, just type in your password)

now the line you should type in is:

rm /home/[username]/.config/autostart/beryl-manager.desktop

where [username] is your username
then type *reboot* to reboot the computer

now beryl will no longer load when you log in

as for the rest of it, well it's a little more advanced so maybe you should stay away from beryl for a while until you get a bit more used to linux, or at least wait until the next version of ubuntu comes out in a few weeks which will make it a lot easier to get these desktop effects going

---

### Post by Soorena on 2007-04-16
Well since I have Windows Vista also running there is a Boot Loader and there is an option for recovery mode when I said I need you to explain it I meant the second part, I'm not that noob, lol. Anyways I tried it and it didn't work it said that the command is not known. Also it didn't ask for a username or password, although I have one.

---

