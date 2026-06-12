---
title: "How to snatch games from www.freeonlinegames.com"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by bamesah on 2007-06-17
I want to snatch DirtBike 3 from [www.freeonlinegames.com](www.freeonlinegames.com) so i can play it from my laptop with no need for Internet

I used to do that with Internet Download Manger's Grabber in Windows, but in Linux
How do i do it??

---

### Post by peedeeramone on 2007-06-17
i dont know if it will really help you but you could try some of the downloader tools in firefox

---

### Post by Cappy on 2007-06-17
Like peed said, You can probably find a firefox addon that looks for flash on a page and downloads it.
Or you can do it manually,
and search for "files.freeonlinegames.com" in the source and I came up with this:
[http://files.freeonlinegames.com/13681/games/dirtbike3/dirtbike3.swf](http://files.freeonlinegames.com/13681/games/dirtbike3/dirtbike3.swf)

and then you can ```
 wget http://files.freeonlinegames.com/13681/games/dirtbike3/dirtbike3.swf
```
to download it

---

### Post by hikaricore on 2007-06-17
You can also use gflashplayer (which is included in the flash 9 download from adobe) to play them without using your browser.  ^_^

---

### Post by ShadowFlar3 on 2007-06-17
If you're not comfortable with command line you can just find a link to www . something . com / something . swf, open it and when the game loads in Firefox you can just do File -> Save Page As and you can save it as something.swf and use a flash player or your browser to go to /home/username/something.swf (or wherever you chose to save it) and play without internet connection.

---

### Post by cocojambo2 on 2009-01-29
The best way to snatch games is to use Wget.exe... It's a small script that you plug in to your Run command Start -> Run in Windows XP. That's how I get games off this [Free games]("http://www.playonlinefreegames.net/") site.

---

### Post by eragon100 on 2009-01-29
> **cocojambo2 said:**
> The best way to snatch games is to use Wget.exe... It's a small script that you plug in to your Run command Start -> Run in Windows XP. That's how I get games off this [Free games]("http://www.playonlinefreegames.net/") site.

Wget isn't a script, it's a terminal download program and one of the GNU tools. It's included by default in ubuntu. :wink:

---

