---
title: "KDE Device Notifier opens device in Nautilus not Dolphin"
date: 2009-11-24
forum: Desktop Environments
---

### Post by G0lg0thaZA on 2009-11-24
Hi All...

I did a fresh install of Kubuntu 9.10 on my laptop. When I attach a USB flash drive (various different ones) the widget Device Notifier sees the new device and mounts it. Sometimes it even opens it with the Nautilus file manger (automatically). I need nautilus for other apps I use (like Dropbox).

When I click on the mounted USB disk in the Device Notifier it open in Dolphin however.

But the problem starts when I want to unmount (safely remove) the USB disk.

When I click the unmount link in the Device Notifier (next to the mounted device) it give the error "Could not unmount the device. One or more files on this device are open within an application."

If I unmount it in the Nautilus file manager (or in the konsole) and then mount it again with the Device Notifier widget (without removing it) I can then successfully unmount it.

So it would appear that Nautilus is holding on to the mounted USB (somehow) and does not allow other apps to unmount it until it has been unmounted first with Nautilus. 

I'd like Dolphin to be the only file manger used with the USB flash drives I insert. Where can this behaviour be changed? Either (1) Nautilus must not mount the USB flash drive OR (2) it must be the default file browser in KDE - I prefer option (1).

Hope you can point me in the right direction.

TIA
Frank

---

### Post by G0lg0thaZA on 2009-11-25
bump

---

### Post by Zorael on 2009-11-25
What is the default file manager set to be in System Settings -> Default Applications? The device notifier plasma widget should honor that setting.

---

### Post by G0lg0thaZA on 2009-11-26
Hi 

Thanx for the reply... it is set for Dolphin. But still Nautilus seems to be the master.

More info:

If I plug in a usb flash disc the Device Notifier widget shows it and Nautilus launches with the usb disc content. If I click the link to the usb stick in the Device Notifier it opens with Dolphin as well.

If I try to unmount it in Dolphin I get the following error: "org.freedesktop.HAL.Device.Volume.NotMountedByHal: Device to unmount is not in /media/hal.mtab so it is not mounted by HAL"

Once unmounted in nautilus I can unmount it in dolphin.

"tail -f /var/log/messages" does not show anything except that the stick is plugged in and when it is physically removed.

Any further ideas?

---

### Post by MickS on 2009-11-29
Cant help I'm afraid other than to give the thread a bump and to say I have the same problem, 


Mick

---

### Post by G0lg0thaZA on 2009-11-29
Thanx ;-)

At least I know I am not the only one then...

---

### Post by Dullstar on 2009-11-30
I thought Kubuntu didn't include nautilus.  Did you guys run sudo apt-get install ubuntu-desktop?  You could use the the package manager to uninstall it, if you think it's safe.  I wouldn't say you should go and do it right now, though, because I'm not 100% sure it's safe.  I see no reason why it wouldn't be safe, but, well, as they say, better safe than sorry!

---

### Post by G0lg0thaZA on 2009-11-30
Hey

As far as I know nautilus does not come by default. I do use Dropbox though, and I believe it was when I installed it in KDE that nautilus was added...

The question is: why is nautilus now the default "mounter" of usb discs and can it be changed back to dolphin?

I'm almost at the point of installing plain Ubuntu again... ;-)

---

### Post by akudewan on 2009-11-30
As you said, Nautilus was probably installed when you installed Dropbox.

Problem 1: Folders open in Nautilus.
Solution: As Zorael pointed out: change the default file manager in systemsettings > Default Applications > File Manager > Dolphin. ("Open Folder" seems to be Nautilus)
[[IMG]http://imgur.com/wmuRjs.png[/IMG]](http://imgur.com/wmuRj.png)


Problem 2: KDE cannot unmount drives, Nautilus/gvfs takes control of them.
Solution: My post here: [http://ubuntuforums.org/showthread.php?p=8408560](http://ubuntuforums.org/showthread.php?p=8408560)


About Dropbox: I also use it to sync files, but as long as I don't click on the tray icon, nautilus doesn't bother me

Hope this helps.

---

### Post by G0lg0thaZA on 2009-11-30
Hi

Thanx for the info. I tried it, but unfortunately it did not work. Actually it does not pop up nautilus when I insert the USB stick anymore, but it still does not allow dolphin to unmount it. I must start nautilus in a terminal and then unmount it there before KDE will unmount properly.

My default file manager is definitely Dolphin.

Thanx for trying ;-)

---

### Post by G0lg0thaZA on 2009-12-01
Hi

Finally got fed up with this, but want to continue trying out KDE - so I just changed the default File Manager to Nautilus. I can not unmount it in the device notifier, but at least I can quickly unmount it in the open Nautilus file browser.

Thanx for the help...

---

### Post by nossifer on 2010-02-22
I have the same issue.  Also, I use Dropbox. At least the 'answer' seems to be to remove it in Nautilus... just tried it and it worked.

---

### Post by birnam on 2010-02-28
I ran into this problem after installing Dropbox as well. The installation seems to have started up the gvfs daemon. In the system activity window I killed all of the gvfs related processes I saw, which for me included:

gvfs-gdu-volume-monitor
gvfs-gphoto2-volume-monitor
gvfsd
gvfsd-burn
gvfsd-metadata
gvfsd-trash

After killing these, everything was back to normal.

---

### Post by G0lg0thaZA on 2010-03-01
Schweet - will give it a go next time I try Kubuntu - for now, I am back in Ubuntu ;-)

---

### Post by NissePisse123 on 2010-06-27
This is what worked for me:
```
gconftool --type Boolean --set /apps/nautilus/preferences/media_automount  false
```
See also: [https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by inhuman!!! on 2010-09-04
Thanks Man
It works

---

### Post by c42105 on 2010-09-27
> **NissePisse123 said:**
> This is what worked for me:
```
gconftool --type Boolean --set /apps/nautilus/preferences/media_automount  false
```See also: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)


So simple and so effective! Many thanks!

---

