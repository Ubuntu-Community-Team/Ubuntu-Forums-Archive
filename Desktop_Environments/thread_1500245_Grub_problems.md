---
title: "Grub problems"
date: 2010-06-02
forum: Desktop Environments
---

### Post by sgosnell on 2010-06-02
My wife's laptop is a dual-boot machine, with Vista.  The grub menu is slightly borked, and I can't figure out how to fix it.  Running update-grub gives incorrect results, and thus a bad menu.  It reports sda2 as Windows recovery partition, and sda3 as Vista loader.  This is wrong, and the two are reversed.  sda2 is the Vista loader, and sda3 is the recovery partition.  Trying to boot what grub calls Vista gives the recovery menu, and booting what grub calls the recovery partition gives a normal Vista boot.  I want Vista as the default, because that's what she knows, and I can do that by making the recovery partition the nominal default, but it looks odd, and it will eventually cause major problems, because she knows nothing about computers, and I'm away from home more than half the time.  When she has a problem, she'll get her brother-in-law to help, and he will see that menu and the game is over.  No use trying to explain it to him.

How can I fix the menu?  Reading the community docs shows how to add menu items, but not how to edit existing items, and the underlying problem is that update-grub is reading the partitions wrong.  That's what I really need to fix.

---

### Post by oldfred on 2010-06-03
the quick and easy to make a default boot:
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

 I added this :
gksudo gedit /etc/default/grub:
```
GRUB_DISABLE_OS_PROBER=true
```

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

after all changes
```
sudo update-grub
```

---

### Post by sgosnell on 2010-06-03
OK, I wasn't snapping to the fact that the custom files in /etc/grub.d override the base file, I was misreading the documentation.  Disabling the os_prober and editing the custom files worked.  I still don't know why the prober was returning incorrect information, but my problem is solved.  Thanks for the help.

---

