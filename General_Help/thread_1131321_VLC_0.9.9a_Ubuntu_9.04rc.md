---
title: "VLC 0.9.9a Ubuntu 9.04rc?"
date: 2009-04-20
forum: General Help
---

### Post by favadi on 2009-04-20
I've installed Ubuntu 9.04rc. I very like it, but when I install VLC, it's so bad. When playing video, VLC has 2 windows. When I use Windows XP, video and controller are in 1 window, it's more beautiful. 
Anyone know how to fix this?

---

### Post by paradigm2 on 2009-04-20
[http://ubuntuforums.org/showthread.php?t=850053](http://ubuntuforums.org/showthread.php?t=850053)

---

### Post by favadi on 2009-04-20
> **paradigm2 said:**
> [http://ubuntuforums.org/showthread.php?t=850053](http://ubuntuforums.org/showthread.php?t=850053)

Tks. But it doesn't work for me. 
I used VLC normaly on ubuntu 8.10.

---

### Post by favadi on 2009-04-21
Need a solution, plz.

---

### Post by x33a on 2009-04-21
try preferences -> video -> general video settings, enable embedded video.

---

### Post by favadi on 2009-04-21
> **x33a said:**
> try preferences -> video -> general video settings, enable embedded video.

Thanks, but it's already checked. I try uncheck, check...but...:((

---

### Post by favadi on 2009-04-21
[[IMG]http://img509.imageshack.us/img509/6209/screenshotwkj.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshotwkj.png)

Screenshot.

---

### Post by TwiStEr55 on 2009-04-21
I have the exact same issue ... the checkbox for embedded video is checked and uncheck/check doesnt work ... it just wont embed

---

### Post by kruppe on 2009-04-21
> **TwiStEr55 said:**
> I have the exact same issue ... the checkbox for embedded video is checked and uncheck/check doesnt work ... it just wont embed

Exact same issue here. Funny how many annoyances showed up with Jaunty upgrade. Finally got my Amarok 1.4 reinstalled and working now I just need to fix this window.

---

### Post by hyperdude111 on 2009-04-21
Same problem here, my ubuntu 9.04 beta had it in 1 window but now i upgrade to rc it is in 2 windows.

---

### Post by LowSky on 2009-04-21
This issue will be "fixed" in the 1.0 release of VLC
[http://forum.videolan.org/viewtopic.php?f=13&t=58405](http://forum.videolan.org/viewtopic.php?f=13&t=58405)

---

### Post by kruppe on 2009-04-21
I think this might be a VLC bug.

I edited the ~/.config/vlc/vlcrc file on line 66.

Initially it is commented out.
If I uncomment it, save and restart VLC. VLC comments it again.

Interesting...

When chmod'ing the file to read only - VLC doesn't respond on the variable.

---

### Post by mc4man on 2009-04-21
The embedded has been disabled in the source since 0.9.4. In the crappy 0.9.5 version in 8.10 it was patched, then in 9.04 it was not patched. (both the 0.9.8a and 0.9.9a versions

Whether you'll ever see a 1.0 release in hardy, intrepid, and jaunty repo's is debatable. (maybe backports at some point

For any of those ubuntu versions atm you have 2 choices
Find a ppa for either 0.9.8a, 0.9.9a that has enabled the embedded, or 1.0pre  

build your own vlc and patch the source (1 line needs to be changed.

A post with some jaunty links and ppa search page
[http://ubuntuforums.org/showthread.php?p=7090561#post7090561](http://ubuntuforums.org/showthread.php?p=7090561#post7090561)

The thread itself includes some building tips and how to patch the source file.

Atm I think 0.9.9a is the best of the lot, use it in both hardy and intrepid

---

### Post by kruppe on 2009-04-21
Thanks. Might just look into it. :)

---

