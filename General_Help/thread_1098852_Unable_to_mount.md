---
title: "Unable to mount"
date: 2009-03-17
forum: General Help
---

### Post by morisila.ardiel on 2009-03-17
I've got intrepid on an hp pavillion dv6000, and going to plug in an external harddrive, I get this:

Unable to mount SPARTA
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

-and-

Cannot mount volume
Unable to mount the volume 'SPARTA'

Details:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denided because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: Mount -t ntfs-3g/dev/sdb/media/SPARTA -o force Or add the option to the relevent row in the /etc/tstab file: /dev/sdb1/media/SPARTA ntfs-3g force 0 0

Putting those in the terminal gets me (respectively)
"Only root can do that" 
-and-
"No such file or directory"

Any ideas? I'm hoping that I've overlooked something since I'm so new to Linux and that I'm just making some small mistake...

---

### Post by taurus on 2009-03-17
Why don't you reboot into windows (if you are dual booting) and unmount your external harddrive using the _safely remove hardware_ option (icon on bottom right corner) before you unplug it.  Then, reboot into Ubuntu and it should be mounted this time.

Otherwise, you have to use ntfsfix to fix that or mount it with the force option.

---

### Post by morisila.ardiel on 2009-03-17
Well I'm not dual booting, so I will have to go with the second option...But thank you for the suggestion.

---

### Post by taurus on 2009-03-17
And the second option is

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by morisila.ardiel on 2009-03-18
My problem has been solved. I plugged it into a friend's laptop to show her something and went through the "safely remove hardware" process. When I plugged it into my machine it was fine. Thanks for the suggestions though.

---

