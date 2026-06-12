---
title: "Backing up for reinstall"
date: 2009-04-16
forum: General Help
---

### Post by Syntax. on 2009-04-16
So I seem to have lost access to sudo,chow etc commands and I'm looking to reinstall ubuntu using wubi again.

Could someone please run me through the steps on how to backup my data.'

Is it possible to backup my programs like skype and keep all the username/passwords that are in it? same with firefox as I have many saved passwords which I would like to recover.

Also just general things such as desktop/documents.

Sudo has stopped working after I accidentaly deleted /usr and then put it back in the same spot. 

When I type sudo i get

sudo: must be setuid root

Thanks.

---

### Post by aaronp on 2009-04-16
you'll find that most of your config files are in hidden folders in your home directory. e.g. for firefox your profile will be in ~/.mozilla
backing these up and then copying them into your new home directory after reinstall should retain your settings.

---

### Post by Syntax. on 2009-04-16
Thanks

So Could I just replace the brand new /home folder with my old one without causing problems?

Are the programs I have installed also in /home? 

Or is there some other place I should be backing them up in?

Thanks.

---

### Post by codeseer on 2009-04-16
For the most part, the programs themselves are not in /home.

It sounds to me like you need to backup /home/username/Desktop, /home/username/Documents, /home/username/.mozilla and anything else under /home/username/ that contains files relating to the program configurations you want to keep.

I think a lot of people create a separate partition to mount /home to, because /home contains the majority of your documents and configuration information. Then they are able to reinstall Linux and keep their old /home directory.

I myself have taken the extra step to setup a bash script, with rsync, and assigned a cron job to it, so that every day my important files (no matter where they are on the system) are backed up to a separate drive. There are some things that aren't in /home that one might want to keep; for instance AppArmor profiles are in /etc/apparmor.d/.

Edit:

You might just want to make a copy of the entire /home directory and then you'll be able to pick and pull files from it after the reinstall. /home contains basically everything you did on your system that you didn't put a 'sudo' infront of.

---

### Post by Syntax. on 2009-04-16
Thanks for the help..

If everything is in /home/* Wouldn't just getting /home with everything in it and plonking it on the fresh install be sufficient?

---

### Post by codeseer on 2009-04-16
> **Syntax. said:**
> Thanks for the help..

If everything is in /home/* Wouldn't just getting /home with everything in it and plonking it on the fresh install be sufficient?

Yeah, it can be; it'd essentially be the same as those who have a separate /home partition, provided you use the same username.

PS: I think just about everybody has hashed their system like that before. I remember doing it back in the earlier days of Linux. I said, forget this I'm going back to Windows; then I ended up doing it on Windows also. :p

---

### Post by howefield on 2009-04-16
> **Syntax. said:**
> Thanks for the help..

If everything is in /home/* Wouldn't just getting /home with everything in it and plonking it on the fresh install be sufficient?

As previously said, not quite. You need to install programs that you previously had, after the basic Ubuntu install.

The home folder only has the settings for the programs.

Eg, if you previously had Virtualbox installed, you would need to install it again, but after copying your old home folder back, the configuration files for it would be intact.

---

### Post by aaronp on 2009-04-16
I find that I accumulate apps that I don't need as time rolls on and have a lot of configuration data in my home directory.
I have /home on a separate partition but I also back it up incrementally to an external location.

When I recently had to reinstall Ubuntu from scratch on a new PC, rather than just dumping /home back into the new install I installed all the apps that I know I required and then selectively replaced their /home/.configuration directories with my old ones, where I know I wanted to keep old settings.
This way I wasn't filling up my new /home partition with heaps of hidden directories that I don't need.
If I ever decide to reinstall an app that I used to use then I can just grab my config files from the backup /home directory of my old system.

---

### Post by Syntax. on 2009-04-16
Thanks everyone. Is there a command to get a list of installed packages? I thought there was. 

aaronp

Yeah I agree, I have many that I don't need but it would be good to find out what I have installed and just to install some and chuck the rest.

Cheers

---

### Post by codeseer on 2009-04-16
> **Syntax. said:**
> Thanks everyone. Is there a command to get a list of installed packages? I thought there was. 

aaronp

Yeah I agree, I have many that I don't need but it would be good to find out what I have installed and just to install some and chuck the rest.

Cheers

```
dpkg --get-selections | grep -v deinstall > installed-packages

```

---

### Post by aaronp on 2009-04-16
i'm sure there would be a command but I don't know it.

However, I used to use sbackup for my backups and whenever it did a backup it would also create a file which had the full list of installed applications.

---

### Post by Syntax. on 2009-04-16
I'm trying to copy my /home folder to my memory stick but It's saying the folder .macromedia cannot be handled because you don't have permission to read it. Anyway to get around this?

Edit

I just stumbled upon rsync, will this back everything in home up if i used rsync -av /home /media/usb  

Thanks.

---

### Post by aaronp on 2009-04-16
> **Syntax. said:**
> I'm trying to copy my /home folder to my memory stick but It's saying the folder .macromedia cannot be handled because you don't have permission to read it. Anyway to get around this?

Edit

I just stumbled upon rsync, will this back everything in home up if i used rsync -av /home /media/usb  

Thanks.

Yes that should work but I don't think rsync can copy files you don't have permissions to read so you will still miss out on that other item. But rsync is the best way to catch 'everything' in my opinion.

If you are the owner of the .macromedia folder then you should able to fix the problem using:

```
chmod -r 622 ~/.macromedia
```

If you are not the owner and you can't sudo then you may not be able to do it because you owuld need to be sudo to change chown to yourself or chmod it so you can read it.

---

### Post by HOLOGRAPHICpizza on 2009-04-17
You could just forget about the .macromedia folder, it can't contain too many important settings.

---

### Post by Syntax. on 2009-04-17
> **codeseer said:**
> ```
dpkg --get-selections | grep -v deinstall > installed-packages

```


Where does that save it to? I couldn't find it.

---

### Post by HOLOGRAPHICpizza on 2009-04-17
It would save to the file "installed-packages" in the current directory.

---

### Post by Syntax. on 2009-04-17
> **HOLOGRAPHICpizza said:**
> It would save to the file "installed-packages" in the current directory.


Thanks, Found it :)

Looks like I'm just about ready to reinstall.

---

### Post by HOLOGRAPHICpizza on 2009-04-17
> **Syntax. said:**
> Looks like I'm just about ready to reinstall.

Have fun! :D

---

### Post by aaronp on 2009-04-17
> **Syntax. said:**
> Thanks, Found it :)

Looks like I'm just about ready to reinstall.

Good luck...just been through it myself recently! 
At least Ubuntu only takes a few minutes to isntall itself before you can start configuring etc. (as opposed to certain other OSes that take hours just to extract themselves!)

---

### Post by Syntax. on 2009-04-17
Thanks :)

I just put the .mozilla folder into my user directory and it worked straight away no problems at all, Sweet!

Now I've got to copy some stuff back, get my programs back :D

Thanks for all the help.

---

