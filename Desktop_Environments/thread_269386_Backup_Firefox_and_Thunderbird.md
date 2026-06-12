---
title: "Backup Firefox and Thunderbird"
date: 2006-10-01
forum: Desktop Environments
---

### Post by sjpritch25 on 2006-10-01
Just wanted to know how i can backup my Firefox and Thunderbird settings.  I mostly want to backup extension, bookmarks and passwords.  Also, would like to back up my emails.

---

### Post by lagagnon on 2006-10-01
Firefox settings are in your ~/.mozilla directory and TBird and your emails are in ~/.thunderbird (where ~ means your home directory). So first of all clear your Browser cache and just back up both those directories - I would use tar for doing that in one quick step.

---

### Post by jpkotta on 2006-10-01
All settings are stored in ~/.thunderbird and ~/.mozilla.  You can save a lot of space in your backups if you exclude the Cache subdirectory for Firefox (and you don't need to back the cache up).

This should do it:
```
(cd ; tar jcvf firefox-thunderbird-`date +%y%m%d`.tar.bz2 --exclude=.mozilla/*/Cache/* .mozilla/ .thunderbird/)
```

---

### Post by sjpritch25 on 2006-10-01
It worked but all i saw was firefox in the tar file.

---

### Post by sjpritch25 on 2006-10-01
When i type
```
stefan@ubuntu:~$ ~/.mozilla
bash: /home/stefan/.mozilla: is a directory
stefan@ubuntu:~$ cd /home/stefan/.mozilla
stefan@ubuntu:~/.mozilla$ dir
appreg  firefox  pluginreg.dat  plugins
stefan@ubuntu:~/.mozilla$

```

Here is what i get when i look for thunderbird

```
stefan@ubuntu:~$ ~/.thunderbird
bash: /home/stefan/.thunderbird: No such file or directory

```

Where are my Thunderbird settings????

---

### Post by NetworkGuy on 2006-10-01
Look at ~/mozilla-thunderbird

---

### Post by sjpritch25 on 2006-10-01
That worked, but i am going to have to clean out my emails before i tackle it.  Thanks everyone.

---

### Post by jpkotta on 2006-10-29
[QUOTE=sjpritch25]
When i upgrade to 6.10, i plan on doing a clean install.  I just wanted to know what command i would use to replace Mozilla Firefox settings and Thunderbird settings i backedup.  Thanks.[/QUOTE]

If the backup is ~/mozilla_backup.tar.gz, then
```
cd 
tar zxvf ~/mozilla_backup.tar.gz
```

---

### Post by sjpritch25 on 2006-10-29
what about in /home folder.

---

### Post by abovett on 2006-10-29
> **sjpritch25 said:**
> what about in /home folder.Not sure exactly what you mean - do you mean that you saved the backup file in /home? If so, try:```
cd ~
tar zxvf /home/mozilla_backup.tar.gz
```

---

### Post by sjpritch25 on 2006-10-30
Okay, i have this file in my /home folder

> 
firefox-thunderbird-061028.tar.bz2


How do i extract the backup????  Should i install thunderbird before i do this????

---

### Post by ciscosurfer on 2006-10-30
> **sjpritch25 said:**
> ...How do i extract the backup????  Should i install thunderbird before i do this????

Yes.  Install and then run it once.  That will create your Thunderbird directory.  Once you have installed, you can then uncompress the file you compressed and move your Thunderbird files to their appropriate directory within ~/.mozilla-thunderbird

---

### Post by abovett on 2006-11-01
> **ciscosurfer said:**
> Yes.  Install and then run it once.  That will create your Thunderbird directory.
Actually, if the archive file was created correctly, it should restore the files to their correct locations, creating the Thundserbird directory in the process. Thus it's better to extract the files from the archive _before_ running Thunderbird for the first time - you could even extract them before installing Thunderbird. That way, when you run it for the first time it will find it's files already present and correct.

If you do it the other way around it can cause some small issues as if it doesn't find a profile when it runs it creates a new profile with a different identifier, which can cause confusion when you then restore the data from the old profile.

Cheers

Andy

---

### Post by ciscosurfer on 2006-11-01
> **abovett said:**
> Actually, if the archive file was created correctly, it should restore the files to their correct locations, creating the Thundserbird directory in the process. Thus it's better to extract the files from the archive _before_ running Thunderbird for the first time - you could even extract them before installing Thunderbird. That way, when you run it for the first time it will find it's files already present and correct.

If you do it the other way around it can cause some small issues as if it doesn't find a profile when it runs it creates a new profile with a different identifier, which can cause confusion when you then restore the data from the old profile.

Cheers

Andy

Would doing it your way create a profile folder from the older firefox or thunderbird your are trying to backup from?  If you're starting fresh, a new profile folder is just fine in my experience.  But please, let's continue to discuss this because I am curious :D

---

### Post by sjpritch25 on 2006-11-01
It worked great, but i just lost a couple emails.  I did because i created one of my accounts before i placed the backup folders.  Firefox worked great and some of my extension weren't compatible with Firefox 2.0.  I didn't have one issue that came up.    Thanks everyone:p

---

### Post by abovett on 2006-11-08
> **ciscosurfer said:**
> Would doing it your way create a profile folder from the older firefox or thunderbird your are trying to backup from?
Not quite sure what you mean. If you mean there might be things in the profile that are not compatible with the newer version I suppose it's possible but if it happens then that's a bug, because this scenario is exactly the same as when you upgrade from one version of firefox or Thunderbird to the next. It has to be able to use the profile created by the previous version.

>  If you're starting fresh, a new profile folder is just fine in my experience.
Yes, but some of us don't want to "Start fresh". I for one have a lot of settings and preferences in my Thunderbird setup which I would not want to lose. I would only ever consider recreating the profile from scratch if the other method went wrong.

Cheers

Andy

---

### Post by ciscosurfer on 2006-11-08
Whatever works for you 8)

---

### Post by sternkanz on 2008-04-26
So, I just zip the .mozilla folder into a tar.gz, then reinstall ubuntu, then update mozilla(if required), then unpack the tar.gz file into my home folder again?

And does anyone know if this will work for moving my settings in Gutsy under Firefox 2.0.0.14 to Hardy under Firefox 3 beta ?

Thanks,

Stern

---

