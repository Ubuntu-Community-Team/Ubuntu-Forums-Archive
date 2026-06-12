---
title: "Can't boot after windows"
date: 2006-08-24
forum: Desktop Environments
---

### Post by m.musashi on 2006-08-24
I am still dual booting and after using windows and booting ubuntu, ubuntu freezes at "loading files" (the second line). It will sit there probably indefinately. If I shut the computer off and restart, then it will boot normally. If I use windows again and then boot ubuntu the same problem happens again. This is realatvily new. The only change was I added another dvd burner.

Thanks.

---

### Post by ciscosurfer on 2006-08-24
Could be a problem with GRUB and/or your fstab file could be messed up.  Check both and make sure something hasn't gone awry.

---

### Post by m.musashi on 2006-08-25
Thanks for the feedback. I've looked at both the fstab and grub files and they both look fine (though I don't have a photographic memory). I don't know what booting windows would do to the grub file but it's only after booting windows that the problem manifests and after it sticks and I forcibly turn off the computer and start up again it works fine as long as boot only ubuntu. Once I boot windows and then ubuntu again the problem returns.

While not a show stopper, it is annoying.

Thanks.

---

### Post by ciscosurfer on 2006-08-25
Well, you've got me thinking.  I'll get back to you on this if I come up with anything.  Otherwise, I must say, that is quite interesting and right-off-the-bat, I don't have a clue what's causing this.  You say it's relatively new.  Can you remember if you accidentally installed something new or made any modifications to any files recently?

---

### Post by m.musashi on 2006-08-25
Actually, the only change is that I installed a new dvd burner. I also added a new monitor but it was acting up so I went ahead and reinstalled ubuntu. It was working fine with the new monitor and then I added the new drive. That is the only change.

---

### Post by ciscosurfer on 2006-08-26
Hmm...still thinking.  I wonder if the dvd-burner is causing these issues.  Can you post both your fstab and the output from 'mount'?

---

### Post by m.musashi on 2006-08-26
I just did a clean install of windows - and all that that implies - so that also overwrote GRUB. At the moment, I can't boot ubuntu. If I can figure out how to reinstall GRUB without reinstalling Dapper I will. Otherwise I'll just reinstall Dapper too. In that case, the problem may resolve itself or not. I'll just have to wait and see.

Thanks for the help so far. You just can't beat this forum. If you happen to know an easy way to get GRUB back I'd appreciate it.

---

### Post by m.musashi on 2006-08-26
Okay, I grub back and i'm into ubuntu again. The same problem still exists (i.e. freezes on loading first time after booting windows). I will go in and get the fstab output. What exactly is the 'mount' part?

Thanks

---

### Post by ciscosurfer on 2006-08-26
Glad to hear you got back into Ubuntu.  Did you use [this page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")?

I wanted to see the output after you issue the 'mount' command (sorry if I was vague before)```
mount
```

---

### Post by m.musashi on 2006-08-27
Thanks again for the help. Sorry I didn't reply sooner. Here is the fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1 	/media/windows	ntfs nls=utf8,umask=0222 0 0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1 	/media/share 	vfat iocharset=utf8,umask=000 0 0
/dev/hdc7	/media/suse	reiserfs defaults 0 0
```
And mount:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1 	/media/windows	ntfs nls=utf8,umask=0222 0 0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1 	/media/share 	vfat iocharset=utf8,umask=000 0 0
/dev/hdc7	/media/suse	reiserfs defaults 0 0
```
I see that the fstab file does not have an evtry for the new dvd. Of course I don't know why that would cause ubuntu not to boot after windows. It stops at the point where it says "mounting root file system". I finally wrote it down since I couldn't remember.

Hope this helps to identify the problem. Thanks.

---

### Post by varchar32 on 2006-08-28
Hi,

I have the exact same problem. sometimes I need to restart machine 3-4 times until ubuntu starts booting normal. it happens randomly most of the time. I tested mandrake sometime back it was behaving similar. I built up a new system and same thing was happening again. ](*,) 
Some people advising unplug usb devices. I have a mouse and logitech camera and Dell lcd with usb hub and 4 port.  I dont want to remove any usb device since I have only 2. if it is because of usb I will wait for a better OS comes with a simple usb support at least. USB is a standard now and any OS has problems with booting because of a usb mouse or camera with  is not a real OS in my mind....

thanks

---

### Post by m.musashi on 2006-08-29
At first I was thinking your problem is different but then I remembered that I also added a new monitor with usb hub. I actually did a clean install after adding this monitor but I can't recall if the problem manifested right then or only after the new dvd. I will have to try booting without the monitor usb hub connected and see if that solved the problem. If so, then it looks like there is an issue with usb support.

Thanks for the input. This may be the key to the problem. I'll post after I have a chance to test this.

I should point out, however, that I have no problems with usb support once the computer boots. I can add a camera, flash drive or external hd via usb without any problems. Perhaps it's only a boot issue. Anyway, I'll try and post back.

---

### Post by m.musashi on 2006-08-31
Varchar32, it would seem you have pinpointed my problem. I had a chance to test this new theory and when I unplug the usb hub on my monitor and boot windows and then ubuntu I do not have any problem. It would seem that the usb hub is the source of the problem. Would that qualify as a bug then? What's odd, however, is that it will boot with the usb hub connected as long as I don't boot windows. Once I boot windows, I  have the problem once, hard reset and then I can boot ubuntu as many times as I like - with the hub connected - without any problems. That would suggest there is more to it than just a usb problem or perhaps a different, but related issue.

Anyway, I know what the problem is and how to avoid it. I just don't know how to FIX it. Any ideas?

Thanks.

---

### Post by mssever on 2006-08-31
My thought would be to file a bug report on Launchpad. I don't have a USB hub to test with, but perhaps something doesn't quite get cleared during the Windows reboot. What happens if you shut down Windows and power down for about 30 seconds?

@Varchar32: I've been amazed at how far USB support has come in Linux. This sounds like a bug that--while annoying--only occurs in a very specific situation. Every OS has those. And try reporting a bug for a certain other OS...

---

### Post by m.musashi on 2006-08-31
It doesn't seem to matter how long the computer is powered down. Sometimes I'm in windows one day and then shut down and come back the next day and boot ubuntu. If it is the first boot after windows it will still hang. Of course, I think my main board always has power to it. I haven't tried completely powering down so that would be something else to try.

I've never filed a bug. I tried before and needed to go through some registration process that for some reason I couldn't finish. I'll try again.

---

