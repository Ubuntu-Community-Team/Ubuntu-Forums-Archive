---
title: "Unable To Mount Volume"
date: 2009-03-28
forum: General Help
---

### Post by Punkage on 2009-03-28
Ive just installed Ubuntu onto my computer after windows has failed to start on me, so formatted the drive and I have a fresh install on.

Ive got two int.hdd one with ubuntu the other is currently empty, and I also have an ext.hdd which everything is saved to.

I cannot access the empty int.hdd or my ext.hdd

Ive tried looking at various other threads about this but none has seemed to worked

Can anyone help me please

---

### Post by Punkage on 2009-03-28
anyone...been trying to sort this our for hours now and its really annoying me

---

### Post by cybergalvez on 2009-03-28
are you getting an error message? Its been my experience that windows often does not dismoutn drives properly and you will have to force the mount.

---

### Post by Punkage on 2009-03-28
> **cybergalvez said:**
> are you getting an error message? Its been my experience that windows often does not dismoutn drives properly and you will have to force the mount.

Yup I get this message

[B]Cannot mount volume

Unable to mount the volume 'Punkages HDD'

$Logfile indicates unclean shutdown (0, 0) Failed to mount '/devsdc1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1 If you have Windows then disconnect the external devices by clicking on t5he 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you dont have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdc1 /media/Punkages HDD -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdc1 /media/Punkages HDD ntfs-3g force 00[/B]

And then this message

[B]Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/B]

Now I dont have access to windows at all so thats the first option out of the question...ive tried following instructions for force mounting it but it doesnt seem to work so I must be doing something wrong

---

### Post by Punkage on 2009-03-28
im being told that I cannot force mount and im getting this message again

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/windows_d -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/windows_d ntfs-3g force 0 0


that was through the terminal and ive done it by editing the fstab file.

When I got to clock the hdd now though system then computer im being told that "You are not privileged to mount the volume' now.

Any ideas for the new problem

---

### Post by rumfoord on 2009-04-03
I have a similar problem - Vista has had its boot file corrupted, having gone screwy during boot-up, and now I cannot access my Windows partition from Linux (where the majority of my files are stored). I'm being told that I am not privileged to mount the volume, indicating that the partition has been locked or something by NTFS (as happens when Vista is hibernated).
Is it possible to force a successful mount so that I can recover my files prior to Vista repair/reinstall?
I have been looking at a post on the dreamlinux forum which may help, but I don't know how different either of these situations are. The link is:
[http://dreamlinuxforums.org/index.php?topic=2540.0](http://dreamlinuxforums.org/index.php?topic=2540.0)
Any help with this would be appreciated. Many thanks.

---

### Post by rumfoord on 2009-04-10
I have now managed to mount my windows partition drive. It seems that when windows isn't shut down properly. a log file is left which determines the access to the drive (or something like that anyway) - clearing the logfile will sort it. This can be done using ntfsfix.

First, check that you have the required ntfs packages:
type: sudo apt-get install ntfs-3g
      sudo apt-get install ntfs-config
      sudo apt-get install ntfsprogs

Now you need to know the id of the drive that cannot be mounted. In my case it was /dev/sda3, so the command is
      sudo ntfsfix /dev/sda3

This will check whether the drive can be mounted, and if not will correct the errors. If this is successful, you will get a message similar to:

      NTFS partition /dev/sda3 was processed successfully.

You can now mount the drive manually:
      sudo mount /dev/sda3

This worked for me, and hopefully it will work for you.
Regards,
Rum

---

