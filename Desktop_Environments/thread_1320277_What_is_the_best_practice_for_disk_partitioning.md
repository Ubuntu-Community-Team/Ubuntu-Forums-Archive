---
title: "What is the best practice for disk partitioning?"
date: 2009-11-09
forum: Desktop Environments
---

### Post by bullka on 2009-11-09
I have already read some other forums. Seems that the best practice is...

"/" - 20-25GB. This should be enough for most of the Desktop installations.

"/home" - 30GB. This is for perdonal settings, my documents and firefoc downloads , Desktop!! (some people store many files on desktop) etc. Maybe this is too much if no data is stored in Home (just settings)

"/data1"
"/data2"
"/dataX"
All the rest /data* would be for movies, photos, music, installations etc.

Is this the right partitioning for Desktop distrubution and home computer??
Do we need to dedicate a partition for /usr, /usr/local?

---

### Post by _khAttAm_ on 2009-11-09
I don't know if it is a very good idea but the way I have done is:
/ - 30GB
/home  - Rest of the drive (200GB)

---

### Post by aquavitae on 2009-11-09
I prefer not splitting up my data any more than necessary since it usually leads to wasted space.  But I have seen arguments that you should have a separate small (i.e. 32M) partition for /boot.  I'm kinda undecided myself though.

---

### Post by bullka on 2009-11-09
> **_khAttAm_ said:**
> I don't know if it is a very good idea but the way I have done is:
/ - 30GB
/home  - Rest of the drive (200GB)

I see that if you would be a Windows user you would store all your data in My Documents? Correct? Coz /home in Linux is equal to C:\Documents and Settings\%User%

I don't think this is a good idea. I want all my data outside the Home. And maybe links on my Desktop (or in Home) to those file systems (like Movies, Mp3...)

---

### Post by aquavitae on 2009-11-09
That's the setup I have.  I have a documents partition which I mount to ~/Documents, so all my files are accessible through home, but are actually stored on another partition, separate from the user settings.  You could mount it anywhere though or use links as you say. The advantage of this is that it is easy to reinstall without worrying about losing data. Or in my case, try out a new distro!

---

