---
title: "can't start X with fvwm"
date: 2006-12-31
forum: Desktop Environments
---

### Post by drx4 on 2006-12-31
I have just installed my first Ubuntu (Edgy), having run Red Hat since 1997.
I installed fvwm (2.5.16) and a simple ~/.Xclients:

  #!/bin/sh

  xterm -sb -sl 500 -j -ls -fn 7x14 -geometry 224x76+0+94 &
  exec fvwm2

I have my usual ~/.fvwm2rc in place.

When I call startx, the crude gray screen with the big "X" cursor flashes on
briefly, and then it fails with the following errors:

  Error opening /dev/wacom : Success
  (EE) xf86OpenSerial: Cannot open device /dev/wacom
          No such file or directory.
  Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
  Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
  Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
  waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
  refcount is 2, should be 1; fixing.

I have tried the following:

1. Commenting out all the wacom entries from /etc/X11/xorg.conf.  This gave a
   "no screen found" error.
2. Copying the TTF, OTF, and CID directories from Red Hat to Ubuntu's
   /usr/share/fonts/X11.  Then I got just the CID error.  That directory was
   empty even under Red Hat.
3. Installing fvwm by compiling the source.  I got the same errors.
   
I do have xfs, xfonts-base, linux-restricted-modules-386, and libfreetype6
installed.

I'd appreciate any suggestions on how to bring up an X-window with fvwm.
Thanks.

---

### Post by ThomasAdam on 2006-12-31
I'm not surprised.  You're ignoring almost everything that's being said of you.  I would imagine your wacom tablet is your corepointer device, no?  If you comment it out, you should be replacing it, ideally with a refence to your mouse device.  Unless you tell X11 to load on mouse error, of course.

Further down, you'll notice that there was an error indicating a ref count to your fonts.  This is typically related to all manner of things.  Running:

fc-cache -f

Might help, as might poking around at the order of your font paths listed in /etc/X11/xorg.conf -- indeed, does using 'xinit' alleviate this issue?

-- Thomas Adam

---

### Post by drx4 on 2007-01-01
Thanks for trying to help with this, Thomas.

The /dev/wacom errors are confusing because I don't have a graphics tablet at
all.  Still, xorg.conf lists three wacom InputDevices (stylus, eraser, and
cursor).  However, the Configured Mouse device is the only one identified as
CorePointer.  So I don't know why anyone is looking for /dev/wacom.  There is
no such device or device file.

I ran fc-cache -f which exited with status 0 and no output or errors, but
this didn't fix anything.

Calling xinit does in fact bring up a really simple X-window but still
generates the same errors as startx.  I am able from the simple X-window to
call other windows (e.g. mozilla).

As for xorg.conf, the first FontPath is "/usr/share/X11/fonts/misc", which
does not exist.  If I eliminate this, there is just one change to the errors.
The FPE message becomes:

  waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"

This is the last FontPath in xorg.conf.  This directory does exist, and it
contains >400 gzipped font files.

Another odd thing happened when I ran

  apt-get install --reinstall xfonts-base

This complains that /usr/lib/X11/fonts/misc does not exist.  However, if I
create that directory, it gets deleted during the reinstall, and I get the
missing-directory error again.

I should mention that I do all of this after booting to runlevel 3, which
brings up a console and never calls gdm.

---

### Post by ThomasAdam on 2007-01-13
> **drx4 said:**
> Thanks for trying to help with this, Thomas.

The /dev/wacom errors are confusing because I don't have a graphics tablet at
all.  Still, xorg.conf lists three wacom InputDevices (stylus, eraser, and
cursor).  However, the Configured Mouse device is the only one identified as
CorePointer.  So I don't know why anyone is looking for /dev/wacom.  There is
no such device or device file.

Then comment out all references in xorg.conf to wacom, ensuring that in so doing you set your mouse up as a CorePointer device.

---

### Post by drx4 on 2007-01-16
Thanks again, Thomas.  I did already try that, and it didn't fix the problem.

Because I had several problems with Ubuntu, I am trying Debian now.  Mostly the problems with Ubuntu and Debian are similar, which I guess is not surprising.  I'll get back to the fvwm issue in the future.

---

### Post by K.Mandla on 2007-01-17
Make sure you have *exec fvwm* (it is fvwm, or is it fvwm2? I'm not 100 percent sure on that) in your ~/.xinitrc file. Starting X without telling it which window manager to execute usually gives me the same gray-screen-flash.

The Wacom thing is ... well, I don't know. I also get configuration messages for Wacom stuff in my xorg.conf files, but I don't know why. If they're commented out, they shouldn't affect the system at all -- and are therefore safe to ignore.

Let us know if that helps at all.

---

### Post by ThomasAdam on 2007-01-20
> **K.Mandla said:**
> Make sure you have *exec fvwm* (it is fvwm, or is it fvwm2? I'm not 100 percent sure on that) in your ~/.xinitrc file. Starting X without telling it which window manager to execute usually gives me the same gray-screen-flash.

And of course, with no ~/.xinitrc means nothing anyway -- you won't get kicked out of X11 for it.  And to answer your question, it's "fvwm" with FVWM 2.5.X -- the naming convention for the fvwm2 binary was stopped long ago.

It also doesn't matter whether you have "exec" or not -- it just means the spawning shell isn't kicked out of the way when the fvwm process is started.

-- Thomas Adam

---

### Post by drx4 on 2007-01-22
Thanks.  I've been trying fvwm with the Debian testing release (sarge) and do now have fvwm working well now.  After hours of tracking down and testing leads that didn't help, I found a problem: startx ignores ~/.Xclients (which had worked under Red Hat).  When I moved that to ~/.xinitrc, everything worked fine.  The file does have "exec fvwm", and the installation has a symbolic link fvwm2.

It is still the case that, unpredictably, calling startx makes the screen flash.  Mostly it works the way it should, and I haven't figured out what it takes to crash it.  Unfortunately, I have to boot out from such a crash.  Why?  Because I can't interrupt out of it and because virtual terminals don't work on my installation.  I've filed bug reports about the virtual terminals at Ubuntu (bug 77765) and Debian (bug 407228).

Thanks again.  It's great to have fvwm back.

---

### Post by drx4 on 2007-01-22
> I've been trying fvwm with the Debian testing release (sarge) ...

Woops.  Make that "etch".

---

### Post by mahfiaz on 2007-01-23
For me, after running xinit, gnome-session $  brought everything up, while having same problem on gentoo.

---

