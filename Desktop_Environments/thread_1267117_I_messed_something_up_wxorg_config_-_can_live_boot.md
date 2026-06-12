---
title: "I messed something up w/xorg config - can live boot in..."
date: 2009-09-15
forum: Desktop Environments
---

### Post by jzacsh on 2009-09-15
after a reboot one day my resolution was set to oddly low, so i was trying to fix it. i found this post on [**_changing screen resolution_**]("http://ubuntuforums.org/showthread.php?t=83973"):
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)


after a brief (apparently, too brief) look at that post ^ I ran: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
/etc/init.d/gdm restart

```

*this caused my screen to go black immediately*. I rebooted the computer (forced shutdown), than when I got to GRUB and selected the Ubuntu install (*two drives in this tower: one w/xp, one w/ub*), the screen goes black and never does anything - nothing happens.

I tried this [_**IRC #ubuntu channel**_]("http://irclogs.ubuntu.com/2009/09/10/%23ubuntu.html") (*ctrl+F my handle "jzacsh" on that page to see*). someone said it doesn't sound like the command i ran could've caused this. then it was suggested I try:
> chroot into the troubled install while booted w/a LiveCD,
```
sudo dpkg-reconfigure xserver-xorg
```


i did successfully chroot in and ran the command successfully w/no errors. unfortunately, it doesn't solve the problem. 

[B]anybody have any ideas? this drive has a development server on it w/a lot of work that i'd hate to have to reconfigure/install.
[/B]
*let me know if i'm posting this in the wrong forum (maybe I should be putting this in [_Multimedia and Video_]("http://ubuntuforums.org/forumdisplay.php?f=334"))*

---

### Post by juancarlospaco on 2009-09-15
purge and reinstall the X
:)

---

### Post by jzacsh on 2009-09-15
> **juancarlospaco said:**
> purge and reinstall the X
:)
oh,okay thanks. so.... would this be right?
```
sudo apt-get uninstall xorg
```

---

### Post by jzacsh on 2009-09-15
anyone?

---

### Post by jzacsh on 2009-09-18
> **jzacsh said:**
> oh,okay thanks. so.... would this be right?
```
sudo apt-get uninstall xorg
```

for anyone else coming by - I believe its:
```
sudo apt-get purge x
```
i'm assuming x, because it was just suggested to me, so I'm taking it literally - i don't know if "x" includes xorg? if xorg has little to do with this... but i'll post here when i fix the problem.

okay, trying to purge x didn't work. so i purged exactly what i originally posted about: xserver-xorg, like so:
```
sudo apt-get purge xserver-xorg
```
after of course booting from a LiveCD, and mounting the troublesome drive, then:
**sudo chroot /media/disk** (*disk being what my drive mounted as*)

* i've also been ignoring all the errors about /dev/null (*because, i guess i don' know how to use chroot to allow fstab to work right?*)

I'll see now how installing goes...

---

### Post by Joeb454 on 2009-09-18
Thread moved to Desktop Environments at OP request :)

---

### Post by jzacsh on 2009-09-18
so purging and reinstalling xserv-xorg didn't do the job.
anymore ideas?? to have to reinstall my development server is really going to.... well, push back development. any more help at all?

---

