---
title: "Disable GDM and Boot Gui"
date: 2007-01-30
forum: Desktop Environments
---

### Post by duaux on 2007-01-30
I have a few questions related to graphics and the boot up process of xubuntu which I am assuming is same as ubuntu.

1. I would like see the boot up process, ie. disable the boot gui.
2. I would like to then boot straight into the console.

I believe this is involves editing /etc/inittab and changing the runlevel to 3 with other linux distributions? However xubuntu does not have an /etc/inittab file...

Do I have to disable GDM for this to happen?

Please advise.

Thank you.

---

### Post by Rui Pais on 2007-01-30
hi,
you need to edit your kernel line (or replicate your kernel entry) on /boot/grub/menu.lst.

Remove 'quiet' option from kernel line to see a boot processes in usplash screen

Deeper: remove 'quiet' and 'splash' from kernel line and the 'quiet' line to see all messages on pure console.

To avoid gdm from load try to install something like sysv-rc-conf (console) or bum (gui) and remove the gdm load from start level.

---

### Post by duaux on 2007-01-30
Hi Rui,

Thank you so much.

That was exactly what I was looking!
:guitar:

---

### Post by Rui Pais on 2007-01-30
you're welcome :)

---

### Post by tlsarles on 2007-02-15
Just what i needed as well!

---

### Post by golfing22 on 2007-03-01
Hi,
I'm running a server and normally gdm doesn't need to be running 95% of the time, so it's great that is now doesn't start on bootup.  I can type "/etc/init.d/gdm start" and it's work perfect.  Now my only problem is that I don't know how to shut gdm/gnome/x (not sure what the gui is technically called) down once I'm done using it.  I tried "/etc/init.d/gdm stop" but that just shuts off gdm and gives me a blank black screen.

Thanks for the help,

-golfing22

---

### Post by josiah on 2007-03-05
It's been awhile since I've used a Debian-based system, but I believe there's a file /etc/X11/default-desktop-manager or something of that sort... I seem to recall that removing the references to gdm/kdm gave me the desired result of not having gdm or kdm load.

[editing for greater specificity]

Upon looking through the Debian Reference, it looks like it is /etc/X11/default-display-manager, though it may be different now (the document looks old... and I don't know how different Ubuntu is from Debian here). 

The DR also has more info on disabling gdm, but again, I don't know how relevant it is for you:
[http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-no-x-start](http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-no-x-start)

---

### Post by Rizado on 2007-03-19
> **golfing22 said:**
> Hi,
I'm running a server and normally gdm doesn't need to be running 95% of the time, so it's great that is now doesn't start on bootup.  I can type "/etc/init.d/gdm start" and it's work perfect.  Now my only problem is that I don't know how to shut gdm/gnome/x (not sure what the gui is technically called) down once I'm done using it.  I tried "/etc/init.d/gdm stop" but that just shuts off gdm and gives me a blank black screen.

Thanks for the help,

-golfing22You really don't have to start gdm at all. Just type "startx" and x will start for the user you logged in on. When you log out you'll be back at the console.

---

### Post by tmetzcc325 on 2007-09-06
Hello all,

I am running Ubuntu Feisty with GDM.  I remember that when I used to boot Breezy, there was a graphical boot screen showing which processes were starting that all that.  Now when I boot Feisty, there is just a blank screen with nothing at all on it, not even a blinking cursor, until the user login screen appears.  I assume this has something to do with the 'quiet' and 'splash' options in the menu.lst file, but I am not exactly sure what all these different options mean.  Can anyone give me a quick rundown of what these are, and how I might be able to see some sort of graphical boot screen?

Thanks a bunch,
Tom

---

### Post by merlinus on 2007-09-06
quiet means you do not see the text scrolling by as ubuntu checks for various components and initializes this and that.

Remove it from the kernel line in /boot/grub/menu.lst.

-merlin

---

### Post by tmetzcc325 on 2007-09-06
Thanks Merlin.  This gave me the text display.  Has the graphical display that I remember seeing in Breezy been done away with?  It is a lot easier on the eyes.  Basically I don't need to see EVERYTHING that is happening during boot, but I'd like a bit more feedback than the blank screen.  Does this make sense?

Thanks,
Tom

---

### Post by merlinus on 2007-09-06
Don't know about breezy -- before my ubuntuing.

Watching the text scroll by can be interesting.  You can always restore "quiet" if you get tired of it.

I rarely restart my machine, and when I do, I usually walk away for a bit.

-merlin

---

### Post by Rui Pais on 2007-09-07
> **tmetzcc325 said:**
> Thanks Merlin.  This gave me the text display.  Has the graphical display that I remember seeing in Breezy been done away with?  It is a lot easier on the eyes.  Basically I don't need to see EVERYTHING that is happening during boot, but I'd like a bit more feedback than the blank screen.  Does this make sense?

Thanks,
Tom

Hi, 
for get the usplash look of breezy, basic process information on graphical display, just remove the word 'quiet' from kernel line and leave the line that contains the option 'quiet' only. And keep the option 'splash' too.

hth

---

### Post by tmetzcc325 on 2007-09-08
I tried that, but now I just get the blank screen with nothing on it.  Here is my default entry in menu.lst.  What needs to change?

[FONT="Courier New"]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=909acbb1-c5d1-431e-ada8-f20ac1b5856c ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault[/FONT]

If it can't be changed, that is okay, I am just curious about this.

Thanks,
Tom

---

### Post by Rui Pais on 2007-09-08
> **tmetzcc325 said:**
> I tried that, but now I just get the blank screen with nothing on it.  Here is my default entry in menu.lst.  What needs to change?

[FONT="Courier New"]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=909acbb1-c5d1-431e-ada8-f20ac1b5856c ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault[/FONT]

If it can't be changed, that is okay, I am just curious about this.

Thanks,
Tom

then you may need to add a vga=791 to root line, and see if that make it visible:
```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=909acbb1-c5d1-431e-ada8-f20ac1b5856c ro splash vga=791
```

hth

---

