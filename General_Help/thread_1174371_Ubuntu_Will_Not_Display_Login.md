---
title: "Ubuntu Will Not Display Login"
date: 2009-05-30
forum: General Help
---

### Post by chouse626 on 2009-05-30
I'm currently running Ubuntu Jaunty Jackalope and was attempting to do a dual monitor setup and it wasn't working correctly so I didn't save the settings that I was tinkering with in the System Administration or Preferences "Display" section.  I left my computer running and at some point it locked up during the night.  I rebooted and it told me there was no resume image or something along those lines, the Ubuntu logo loads up, but then my login doesn't display and the system will not load.  I've read through numberous forums about trying CTRL+ALT and many keys to press and nothing seems to be working.  I'm thinking this is some king of video driver issue.  I'd rather not have to do a complete reinstall as I have some valuable files on there, but if that has to be done I guess it has to be done.  Does anyone know what the issue might be or experienced a similar problem?  I'm using an HP Pavilion DV6449US.

Any info will be greatly appreciated.  Oh and I'm new to Linux so if you have a solution try to give me a breakdown for dummies.

---

### Post by pastalavista on 2009-05-30
Boot in 'recovery mode' and select 'Fix broken packages' and 'Repair X' then exit/reboot.

edit: to boot in recovery mode you might need to press 'escape' at the first boot screen if you have the boot menu hidden

---

### Post by chouse626 on 2009-05-30
I will give that a try.  I did find this command somewhere throughout the forum

dmesg | grep -i failed and it showed me that....


Resume from disk failed
uvcvideo: Failed to query   (this error was multiple times)

So now I'm wondering if it's some kind of resume/hibernate issue

---

### Post by sigixv on 2009-05-30
can't you do a recovery in text mode? or at least see where the problem is when in text mode?

i thought it should be possible to log in as root and change xconf or other files that might be blocking the gui. Perhaps you can replace them from the ones on your live cd

---

### Post by pastalavista on 2009-05-30
> **sigixv said:**
> can't you do a recovery in text mode? or at least see where the problem is when in text mode?

i thought it should be possible to log in as root and change xconf or other files that might be blocking the gui. Perhaps you can replace them from the ones on your live cd

If the "repair X" option doesn't work, you can reboot in recovery mode and select "Root Terminal". Then you could try
```
sudo dpkg-reconfigure xserver-xorg
```
or (I don't recommend this.. you can really make a mess of things if not careful)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
``` to backup the file before editing it and then ```
sudo nano /etc/X11/xorg.conf
```

---

