---
title: "C64 games"
date: 2009-05-13
forum: Gaming &amp; Leisure
---

### Post by UncleMonty on 2009-05-13
How can I run C64 games in Ubuntu? I have emulators but they only run in windows.

---

### Post by u235sentinel on 2009-05-13
> **UncleMonty said:**
> How can I run C64 games in Ubuntu? I have emulators but they only run in windows.

I've used vice in Ubuntu.  Works ok.  Not my favorite but it does work and it works very well.  Not my fav because I'm not as familiar with it I'm guessing :D

---

### Post by UncleMonty on 2009-05-13
> **u235sentinel said:**
> I've used vice in Ubuntu.  Works ok.  Not my favorite but it does work and it works very well.  Not my fav because I'm not as familiar with it I'm guessing :D

How? In WINE?

---

### Post by u235sentinel on 2009-05-13
> **UncleMonty said:**
> How? In WINE?

No.  There is a native vice package available.

type 

sudo apt-get install vice 

and it will install it for you.

I haven't used it seriously but I know it works.  Glad I kept my old C64 games.  I was going to chuck them out years ago until I stumbled across vice and frodo (frodo I think ONLY works in windows).  Vice will work natively in both Windows and Linux.

---

### Post by UncleMonty on 2009-05-13
> **u235sentinel said:**
> No.  There is a native vice package available.

type 

sudo apt-get install vice 

and it will install it for you.

I haven't used it seriously but I know it works.  Glad I kept my old C64 games.  I was going to chuck them out years ago until I stumbled across vice and frodo (frodo I think ONLY works in windows).  Vice will work natively in both Windows and Linux.

Thanks have installed it now - where should I be able to locate it? Accessories?

---

### Post by u235sentinel on 2009-05-13
> **UncleMonty said:**
> Thanks have installed it now - where should I be able to locate it? Accessories?

I don't recall.  Not in front of my home computer at the moment.  You should have it located in /usr/bin/however.

Try this.  Run dpkg -L vice  

You should see a list of everything that package installed.  I see I have a few things including the following

/usr/bin/vsid
/usr/bin/x64
/usr/bin/x128
/usr/bin/xvic
/usr/bin/xpet
/usr/bin/xplus4
/usr/bin/xcbm2
/usr/bin/c1541
/usr/bin/petcat

x64 is what I typically run.  I'm not sure if there is an icon however for the launcher.  Never used one myself :D

---

### Post by UncleMonty on 2009-05-14
> **u235sentinel said:**
> I don't recall.  Not in front of my home computer at the moment.  You should have it located in /usr/bin/however.

Try this.  Run dpkg -L vice  

You should see a list of everything that package installed.  I see I have a few things including the following

/usr/bin/vsid
/usr/bin/x64
/usr/bin/x128
/usr/bin/xvic
/usr/bin/xpet
/usr/bin/xplus4
/usr/bin/xcbm2
/usr/bin/c1541
/usr/bin/petcat

x64 is what I typically run.  I'm not sure if there is an icon however for the launcher.  Never used one myself :D

I entered "Run dpkg -L vice" and it said "command not found" - is that exactly how I should enter it?

---

### Post by FsFrey on 2009-05-14
Drop the Run....

In the terminal type dpkg -L vice.

---

### Post by UncleMonty on 2009-05-14
> **FsFrey said:**
> Drop the Run....

In the terminal type dpkg -L vice.

It runs! 

Thanks :)

---

### Post by u235sentinel on 2009-05-14
> **FsFrey said:**
> Drop the Run....

In the terminal type dpkg -L vice.

Rofl... My bad.  Sorry about that :D

It's the way I type.

---

### Post by UncleMonty on 2009-05-14
> **u235sentinel said:**
> Rofl... My bad.  Sorry about that :D

It's the way I type.


No probs. Is there anyway of making it full screen or at least bigger btw as it's just a tiny square at the moment?

---

### Post by u235sentinel on 2009-05-15
> **UncleMonty said:**
> No probs. Is there anyway of making it full screen or at least bigger btw as it's just a tiny square at the moment?

I believe there was an option to double the video somewhere.  I had to poke around though to find it.

[http://viceteam.org/vice_6.html#SEC46](http://viceteam.org/vice_6.html#SEC46)

Maybe this will help :D

---

### Post by UncleMonty on 2009-06-01
> **u235sentinel said:**
> I believe there was an option to double the video somewhere.  I had to poke around though to find it.

[http://viceteam.org/vice_6.html#SEC46](http://viceteam.org/vice_6.html#SEC46)

Maybe this will help :D

yo what ubuntu version are you using? I just updated to Jaunty and can't get vice to run anymore. :(

---

### Post by Grishka on 2009-06-01
> **UncleMonty said:**
> yo what ubuntu version are you using? I just updated to Jaunty and can't get vice to run anymore. :(

[lookie.](http://ubuntuforums.org/showthread.php?t=1135058)

---

