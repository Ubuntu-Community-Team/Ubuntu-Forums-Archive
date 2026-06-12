---
title: "Disk Full!"
date: 2011-04-13
forum: Desktop Environments
---

### Post by pbhill on 2011-04-13
Something has rapidly filled up my hard drive. I have a 14 GB partition for root that only had 9 GB used the other day. Now it is full! Nothing has been installed to my knowledge. What is happening?

---

### Post by jwcalla on 2011-04-13
Have you opened the Disk Usage Analyzer to check directory sizes?

---

### Post by Krytarik on 2011-04-13
Also see this guide:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Greetings.

---

### Post by KegHead on 2011-04-13
Hi!

Somethings you could try:

sudo apt-get autoclean

sudo apt-get autoremove

You could also use bleachbit and/or Ubuntu tweak.

KegHead

11.04b2/classic/2.6.39-999

---

### Post by pbhill on 2011-04-14
I think I figured it out.... my backups  were supposed to go to an external drive (/media/USB STORAGE/Backups) however, since that drive is mounted on /media it was somehow filling up my root partition. Not sure how that works!
I resized my root partition and reinstalled. How can I keep backups only my USB hard drive?

---

### Post by vanadium on 2011-04-14
There was no need to reinstall, and there was no need to increase the system partition size.

It is not because your drive is mounted in /media that "it" was somehow filling your root partition. Rather, there was some mistake in the backup procedure, which did not write where you want it to write. This makes me wonder what backup procedure you use: must have been one you ran as root.

---

### Post by pbhill on 2011-04-14
I use Lucky Backup, which runs as root. See the attached screenshot that shows my configuration.
With the fresh install root uses only 4.3 GB.

---

### Post by SeijiSensei on 2011-04-14
If the external drive isn't mounted when the backup takes place, then the files will be written to the root filesystem.  I don't know if you can modify "Lucky Backup" or wrap it in a shell script, but you should add a check for whether the drive is mounted before continuing like this:

```

if [ "$(mount | grep '/media/USB')" != "" ] 
then
    run the backup
elif
    mail -s 'Backup Failed' you@example.com
fi

```

You'll need to install the package bsd-mailx to use the "mail" command.

---

### Post by pbhill on 2011-04-14
> **SeijiSensei said:**
> If the external drive isn't mounted when the backup takes place, then the files will be written to the root filesystem.  I don't know if you can modify "Lucky Backup" or wrap it in a shell script, but you should add a check for whether the drive is mounted before continuing like this:

```

if [ "$(mount | grep '/media/USB')" != "" ] 
then
    run the backup
elif
    mail -s 'Backup Failed' you@example.com
fi

```

You'll need to install the package bsd-mailx to use the "mail" command.

Thanks! I'll try this.

---

