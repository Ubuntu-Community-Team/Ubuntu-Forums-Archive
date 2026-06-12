---
title: "KDE 3.5.3 - missing device icons"
date: 2006-06-01
forum: Desktop Environments
---

### Post by tgrzejsz on 2006-06-01
Hi,
After installing latest KDE devices icons are gone from my desktop, although they are configured to be there. Does anybody else see this? Is it a bug?

Greetings,
Tomek

---

### Post by msak007 on 2006-06-05
[QUOTE=tgrzejsz]Hi,
After installing latest KDE devices icons are gone from my desktop, although they are configured to be there. Does anybody else see this? Is it a bug?

Greetings,
Tomek[/QUOTE]

I just upgraded to KDE 3.5.3 last night and noticed this. I checked the Desktop properties, and I have it checked to show mounted hard disk volumes but the icons are missing. Also I found it rather strange that I would uncheck that option, click Apply or OK, go back into the properties, and the box would still be checked but no icons. I haven't tested a CD or other device to see if the icon shows up when mounted, but from my experience mounted hard disks icons no longer show up. Will follow up tonight when I get home about other devices I try.

---

### Post by msak007 on 2006-06-06
Well not sure what happened but my icons came back. I don't remember rebooting after the initial reboot after the upgrade, but after leaving it on all day and coming home from work, I went to Desktop properties, enabled the mounted hard disk device icon setting, and voila they all came back. :-k I did plug in my MP3 player first to see if it was detected, and it mounted it and put an icon on the Desktop.

EDIT: I just confirmed that what I did is what fixed the problem. After restarting X (CTRL+ALT+BACKSPACE), all my icons disappeared again. I enabled / disabled the option several times, restarted X again, and even restarted the comp. The only thing that brought the icons back was to plug in my MP3 player again, wait for it to be mounted and the Desktop icon to appear, then go back to Desktop properties and enable the mounted hard disk icons again (if the option is already checked, the icons come back automatically after plugging it in). Can anybody replicate this issue? I restarted X and the comp several times before upgrading to KDE 3.5.3, and didn't seem to have this issue (as far as I can remember). I haven't searched for any bug reports, but if anybody else can confirm this we should file a bug report.

---

### Post by moopere on 2006-06-07
[QUOTE=msak007]Well not sure what happened but my icons came back. I don't remember rebooting after the initial reboot after the upgrade, but after leaving it on all day and coming home from work, I went to Desktop properties, enabled the mounted hard disk device icon setting, and voila they all came back. :-k I did plug in my MP3 player first to see if it was detected, and it mounted it and put an icon on the Desktop.

EDIT: I just confirmed that what I did is what fixed the problem. After restarting X (CTRL+ALT+BACKSPACE), all my icons disappeared again. I enabled / disabled the option several times, restarted X again, and even restarted the comp. The only thing that brought the icons back was to plug in my MP3 player again, wait for it to be mounted and the Desktop icon to appear, then go back to Desktop properties and enable the mounted hard disk icons again (if the option is already checked, the icons come back automatically after plugging it in). Can anybody replicate this issue? I restarted X and the comp several times before upgrading to KDE 3.5.3, and didn't seem to have this issue (as far as I can remember). I haven't searched for any bug reports, but if anybody else can confirm this we should file a bug report.[/QUOTE]

Yep, thats what happens to me too.  I didn't use an mp3 player though, it works as you describe with a usb stick drive as well :)

Regards,
Craig

---

### Post by KubuntuKilledMe on 2006-06-07
The icons come and go - I get them back when i connect to a remote share, which should add a new icon on the desktop, but instead brings them all back. Sometimes they are there, sometimes they aren't. I really hope the KDE people consider this a bug and not a feature, because it has been present in similar forms in 3 releases and its starting to stink.

---

### Post by msak007 on 2006-06-07
Yea they disappeared again yesterday after a reboot so I tested a CD and the icons came back - pretty much any device / drive that's mounted and adds an icon to the Desktop will bring back all of the missing icons. To me it's not a *huge* issue as I don't reboot or restart X often unless I'm testing (breaking :D) something, but it is annoying nonetheless and should be fixed.

---

### Post by ernstblaauw on 2007-05-23
Is a fix available? I'm running KDE 3.5.7 and I also don't have those icons...

---

### Post by Robin T Cox on 2007-05-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/116375](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/116375) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I upgraded to KDE 3.5.7 the day before yesterday, and ever since I have also had this problem.

---

### Post by grinias on 2007-10-14
Today October 14 of 2007, in candidate release of kubuntu 7.10, the problem remains. Could someone of the development team describe exactly what happens? Is it a problem of kde 3.5 or of Kubuntu? Any solution?

---

### Post by ernstblaauw on 2007-10-19
> **grinias said:**
> Today October 14 of 2007, in candidate release of kubuntu 7.10, the problem remains. Could someone of the development team describe exactly what happens? Is it a problem of kde 3.5 or of Kubuntu? Any solution?
Yesterday, I installed the final version of Kubuntu (a clean install). Still no solution. Hopefully, someone can write a patch.

---

### Post by Starlight on 2007-11-03
I recently installed Kubuntu 7.10 on a new computer, and I have the same problem. On my old computer I had Kubuntu 7.04, and I had all the device icons on my desktop...

---

### Post by HeavyAl on 2007-12-20
I see this thread is over a month old but I thought I'd add my own 2c in that I have the same problem. Normally I'm a gnome guy but I've been looking at the new kde 4 rc's and seeing how it's coming along I figured I'd give the old kde 3 a spin again to see what might have changed since I tried it last. I get no desktop icons at all - no home icon, no drives, no configuration icons, nothing at all. 

Like the previous posters, once I insert a usb device (thumb drive in my case) all the drives show up suddenly on the desktop but there are still none of the expected 'colorful' home icons and unplugging the thumb drive ends up leaving the icon for it on the desktop. Weird.

---

### Post by grinias on 2008-01-18
Device icons appeared today in Kubuntu 7.10 (KDE 3.5.8 ), once I changed the wallpaper of one desktop!!! Furthermore, the letters of desktop icons became black with white 
surrounding (they were white since installation). Haven't logout yet. Hope after logout  (or reboot) device icons will still be there :) 

Very Very strange behaviour...

EDIT: Unfortunately, it did it again after reboot. Device icons disappeared...

---

### Post by dirku2000 on 2008-02-25
I got the same problem with Kubuntu 7.10 and also now with Kubuntu 8.04 Alpha5.

I installed Sidux and had no problems like that but a major  problem with the hardware support. Missing w-lan card is is one to much with my Notebook.

---

### Post by GSX on 2008-02-25
Edit manually /usr/share/services/kded/mediamanager.desktop

The line 
```
X-KDE-Kded-phase=1
```

change to 
```
X-KDE-Kded-phase=0
```

That should fix this Problem.

---

