---
title: "Azureus' voracious apetite."
date: 2006-09-29
forum: Desktop Environments
---

### Post by kpm on 2006-09-29
I have read about Azureus' voracious appetite for system resources before, but usually also read the odd post stating that Azureus was not that bad and that the problem was more in how it was configured (or lack there of).  Anyway, I gave it a try, read how to configure it properly and believe I have it working as optimally as it could on this laptop.  But, indeed it does drain my poor old laptop dry.  I have attached a couple of screen shots of my system monitor.  The peak is the moment I fire up Azureus.  The memory usage skyrockets up to over 70% right away, and then, if left on for a number of hours, gobbles up more and makes the computer unusable until Axureus is killed.
I am not sure if this correlation is significant, but as the default folder where torrents are stored has grown, Azureus has gotten worse and worse, even though there is only ever two of those torrents being accessed at any one time.
Does anyone have any more insight as to what is happening with Azureus here?  Can it be 'fixed' or is it naturally a gluten??
Thanks

---

### Post by grte on 2006-09-29
Sorry, but it's a glutton.  There's only so much optimizing you're going to be able to do.

---

### Post by kpm on 2006-09-30
Ahh well, anyway I just read about 'btdwonloadcurses' So will open up a terminal and type 'man bittorent' and figure out that method.

---

### Post by grte on 2006-09-30
> **kpm said:**
> Ahh well, anyway I just read about 'btdwonloadcurses' So will open up a terminal and type 'man bittorent' and figure out that method.

If you wanna try a command-line torrent program, give rtorrent a try.  Once you configure it and learn a couple of keyboard short-cuts, It's really effective.

[edit] Oh yeah, the version in the repos is really old.  If you do want to give it a try, you might wanna try the newer debs in [this]("http://www.ubuntuforums.org/showthread.php?p=1546863#post1546863") thread.

---

### Post by kpm on 2006-09-30
> **grte said:**
> If you wanna try a command-line torrent program, give rtorrent a try.  Once you configure it and learn a couple of keyboard short-cuts, It's really effective.
Thanks for the info! I will give it a go.

---

### Post by orb9220 on 2006-09-30
Also utorrent under wine runs well. And is not a oink!,Oink!

---

### Post by infol on 2006-09-30
Don't know how much ram you have, but on my laptop (w/ 512Mb) Azureus is never the top 'consumer' of ram (which is Xgl), but does use it's fair amount - around 13% on az startup - and then goes down to about 1-3%.
Are you using open source Java or Sun's proprietary Java(jre-1.5.0)?

---

