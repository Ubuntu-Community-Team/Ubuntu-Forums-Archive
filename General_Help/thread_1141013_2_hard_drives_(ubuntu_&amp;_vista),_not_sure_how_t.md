---
title: "2 hard drives (ubuntu &amp; vista), not sure how to choose which one to boot up"
date: 2009-04-28
forum: General Help
---

### Post by duhglas on 2009-04-28
hey just got ubuntu installed and workign on a 2nd hard drive. To install it I just unplugged original hard drive and installed it from there, and if i want to use vista I just unplug the ubuntu hard drive. I havn't figured out how to choose which one i want to start up. Im looking for the boot loader but not sure where it is, as it doesn't give me option of which os i want to run. and when should the boot loader give me the option, b4 either system starts up or after they go to the log in screen for either os. Thx for the help.

---

### Post by duhglas on 2009-04-28
any recommendations? i'm sure it's probably fairly simple, just havn't figured it out yet.

---

### Post by ndefontenay on 2009-04-28
Hi.

usually when you install ubuntu it should install the boot loader as well.

The problem here is that you install ubuntu while vista was unplugged. So ubuntu was thinking he was alone on this PC and didn't go through the trouble to creating a boot loader.

I think you can change that in some config file by adding a new entry for vista.

That would be this file:

```
gksudo gedit /boot/grub/menu.lst
```


before doing that, try to look for applications in the repository that would allow you to modify this file in a User Interface without having to edit it yourself.

There's this for exemple but you would have to compile and all:
[http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391]("http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391")

---

### Post by etnlIcarus on 2009-04-28
Your BIOS ought to give you a couple of ways to choose which HDD to boot from. At the first screen when booting your computer, try pressing F11. Failing that (I'm not sure if that's only for AWARD BIOS), go in and change the boot-order by pressing Delete at the first boot screen.


Your mistake was taking the Windows HDD out before installing Ubuntu. If you left the Windows HDD in as slave while installing Ubuntu to your blank primary, GRUB would have automatically had this entry (or something similar) added to the end of your /boot/grub/menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by duhglas on 2009-04-28
ok im in ubuntu. Trying to figure out how I can work on the grub boot loader, to get it to read the vista hdd. Well be doing some browsing and research looking for some ideas, if anyone knows how to do it let me know, if i havn't figured it out by then.

---

### Post by duhglas on 2009-04-28
Installed the KGRUBEditor. I attempted to get that working, which i thought i did, but when I restarted my pc, it went to the grub boot loader I attempted to boot my vista hdd but it did not do anything, so i just loaded up ubuntu instead which worked fine. I had to mount the vista hard drive in ubuntu, before the kgrubeditor would know it's there. Not sure if i entered in the information correctly or not, and not sure if i needed to enter in a 'kernel' and 'argument' for vista, not sure if it has any. As well niot sure if i need to enter in an 'initrd' for vista. Well I have to get to sleep, ill be bak on in about 8 hours or so checking for any suggestions. Thx.

---

### Post by duhglas on 2009-04-29
does anyone have any ideas with this, can u help me in some way because, at this point im not sure at all what i should do.

---

### Post by etnlIcarus on 2009-04-29
> **duhglas said:**
> does anyone have any ideas with this, can u help me in some way because, at this point im not sure at all what i should do.

Absolute easiest thing to do, with a minimum of effort, fuss and guesswork:

- Win HDD as slave.
- Ubuntu HDD as primary.
- Reinstall Ubuntu, wiping the old Ubuntu installation (choose, "Use entire disk"), with HDDs in this configuration. 

When GRUB is being setup, it will automatically scan and detect Vista on the other HDD and add the correct entries to GRUB's menu.lst file.

---

### Post by caljohnsmith on 2009-04-29
> **etnlIcarus said:**
> Absolute easiest thing to do, with a minimum of effort, fuss and guesswork:

- Win HDD as slave.
- Ubuntu HDD as primary.
- Reinstall Ubuntu, wiping the old Ubuntu installation (choose, "Use entire disk"), with HDDs in this configuration. 

When GRUB is being setup, it will automatically scan and detect Vista on the other HDD and add the correct entries to GRUB's menu.lst file.
I disagree, I don't think there is any need at this point to reinstall Ubuntu nor switch the drives around so that Ubuntu becomes the primary drive just to get dual-booting between Ubuntu/Vista working. Duhglas, if you have both your HDDs turned on at start up, can you go into your BIOS settings and set the Ubuntu HDD to boot first (it should be the "boot order" setting)? If you can do that, you could then simply add an entry in your Grub's menu.lst to make booting the Vista drive on start up an option, and you'll have your dual-boot. Or if your BIOS will only allow you to boot the Vista drive on start up when both drives are connected and turned on, we can work with that scenario too. Let me know and we can work from there if you want.

---

### Post by mixmaster on 2009-04-29
The ubuntu installer can cope with installing a bootable linux and making a dual boot system whether windows is on the first or second hdd or shares a disk.

TBH, given how easy it is to install ubuntu and that you haven't been using it for long enough to have heavily customized it, I would replug both HDDs in the order in which they were originally installed then reinstall ubuntu.  When it asks where to put it make sure you tell it to overwrite the existing ubuntu installation

---

### Post by duhglas on 2009-04-29
I could reinstall it, havn't done muhc on there so it's still pretty fresh and wouldn't matter much. As for changing the grub menu.1st, i really dont have much of a clue how do do that. If u read in my previous post i tried with the kgrubeditor, but didn't have much luck, wasn't sure if i was doing it right. If its a fairly simple procedure altering grub menu.1st let me know, and u could help me through it. Other wise it looks like I will just have to reinstall ubuntu. 

I have changed the settings in the bios, when i need to get either os running. I have to change it everytime i want to run the other os. I have tried adding vista to grub boot loader using kgrubeditor, unfortunately that didn't work though.

---

### Post by caljohnsmith on 2009-04-29
In your original post you mentioned that you had to unplug the Ubuntu HDD if you wanted to boot the Vista HDD. But when you have both HDDs plugged in and turned on at start up, which HDD boots? And do you know how to change the boot order in your BIOS? I think that's the key issue right now to determining what might be the best way to dual boot your Ubuntu and Vista. Also, it would be helpful to get more info about your system related to booting before I can give you any specific advice on modifying your menu.lst, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
Make sure you run the script when the Vista drive is connected and turned on. That script will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by duhglas on 2009-04-30
Yeah when I said that I had to manually plug and unplug hdd`s, in an earlier post, I wasn`t familiar with the bios at all, and how to change which hdd I want to start up. That was the only way I knew how, now I know how to change it through the bios which I have been doing. I believe the easiest way to fix this problem is just going to be to reinstall ubuntu over top of this version I have installed right now, so it will automatically read vista now. That seems to be the simplest option at this point. 

So Im hoping it will be simple reinstalling it over the previous version. I should be able to do that alright, and Ill let you guys know how that goes.

---

### Post by duhglas on 2009-04-30
thx for all the help everyone who contributed something. i ended up just reinstalling ubuntu and have everything up and running smoothly now. The boot loader works well. Im going to keep tweaking and working on the system, im sure ill ask for more help, but thx again for the help with this problem.

---

