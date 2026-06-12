---
title: "No Video"
date: 2005-12-22
forum: Desktop Environments
---

### Post by Thanatos10 on 2005-12-22
Well first I'm very new to Linux and I hope this question isn't to far off base.  I loaded the Ubuntu CD everything seemed OK until I rebooted.  I got the Ubuntu start screen.  Then when it was done the screen went black and my monitor (LCD) stated "OUT OF RANGE".  I'm thing that the display setting are way out of whack for my monitor or video card (6600LE).

Any ideas on how to force Ubuntu to startup in and lower resolution or frequency?  Is there a "safe start" as in XP?

Any ideas would be most welcome

Scott.

---

### Post by DevilsAdvocate on 2005-12-23
Umm, if I recall correct, when you boot from the CD it will tell you to hit some function key to see the boot options.  I know you can manually configure the windows server (X) but I don't know how.  Hopefully, someone w/ more knowledge will break you off some.-+

Curious, is Thanatos your real name or made up?  Isn't Thanatos the Greek God of death or something like that?

---

### Post by antidrugue on 2005-12-23
When you boot your computer, hit ESC to bring the grub loader (just after the BIOS screen). Then boot in "recovery mode". From there you can reconfigure your x server:

```

dpkg-reconfigure xserver-xorg

```

Just choose the right options. If you don't know the answer to a question, just leave it default or blank.

Then reboot.

---

