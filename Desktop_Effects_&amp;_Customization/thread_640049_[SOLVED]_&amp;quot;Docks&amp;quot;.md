---
title: "[SOLVED] &amp;quot;Docks&amp;quot;"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by Techwiz on 2007-12-13
I have noticed that a few users have replaced one or all of their panels with "docks" like the mac's (or similar). How do I do that? I am completely new to this, so could you please explain it pretty simply?
Thank you.

---

### Post by SunnyRabbiera on 2007-12-13
well there are several docks available for linux, the main one featured I have seen is avant window manager.
Personally I prefer kooldock as you dont need compositing to use it

---

### Post by LaRoza on 2007-12-13
AWN is nice.

[http://wiki.awn-project.org/index.php?title=Installation](http://wiki.awn-project.org/index.php?title=Installation)

---

### Post by K.Mandla on 2007-12-13
Moved to Desktop Effects & Customization.

---

### Post by Techwiz on 2007-12-13
Could you each explain to me in very basic terms how I should go about installing either of these docks?
Thanks!

---

### Post by SunnyRabbiera on 2007-12-13
well installing awn is simple, but you have to search around for it here as there are many topics on the matter.

---

### Post by Dark Hornet on 2007-12-13
I use AWN Curves, and I love it.  I have been following this thread for a while now, and it has helped me out a ton!

[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

Good Luck!
:guitar:

---

### Post by LaRoza on 2007-12-13
> **Techwiz said:**
> Could you each explain to me in very basic terms how I should go about installing either of these docks?
Thanks!

For AWN in Gutsy:

0. Run this command
```

gksudo gedit /etc/apt/sources.list

```

1. Add these to the end:

```

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

Save and exit.

2. Run these in the terminal:

```

wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

```

3. Run this command:

```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

```

---

### Post by Techwiz on 2007-12-13
Ok, I've got the AWN manager under my System>Preferences menu. But when i click on it, it doesn't start. Any ideas?

---

### Post by Dark Hornet on 2007-12-13
add it to your start up menu, then restart X by hitting "ctrl, alt, backspace".

---

### Post by LaRoza on 2007-12-14
> **Techwiz said:**
> Ok, I've got the AWN manager under my System>Preferences menu. But when i click on it, it doesn't start. Any ideas?

You have to start AWN, Applications->Accessories

---

### Post by Techwiz on 2007-12-14
Ok, the AWN dock is working, thank you all!

---

### Post by nae5 on 2007-12-14
I got this on the last step.  Any ideas? Are those unmet dependancies simply packages i need to install?

```
naes@naestwo:~$ gksudo gedit /etc/apt/sources.list
naes@naestwo:~$ wget http://download.tuxfamily.org/syzygy42/reacocard.asc
--16:25:55--  http://download.tuxfamily.org/syzygy42/reacocard.asc
           => `reacocard.asc'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [application/octet-stream]

100%[====================================>] 1,682         --.--K/s             

16:25:56 (54.60 MB/s) - `reacocard.asc' saved [1682/1682]

naes@naestwo:~$ sudo apt-key add reacocard.asc
OK
naes@naestwo:~$ rm reacocard.asc
naes@naestwo:~$ sudo apt-get update
Get:1 http://download.tuxfamily.org gutsy Release.gpg [189B]
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Get:3 http://download.tuxfamily.org gutsy Release [10.9kB]
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy/main Packages
Get:4 http://download.tuxfamily.org gutsy/avant-window-navigator Packages [1952B]
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/universe Sources                
Hit http://archive.ubuntu.com gutsy/main Sources                    
Hit http://archive.ubuntu.com gutsy/multiverse Sources              
Hit http://archive.ubuntu.com gutsy/restricted Sources              
Get:5 http://download.tuxfamily.org gutsy/avant-window-navigator Sources [673B]
Fetched 13.7kB in 1s (8844B/s)                
Reading package lists... Done
naes@naestwo:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages
naes@naestwo:~$ 
```

---

