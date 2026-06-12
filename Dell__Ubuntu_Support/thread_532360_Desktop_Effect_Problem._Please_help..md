---
title: "Desktop Effect Problem. Please help."
date: 2007-08-22
forum: Dell  Ubuntu Support
---

### Post by kenwales on 2007-08-22
I just received a band new Dell 1420n Ubuntu laptop. I opened it, answered a few questions and longed right in. Audio worked, video worked, everything looked good. I started poking around through some of the menus and thought I'd enable desktop effects. As soon as I clicked OK I could no longer click anything. Not the menus, shutdown, nothing. Withing 3 minutes of having my new laptop I had screwed it up. 

I hard powered it off and tried different sessions but still I could not click anything. After searching through the Ubuntu forum I learned how to boot up to a command prompt and create a new user and password. Once I logged in as that new user everything seemed to be fine, except this time no audio and for some reason the menus look limited.

How can I turn the desktop effects off under my original user name and get back to the factory settings?

Please help a newbie out.

---

### Post by kenwales on 2007-08-22
Well, kind of solved. I discovered that on these Ubuntu Dells that if you hit ESC during GRUB there is an option to reload the OS. Took about 20 minutes and I was right back to factory condition. Dell got one thing right.

---

### Post by davidmorawski on 2007-08-22
After running into a similar problem, I've found a couple ways to deal with this issue.

The first is to add the following lines to your xorg.conf:```
Section "Extensions"
       Option  "Composite"     "Disable"
EndSection

```
This will disable any Desktop Effects, and you won't even be able to open up the Desktop Effects selection GUI (System>Preferences>Desktop Effects). I don't really care for this option, as it doesn't allow much flexibility.

The second option is a more brute force method, and is to simply delete the .gconf/apps/compiz folder in your home directory, which will wipe any previous Desktop Effects options you may have set up, effectively setting the default values (which, of course, are no desktop effects).

I'm not sure what the latter option will do on your machine, but it seems fairly harmless to me. Changing your X configuration file (xorg.conf) is absolutely harmless, as you can simply restore your previous settings with a backup copy of the file.

Hope this helps anyone in a similar bind,

Dave

---

### Post by aspasia82 on 2007-08-23
I also ran into this problem with desktop effects as well as while previewing certain screensavers.  I still haven't figured it out.
Does anyone know of any beta drivers for the Intel Integrated Graphics Media Accelerator 3100 for Inspiron 1420?

---

### Post by srt4play on 2007-08-23
[http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)

---

### Post by Dark Star on 2007-08-23
> **srt4play said:**
> [http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)
Thanks for the link :D

---

