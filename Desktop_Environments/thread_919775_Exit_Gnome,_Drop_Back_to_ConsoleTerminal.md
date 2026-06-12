---
title: "Exit Gnome, Drop Back to Console/Terminal"
date: 2008-09-14
forum: Desktop Environments
---

### Post by maw246 on 2008-09-14
I'm pretty new to Linux, but I'm eager to become proficient.  I want to run Ubuntu WITHOUT always using the GUI (Gnome).  For most tasks, I'll want to work inside Gnome, but when I logoff, I want to drop back to the terminal.  When I boot my machine, I want to see a terminal, thus only launching Gnome when I choose to.

So far, I have configured my Ubuntu installation to boot to a terminal without a GUI by commenting out "/usr/sbin/gdm" from the "/etc/X11/default-display-manager" file.  Then, when I type "sudo gdm", Gnome loads up and I have a nice desktop.  This was half the battle.  However, I cannot figure out how to drop back to that terminal when I'm finished in Gnome.

I've tried issuing the "sudo gdm stop" command from /etc/init.d directory, but that gives me X errors, tries to restart, etc.

1) Is my approach for the bootup correct?
2) How can I achieve my desired effect of landing back in the terminal when I'm finished with gnome?

Thanks.

---

### Post by benerivo on 2008-09-14
Your bootup looks fine. It is exactly what i would have tried. To get back to just a terminal, i would log out from gnome. Then (whilst on the login screen) i would Ctrl+Alt+F1, and login in from the command line. Then sudo killall gdm. You should now only have a terminal session - and no gnome. This is probably not the quickest way. I'd imagine there's a single command that could be given from within gnome that could get you back to the 'initial boot up / login screen'.

---

### Post by Vivaldi Gloria on 2008-09-14
> I want to see a terminal, thus only launching Gnome when I choose to.

See my posts here:

[http://ubuntuforums.org/showthread.php?t=918077](http://ubuntuforums.org/showthread.php?t=918077)

---

### Post by maw246 on 2008-09-16
Thanks to both of you for the feedback so far.  Both posts were helpful, and I actually hadn't realized there were 6 other terminal screens available by pressing Ctrl+Alt+(F1 thru F6) until I read benerivo's post and started experimenting.

However, I'm still stuck on how to cleanly exit from Gnome, short of killing every gnome related process, which seems like an ugly way to do it, and leaves my Ctrl+Alt+F7 Display all hosed up.

As I mentioned before, running "gdm stop", which every other post seems to suggest, just leaves a hanging "gdm stop" process, and/or just triggers a relaunch of GDM.

Any other thoughts?

Thanks.

---

### Post by Malac on 2008-09-16
This may work, haven't tried it.
In /etc/rc1.d is a kill for gdm (K01gdm) when you are running in root single user mode.
Try copying that to another run level e.g. /etc/rc3.d and setting that as one of the boot up options.
following this to test it. [http://ubuntuforums.org/showpost.php?p=5776882&postcount=4](http://ubuntuforums.org/showpost.php?p=5776882&postcount=4)
If it works then make the change permanent in /boot/grub/menu.lst

---

### Post by bnmohler on 2008-12-11
not sure if this helps any but..

for me i run Ubuntu server 8.10 and by default it boots CLI

i later installed the gnome environment with apt-get so on rare days i would have a way to access a web browser

i use the startx command to bring up gnome.

when done with gnome and i want to return to the CLI without having to restart my server i simply use ctrl+alt+backspace and it takes me back to console.

according to htop once back i am using the same amount of memory and tasks as i was prior to starting gnome... so it does not appear to be messy

---

### Post by CholericKoala on 2008-12-11
to go to console, I always just do a "Ctrl + Alt + F1"

---

### Post by wiggie on 2009-12-21
Hi, i have a question regarding the lack of any CLI, so before opening a new thread for a ridiculously easy problem maybe someone can tell me what I do wrong..

After the Boot procedure, before and/or after logging into X11R7.4/Gnome on my Jaunty installation, pressing Ctrl+Alt+Fx does nothing but suspend my monitor into Power Save.
Even though Alt+F7 brings me back unharmed I want, like maw246, to use the terminal without X.
Any suggestions ?

---

### Post by m0nstersnatch on 2009-12-21
> **wiggie said:**
> Hi, i have a question regarding the lack of any CLI, so before opening a new thread for a ridiculously easy problem maybe someone can tell me what I do wrong..
I have the same problem. Can somebody make an educated guess where the problem could be..

---

### Post by m0nstersnatch on 2009-12-22
I tried fiddling with Grub2 and changed /etc/grub.d/00_header as follows:
```
  set gfxmode=0x0317
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  terminal gfxterm
```
but still nothing happens - i cannot use the console mode without X..
Would it help if I`d post some more configs? Which?
Any help would be most welcome.

---

### Post by m0nstersnatch on 2009-12-31
bump!

here are my configs.. maybe this brings up some advice..

boot/grub/menu.lst
[http://nopaste.debianforum.de/34015](http://nopaste.debianforum.de/34015)

/etc/default/grub
[http://nopaste.debianforum.de/34050](http://nopaste.debianforum.de/34050)

/etc/grub.d/00_header
[http://nopaste.debianforum.de/34051](http://nopaste.debianforum.de/34051)

```
$sudo update-grub2 
Updating /boot/grub/grub.cfg ...
Found Debian background: Hortensia-1.tga
Found linux image: /boot/vmlinuz-2.6.28-17-generic
Found initrd image: /boot/initrd.img-2.6.28-17-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by m0nstersnatch on 2010-01-06
> **m0nstersnatch said:**
> bump!
After upgrade to 9.10 still no TTY/CLI. Monitor goes into powersave  a few seconds after Ctrl+Alt+Fx

---

