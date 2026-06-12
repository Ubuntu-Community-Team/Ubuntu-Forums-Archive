---
title: "can't update reps or install programs!"
date: 2006-07-21
forum: Desktop Environments
---

### Post by junglistmaster on 2006-07-21
help my brain hurts! i have spent hours on this forum trying to find a way to download packages such as skype and vlc player so i can do anything but surf. i first had problems with firefox but then removed the ivp6 thing and it works like a dream. but i cant get it to connect to the update servers,it just has this output when i try
:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

and looks like this [ATTACH]13052[/ATTACH]
i have noticed many other people with similar issues over past year but no clear solution, surely there is one like the issue with ivp6 and firefox. I DONT WANT TO RETURN TO WINDOWS WITH MY TALE BETWEEN MY LEGS...

---

### Post by kingmonkey on 2006-07-21
try typing in the terminal

sudo apt-get update 
sudo apt-get upgrade

Post any error messages here.

---

### Post by halfvolle melk on 2006-07-21
What kingmonkey said, but close Synaptic first.

---

### Post by junglistmaster on 2006-07-21
thanks for replying, 
~$ sudo apt-get update
Err [http://nightlies.videolan.org](http://nightlies.videolan.org) ./ Release.gpg
  Could not connect to nightlies.videolan.org:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg
  Could not connect to download.skype.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntu.com (1.0.0.0)]
is what i see as output....

---

### Post by junglistmaster on 2006-07-21
i dont think i have synaptic open as i am doing it through a terminal not the syn package manager or 'add and remove programs'

---

### Post by junglistmaster on 2006-07-21
then this appeared. is it a dns server issue? i am using an ethernet cable direct connection not wireless.

~$ sudo apt-get update
Err [http://nightlies.videolan.org](http://nightlies.videolan.org) ./ Release.gpg
  Could not connect to nightlies.videolan.org:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg
  Could not connect to download.skype.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Could not connect to download.skype.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://nightlies.videolan.org/build/exp-i386/arch/./Release.gpg](http://nightlies.videolan.org/build/exp-i386/arch/./Release.gpg)  Could not connect to nightlies.videolan.org:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by halfvolle melk on 2006-07-21
> i dont think i have synaptic open as i am doing it through a terminal not the syn package manager or 'add and remove programs'
Ok, but these programs need to be closed or you'll get the "Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)".

> **junglistmaster said:**
> then this appeared. is it a dns server issue?
No, not if you can normally surf the web.

What does your /etc/apt/sources.list say? Find out with ```
cat /etc/apt/sources.list
```

---

### Post by junglistmaster on 2006-07-21
~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universedeb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
## Repository for Skype
deb-src [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted
# deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
deb [http://nightlies.videolan.org/build/exp-i386/arch](http://nightlies.videolan.org/build/exp-i386/arch) ./

i couldnt see synoptic open in the system monitor, unless it is called something else?

---

### Post by halfvolle melk on 2006-07-21
> i couldnt see synoptic open in the system monitor, unless it is called something else?
In the screenshot you provided, "Add/Remove programs" was open, that's why I mentioned it. If they're not on the taskbar it's ok.

Are you from Australia? If not I'd replace all instances of **au** with the appropriate letters in /etc/apt/sources.list. Or make a new one with
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Maybe it fixes the time-out.

As for Video Lan, I'd grab the one from the Ubuntu repositories. It's in universe.

---

### Post by junglistmaster on 2006-07-21
i am from australia, how do i find video lan or skype from the universe repositories? are they online too?

---

### Post by halfvolle melk on 2006-07-21
Ok. After first install I got the au repo's as well though I don't live anywhere near.

Enable Universe: gedit /etc/apt/sources.list and change
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe

into

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe

Save the file. Also see:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
Then run sudo apt-get update.

Install vlc: sudo apt-get install vlc.

I don't know about Skype, never tried that.

---

### Post by junglistmaster on 2006-07-21
i found skype for debian on the skype website, is it easy to install? also i think i have found video lan from [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)
can i install that easily too? 
sorry i am completely new to linux.only 24 hours in!

---

### Post by halfvolle melk on 2006-07-21
No worries :)
Here's a good thread on repositories:
[http://ubuntuforums.org/showthread.php?t=185758&highlight=recommended+repositories](http://ubuntuforums.org/showthread.php?t=185758&highlight=recommended+repositories)

At the bottom it says:
> ## skype (official)
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
Offcourse you'll need to remove the '#' before it works. Then the data base of packages needs to be updated:
```
sudo apt-get update[/quote]

Then, installing anything is as easy as
[code]sudo apt-get install vlc
```
or
```
sudo apt-get install thenameofaskypepackagethatimnotawareof
```

---

### Post by junglistmaster on 2006-07-21
thanks, that is a bit much for this late at night so maybe i will try it in the morn. ta again.

---

### Post by khedron on 2006-08-04
I think I am having a similar problem. I cannot reload the package information or install packages from either apt-get or synaptic. However, I can visit the sites in my sources.list with Firefox, and once I have done that, there is about a 5 minute window in which I can update, install etc as much as I like.

I reckon my problem is a DNS error. Can anyone help me with it?

---

