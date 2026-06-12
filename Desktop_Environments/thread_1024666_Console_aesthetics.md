---
title: "Console aesthetics"
date: 2008-12-29
forum: Desktop Environments
---

### Post by thefish123 on 2008-12-29
Hi everyone.  I am a former (and possibly future ;)) openSUSE user.  For years I really liked SUSE but recently I have installed Ubuntu 8.10 and I am really impressed with it.

However it looks like they haven’t put much thought into the console.  I mean the good old text-based TTY’s (pressing Ctrl+Alt+F1).  Under Suse 10.3 there was a really nice “watermark” on the tty1 console and all the other virtual consoles had “normal” resolution.

Under Ubuntu I cannot figure out how to:

a) get tty1 to clear before presenting the login prompt
b) get tty1 to have a nice “Ubuntu branded” watermark
c) get the resolution/font to look “normal” on all the tty’s
d) get a graphical "Ubuntu branded" GRUB

Any assistance in these areas would be great!  I am pretty sure if I can resolve this and get back to reading my Gmail via alpine/pine on TTY1 I will be happy :-)

Thanks,
The Fish

---

### Post by albinootje on 2008-12-29
> **thefish123 said:**
>  d) get a graphical "Ubuntu branded" GRUB


Perhaps Startup-Manager can help you with this.
[http://web.telia.com/~u88005282/sum/screenshots.html](http://web.telia.com/~u88005282/sum/screenshots.html)

See also : [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Install : apt://startupmanager

And what about a fancy looking terminal in X (that's easier to accomplish I think) or are you a console only user ?

---

### Post by x1a4 on 2008-12-29
Hi,
You need to remove **usplash** and install [Splashy]("http://splashy.alioth.debian.org/") (formally [BootSplash]("http://www.bootsplash.org/"))

---

### Post by albinootje on 2008-12-29
> **x1a4 said:**
> Hi,
You need to remove **usplash** and install [Splashy]("http://splashy.alioth.debian.org/") (formally [BootSplash]("http://www.bootsplash.org/"))

Thanks.
It's available in Ubuntu Universe :
[http://packages.ubuntu.com/search?keywords=splashy](http://packages.ubuntu.com/search?keywords=splashy)

---

### Post by x1a4 on 2008-12-29
Don't use the version in the Ubuntu repos.  It's outdated and buggy.  Use the Debian version which is newer and more stable.

---

### Post by thefish123 on 2008-12-30
> **x1a4 said:**
> Don't use the version in the Ubuntu repos.  It's outdated and buggy.  Use the Debian version which is newer and more stable.Sorry in advance if this is a dumb question but where do I find the Debian version?

---

### Post by x1a4 on 2008-12-30
Click Splashy in post #3 and click Install.  It will ask you to add 
[indent]deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main[/indent]
to your repos.

Install **splashy** (with it's deps.(will update some libraries--good)) only. 

After install, comment the Debian repos; reupdate package lists; install **splashy-themes** from the *buntu repos;


EDIT: Installing Splashy from source can also be fun.
To compile Splashy yourself you'll need the following additional applications:
    *
      autoconf 2.59 (or newer)
    *
      automake 1.9 (or newer)
    *
      libproc development files
    *
      libsysfs development files
    *
      libtool 1.5 (or newer)
    *
      make
    *
      pkg-config 0.14.0 (or newer)
    *
      directfb 0.9.22 &#8656; N &#8656; 1.0.x (directfb 1.2 and up won't work)
    *
      glib2
    *
      libmagic or file-devel
    *
      libjpeg and/or libpng (optional)

EDIT: When installing Splashy make sure you have /boot mounted.  Umount it when done.

---

### Post by sdibias on 2008-12-30
I have been trying to figure out why Ubuntu does this? For months I have been using SUSE 11 and more recently 11.1 and I love the beauty of dropping into terminal, but in Ubuntu even the fonts are all big and goofy. I hope they change this in 9.04 however I wont hold my breath. On a brighter note I do love Ubuntu and anything Debian related :)

---

### Post by x1a4 on 2009-01-01
> **sdibias said:**
> I have been trying to figure out why Ubuntu does this?
To reduce the weight of the OS.  Use either **kbd** or directfb--your choice.  try between **console-tools** and **kbd**.  Checkout the available fonts,  make a decision.  Keep the one you like.

EDIT: Use different fonts for different consoles.  Set a similar yet different background image  for the various consoles.  Configure however you like.

---

### Post by superfunkymonkey on 2009-01-05
This forum is very helpful, but I still don't see how to get the console (e.g. tty1) to have a background / watermark. Can anyone explain?

What's turning up on google leads me to believe one would have to patch the kernel, but I don't understand why this would be if you can already see a frame buffer splash screen, why can't you have a frame buffer background behind the console without tweaking the kernel?

---

