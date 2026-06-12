---
title: "SimplyMepis 7 released"
date: 2007-12-23
forum: Debian
---

### Post by angryfirelord on 2007-12-23
[http://www.mepis.org/node/14187]("http://www.mepis.org/node/14187")
> Morgantown, WV, Dec 22, 2007 -- MEPIS has released SimplyMEPIS 7.0. The isos for the 32 and 64 versions are in the released directory at the MEPIS subscriber site and public mirrors. MEPIS 7.0 offers up to date user applications delivered on top of a Debian stable core.

Some of the important packages included with the 7.0 release are: an updated and security patched 2.6.22.14 kernel, Xorg 7.1.0, KDE 3.5.8, OpenOffice 2.3.0, Firefox 2.0.0.11, Thunderbird 2.0.0.6, Digikam 0.9.2, Sun Java 6.00, Amarok 1.4.7, mplayer 1.0.rc1, fuse driver 2.7.0, ntfs-3g 1.710, madwifi-ng Atheros driver 0.9.3.2, wpa-supplicant 0.6.0, ALSA sound drivers 1.0.15, libglib2.0 2.14.0, libgtk2.0 2.10.13, and QT 4.3.1-1.

Some of the additional packages in the MEPIS 7.0 pool include: acroread 7.0.9-0, icaclient 10.6-1, evolution 2.10.3, NVIDIA driver 100.14.19-1, NVIDIA legacy drivers 1.0.9639 and 1.0.7185, AMD fglrx driver 8.43.2-1, libgnome2 2.18.0, compiz 0.6.3, and compiz-fusion 0.6.0.

This release contains a new desktop theme and a detailed user manual, both developed and contributed by the MEPIS community.
Sounds interesting, gonna give it another whirl.

---

### Post by Amorphous_Snake on 2007-12-24
I tried it. It looks good. But on my main PC, the mouse pointer is invisible!!! This doesn't happen on my old PC.

Any ideas?

---

### Post by Antman on 2007-12-24
Hmmm... there has always been a soft spot in me for Mepis. Since it's based on Debian again, I may give it a whirl.

---

### Post by angryfirelord on 2007-12-24
Hmm, seems the mepis repos are a bit busy:
```
Get:1 http://security.debian.org stable/updates Release.gpg [189B]
Hit http://security.debian.org stable/updates Release
Ign http://security.debian.org stable/updates/main Packages/DiffIndex
Ign http://security.debian.org stable/updates/contrib Packages/DiffIndex
Ign http://security.debian.org stable/updates/non-free Packages/DiffIndex
Err ftp://ftp.mepis.com mepis-7.0 Release.gpg
  PASS failed, server said: Sorry, the maximum number of allowed clients (10) are already connected.
Get:2 http://ftp.debian.org stable Release.gpg [378B]
Get:3 http://volatile.debian.org etch/volatile Release.gpg [189B]
Hit http://security.debian.org stable/updates/main Packages
Hit http://security.debian.org stable/updates/contrib Packages
Hit http://security.debian.org stable/updates/non-free Packages
Hit http://ftp.debian.org stable Release
Hit http://volatile.debian.org etch/volatile Release
Ign http://ftp.debian.org stable/main Packages/DiffIndex
Ign http://ftp.debian.org stable/contrib Packages/DiffIndex
Ign http://ftp.debian.org stable/non-free Packages/DiffIndex
Ign http://volatile.debian.org etch/volatile/main Packages/DiffIndex
Ign ftp://ftp.mepis.com mepis-7.0 Release
Hit http://ftp.debian.org stable/main Packages
Hit http://ftp.debian.org stable/contrib Packages
Ign http://volatile.debian.org etch/volatile/contrib Packages/DiffIndex
Ign http://volatile.debian.org etch/volatile/non-free Packages/DiffIndex
Hit http://ftp.debian.org stable/non-free Packages
Hit http://volatile.debian.org etch/volatile/main Packages
Hit http://volatile.debian.org etch/volatile/contrib Packages
Get:4 ftp://ftp.mepis.com mepis-7.0/main Packages/DiffIndex
Hit http://volatile.debian.org etch/volatile/non-free Packages
Ign ftp://ftp.mepis.com mepis-7.0/main Packages/DiffIndex
Get:5 ftp://ftp.mepis.com mepis-7.0/main Packages
Ign ftp://ftp.mepis.com mepis-7.0/main Packages
Hit ftp://ftp.mepis.com mepis-7.0/main Packages
Fetched 3B in 1s (2B/s)
Failed to fetch ftp://ftp.mepis.com/mepis/dists/mepis-7.0/Release.gpg  PASS failed, server said: Sorry, the maximum number of allowed clients (10) are already connected.
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Does Warren have any other mepis repos available?

---

### Post by SunnyRabbiera on 2007-12-24
cool, I will give it a shot when I get more CD's to burn

---

### Post by angryfirelord on 2007-12-24
> **SunnyRabbiera said:**
> cool, I will give it a shot when I get more CD's to burn
hehe, I swear I've went through over 50 cds with my previous distro hopping. I'm getting better, but...it's tempting! (I just hope Comcast doesn't cut me off because of something stupid in their policy)

---

### Post by Antman on 2007-12-24
> **angryfirelord said:**
> hehe, I swear I've went through over 50 cds with my previous distro hopping. I'm getting better, but...it's tempting! (I just hope Comcast doesn't cut me off because of something stupid in their policy)

It's been a little while since I have burnt a distro CD (OpenSuse 10.3 was the last one). But, I have pretty much settled on Sidux as my main OS with XP/vista as secondary. I will probably download the Mepis 7 CD just to play.

---

### Post by Amorphous_Snake on 2007-12-24
I solved my mouse problem by loading the VESA driver.

---

### Post by Bandicoot on 2007-12-24
I've been looking on the mepis website and it all sounds very promising. I am tempted to try it, although KDE just isn't my cup of tea .. so I am stil a bit hesistant to try.

---

### Post by SunnyRabbiera on 2007-12-24
> **Bandicoot said:**
> I've been looking on the mepis website and it all sounds very promising. I am tempted to try it, although KDE just isn't my cup of tea .. so I am stil a bit hesistant to try.

Yeh but the KDE in mepis is usually very good

---

### Post by 67GTA on 2007-12-24
> **angryfirelord said:**
> Hmm, seems the mepis repos are a bit busy:
```
Get:1 http://security.debian.org stable/updates Release.gpg [189B]
Hit http://security.debian.org stable/updates Release
Ign http://security.debian.org stable/updates/main Packages/DiffIndex
Ign http://security.debian.org stable/updates/contrib Packages/DiffIndex
Ign http://security.debian.org stable/updates/non-free Packages/DiffIndex
Err ftp://ftp.mepis.com mepis-7.0 Release.gpg
  PASS failed, server said: Sorry, the maximum number of allowed clients (10) are already connected.
Get:2 http://ftp.debian.org stable Release.gpg [378B]
Get:3 http://volatile.debian.org etch/volatile Release.gpg [189B]
Hit http://security.debian.org stable/updates/main Packages
Hit http://security.debian.org stable/updates/contrib Packages
Hit http://security.debian.org stable/updates/non-free Packages
Hit http://ftp.debian.org stable Release
Hit http://volatile.debian.org etch/volatile Release
Ign http://ftp.debian.org stable/main Packages/DiffIndex
Ign http://ftp.debian.org stable/contrib Packages/DiffIndex
Ign http://ftp.debian.org stable/non-free Packages/DiffIndex
Ign http://volatile.debian.org etch/volatile/main Packages/DiffIndex
Ign ftp://ftp.mepis.com mepis-7.0 Release
Hit http://ftp.debian.org stable/main Packages
Hit http://ftp.debian.org stable/contrib Packages
Ign http://volatile.debian.org etch/volatile/contrib Packages/DiffIndex
Ign http://volatile.debian.org etch/volatile/non-free Packages/DiffIndex
Hit http://ftp.debian.org stable/non-free Packages
Hit http://volatile.debian.org etch/volatile/main Packages
Hit http://volatile.debian.org etch/volatile/contrib Packages
Get:4 ftp://ftp.mepis.com mepis-7.0/main Packages/DiffIndex
Hit http://volatile.debian.org etch/volatile/non-free Packages
Ign ftp://ftp.mepis.com mepis-7.0/main Packages/DiffIndex
Get:5 ftp://ftp.mepis.com mepis-7.0/main Packages
Ign ftp://ftp.mepis.com mepis-7.0/main Packages
Hit ftp://ftp.mepis.com mepis-7.0/main Packages
Fetched 3B in 1s (2B/s)
Failed to fetch ftp://ftp.mepis.com/mepis/dists/mepis-7.0/Release.gpg  PASS failed, server said: Sorry, the maximum number of allowed clients (10) are already connected.
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Does Warren have any other mepis repos available?

This happens a lot. There are 10 people allowed to connect to the Mepis server at a time. It will be a couple of weeks before you can get much out of it. It always agrivated me because there was only one main server.

---

### Post by angryfirelord on 2007-12-24
> **Bandicoot said:**
> I've been looking on the mepis website and it all sounds very promising. I am tempted to try it, although KDE just isn't my cup of tea .. so I am stil a bit hesistant to try.
The MEPIS team does a wonderful job of polishing KDE, so don't let that get in the way. Here's some default screenshots:

[http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution=SimplyMEPIS%207.0]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution=SimplyMEPIS%207.0")

If you still hate it, you can always install gnome and gdm and uninstall kde and kdm.
> This happens a lot. There are 10 people allowed to connect to the Mepis server at a time. It will be a couple of weeks before you can get much out of it. It always agrivated me because there was only one main server.
Ok, so it's not just me. Hopefully someone will mention that in mepislovers.

---

### Post by 67GTA on 2007-12-24
It has been mentioned several times, but it is Warren's distro, and Warren's server. Unless Warren decides to let the community set up some mirrors, it will stay that way. This is just one of the several little reasons I stopped using Mepis. It is an awesome distro that suffers from no community participation. This is supposed to change now that 7 is final. The most obvious is the artwork. Maybe now with more community influence, Mepis will climb back up.

---

### Post by Bandicoot on 2007-12-25
:( that doesn'tsound very good. If I read the above correctly you're lucky if you can reach the repo's ? So if I wanted to download some packages or if there are updates available it can very well be thatI have to sit and wait until I am lucky enough to get a connection ?

Maybe I am reading it wrong .. but if I read it correctly that would be a  reason to not even start with Mepis.

---

### Post by Amorphous_Snake on 2007-12-25
Actually, I wanted to replace openSUSE 10.3 on my PC with another distro. Mint 4.0 was the perfect candidate, but I waited till Mepis 7 was released, just to try something that isn't Ubuntu! I haven't tried Mepis since 6.0.

If what you guys say is correct about the repos, then I will wait a few days before installing it. If I don't like it, then I am all sold to Mint!

---

### Post by Antman on 2007-12-25
> **67GTA said:**
> The most obvious is the artwork. Maybe now with more community influence, Mepis will climb back up.

I was looking at the screen shots of Mepis7 and it looks the surface looks the same as 6 and 6.5. Of course the apps and kernel are updated; and debian etch is the core now instead of *buntu, but hopefully the community steps in and donates some themes and icons. :-k

Also, I think I will pass on trying Mepis 7 I think. I'm not to keen on trying new flavors of linux every 2 weeks anymore. ;)
The next distro I will probably try is OpenSuse 11. Until then I'll stick with Sidux.

---

### Post by angryfirelord on 2007-12-25
> **Bandicoot said:**
> :( that doesn'tsound very good. If I read the above correctly you're lucky if you can reach the repo's ? So if I wanted to download some packages or if there are updates available it can very well be thatI have to sit and wait until I am lucky enough to get a connection ?

Maybe I am reading it wrong .. but if I read it correctly that would be a  reason to not even start with Mepis.
It's not really that bad because Mepis's user base isn't as large as Ubuntu's is. I've been able to connect successfully now, so I think that issue was just the "distrowatch rush".

Plus, your security updates comes from security.debian.org, so you won't have any vulnerable packages should the mepis server be unavailable.
> I was looking at the screen shots of Mepis7 and it looks the surface looks the same as 6 and 6.5. Of course the apps and kernel are updated; and debian etch is the core now instead of *buntu, but hopefully the community steps in and donates some themes and icons.
If you look at the final release screenshots, the theme has been updated to a much better look. Icons are still the same, but I like those over the default KDE ones. :)

---

### Post by Amorphous_Snake on 2007-12-26
Anybody saw a review anywhere?

---

### Post by markharding557 on 2007-12-26
> **Amorphous_Snake said:**
> Actually, I wanted to replace openSUSE 10.3 on my PC with another distro. Mint 4.0 was the perfect candidate, but I waited till Mepis 7 was released, just to try something that isn't Ubuntu! I haven't tried Mepis since 6.0.

If what you guys say is correct about the repos, then I will wait a few days before installing it. If I don't like it, then I am all sold to Mint!

a easy way of testing distros without touching anything on your pc is to use virtualbox or other virtual program,then you can look at as many as you want untill you find one to install for real.
i find this saves alot of work

---

