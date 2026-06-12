---
title: "How do I install this?"
date: 2009-04-23
forum: General Help
---

### Post by Hellstudios on 2009-04-23
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)


I want to install this, I downloaded it, now it's just sitting on my desktop, how do I do this? So far the only applications I've installed have been through the repositories or terminal.


Help?


Thanks, Hellstudios.

---

### Post by zero777zero on 2009-04-23
download flash from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

select ".deb for Ubuntu 8.04+"

---

### Post by Hellstudios on 2009-04-23
No, Flash for linux is a Flash **Developer** Not a player.


Thanks though, Lol.

---

### Post by LoneWolfJack on 2009-04-23
first, you need to install CVS (should be in the repos). then you follow the instructions on that page.

I'm recommending against it though. there has to be some flash editor in the repos or as an ubuntu binary somewhere. or at least a clean source file, not a csv version.

you should be leaving installation from CSV to users who know what they're getting into. no offense.

---

### Post by codeseer on 2009-04-23
You'll need to acquire 'cvs' and then run the commands listed in the first grey block of that page. You might have to get extra dependencies, it should tell you though.

---

### Post by rhcm123 on 2009-04-23
> **Hellstudios said:**
> 
I want to install this, I downloaded it, now it's just sitting on my desktop, how do I do this? So far the only applications I've installed have been through the repositories or terminal.


alrighty, do the following (each line is a different command)
```

cd ~
cd ./Desktop
sudo apt-get install cvs
cvs -z9 -d:pserver:anonymous@f4l.cvs.sf.net:/cvsroot/f4l co f4l-0.2
cd ./f4l-0.2
sudo make

```
it should work after that (the executable will be in the directory on your desktop)

---

