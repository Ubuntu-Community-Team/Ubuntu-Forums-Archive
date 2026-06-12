---
title: "Configuring Clam AV"
date: 2005-12-07
forum: General Help
---

### Post by autonomy on 2005-12-07
I followed the instructions, [here]("http://www.hula-project.org/ClamAV_Ubuntu#Configuring_ClamAV"), but got this result, "bash: /etc/init.d/clamav-daemon: No such file or directory"

---

### Post by Appolusionist on 2005-12-08
[quote=autonomy]I followed the instructions, [here]("http://www.hula-project.org/ClamAV_Ubuntu#Configuring_ClamAV"), but got this result, "bash: /etc/init.d/clamav-daemon: No such file or directory"[/quote]
 
The install steps there are for Hoary 5.04 and it appears you are using Breezy 5.10. The install guide you followed had you edit your sources.list to include Hoary. I followed this [guide]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-anti-virus") and it worked perfectly.

---

### Post by autonomy on 2005-12-08
Oh thanks. Is there anything I should do to exclude Hoary?
I tried to set up automatic scans, but the last step was weird; and I couldn't make anything happen (including saving it) The whole terminal looked backwards, and I don't know if I was supposed to enter a certain time, date, et cetera or leave the zeros and the asteriks.

---

### Post by Appolusionist on 2005-12-08
[quote=autonomy]Oh thanks. Is there anything I should do to exclude Hoary?
I tried to set up automatic scans, but the last step was weird; and I couldn't make anything happen (including saving it) The whole terminal looked backwards, and I don't know if I was supposed to enter a certain time, date, et cetera or leave the zeros and the asteriks.[/quote]

I personally have not had a problem using this [sources.list]("http://www.psychocats.net/linux/sources.php"). You can always post what you currently have here also.

---

### Post by autonomy on 2005-12-08
I admit, I'm a novice at this, which is over my head, but I appreciate your help. Here's my source list:```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by Appolusionist on 2005-12-08
[quote=autonomy]I admit, I'm a novice at this, which is over my head, but I appreciate your help. Here's my source list:```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```[/quote] 
No problem...glad to try to help. Your sources looks pretty good, but go ahead and replace the one you have with the one I referred to earlier and also add the following line. It will give you access to the additional backports/extras which are the software packages that weren't ready at the time when Breezy 5.10 was released. 

```
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

---

### Post by autonomy on 2005-12-08
Do I need your source list to [automatically scan files/folders for                             viruses]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2518329")? That's all I'm trying to do. I think I especially need help with *this* step, "00 00 * * * sudo clamscan -r /location_of_files_or_folders". the zeros and the asteriks are supposed to be the times when I want to scan, but I want it to periodically scan. I want it to scan my whole computer, but I'm not sure how to put that where it says, "location_of_files_or_folders".

---

### Post by braynyac on 2005-12-09
Autonomy...

The guide says:

```
The format “* * * * *” below refers to: minute hour date month year

Append the following line at the end of file

00 00 * * * sudo clamscan -r /location_of_files_or_folders
```

Which basically means: run command 'sudo clamscan -r /location_of_files_or_folders' at minute 00 of hour 00 every day ( 00 00 * * *)

In order for it to scan the files you want - let's say your home directory (/home/username) periodically (say, every 4 hours), you would want to modify as such:

```
00 */4 * * * sudo clamscan -r /home/username

```
The -r option of clamscan scans all folders recursively (travels down the directory tree into ALL subdirectories of the specified starting point).  Setting the SECOND option to */4 runs the command every 4 hours, starting at the minute 00.  

To scan the whole computer, just change ```
00 00 * * * sudo clamscan -r /location_of_files_or_folders
``` to ```
00 */4 * * * sudo clamscan -r /
```

Also, see man 5 crontab for more information about how to set up the times for it to run, and the different options available.

Let me know if this helps,

~braynyac

---

### Post by autonomy on 2005-12-09
Yes, that helps indeed. Thanks. Where's man 5 crontab? I think every four hours is too often. Once a week should be plenty, but if I'm not using my computer when it's scheduled to run, then it won't run, next time I'm using my computer.

---

### Post by Appolusionist on 2005-12-09
[quote=autonomy]Yes, that helps indeed. Thanks. Where's man 5 crontab? I think every four hours is too often. Once a week should be plenty, but if I'm not using my computer when it's scheduled to run, then it won't run, next time I'm using my computer.[/quote]
 
Just run 
 
> man 5 crontab
 
from a terminal

---

### Post by autonomy on 2005-12-09
I think the second step,```
export EDITOR=vim &&
sudo crontab -e
```is messing up me because it says, "There's no cron tab for root - using only [. . .]", and then, it switches to this screen (I *would* show you a picture of the screen, but I can't capture the screen and paste it in GIMP Image Editor like I used to in Winders with something besides GIMP. In fact, I can't even copy the text from the terminal and paste it in here!):```

~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
"/tmp/crontab.4bZYOm/crontab" 0L, 0C                          0, 0-1         All
```Entering text just makes beeping noises, and pressing "Enter" does nothing.

---

### Post by braynyac on 2005-12-09
heheh....that's vi (or vim) - and they are a bit finicky to learn.  Best bet is to make sure you have nano installed (I think it's installed by default in Breezy), and change this line in the config:

```
export EDITOR=vim &&
```

to

```
export EDITOR=nano &&
```

That should get you a nice, easy editor =).  Also, what user are you trying to do this as?  You should be running the crontab as your user, without the sudo part...at least, that's how mine is set up (since you use sudo when calling clamscan in the crontab).  So, new commands should look like this:

```
export EDITOR=nano &&
crontab -e
```

Give that a try and let me know how it goes!

~braynyac

---

### Post by autonomy on 2005-12-09
OK, I just can't figure out how to save it. By the way, here's the line```
0 0 1 * * sudo clamscan -r /
```That means that it will check, once a month.

---

### Post by braynyac on 2005-12-09
ctrl x (to exit)
Press y (to save)

That should be it =)

~braynyac

---

### Post by autonomy on 2005-12-09
Wait, why is this file in my temporary directory? I think it said I didn't have that file either and that it just generated this crontab in my temporary folder.

---

### Post by braynyac on 2005-12-09
The crontab is initially created in a temp folder, but once you exit (and save on exit), it will install it to the correct location.

~braynyac

---

### Post by autonomy on 2005-12-09
Can I find it and make sure that line is in there?

---

### Post by braynyac on 2005-12-09
All you have to do is re-run:

crontab -e

If it is there, it will show up.  Otherwise recreate, exit, and save.

~braynyac

---

