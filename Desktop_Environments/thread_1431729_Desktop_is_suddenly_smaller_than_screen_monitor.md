---
title: "Desktop is suddenly smaller than screen monitor"
date: 2010-03-17
forum: Desktop Environments
---

### Post by cbecker78 on 2010-03-17
After installing some themes, my desktop space no longer stretches all the way across the monitor.   The top and bottom task bars do, but not the desktop area.  And it's not just the wallpaper, windows will not extend beyond the end of the walpapered desktop area (see screen shot: look at lined black/grey area at right of screen).  Also, changing themes back to human/etc. does not fix the issue.  Please help???


Backstory if info needed:

I was trying to download/install the theme set from [bisisgi]("http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html") and ran into an error (among others) saying I had to do ```
sudo dpkg --configure -a
``` before I could proceed.  running that command brought up a looped dialoge asking me to pick my bisigi screen resolution from two types and there was no way to download other programs or such.  Following what I found on this forum to correct that, i did

```

sudo dpkg --purge --force all linux-headers-2.6.31-20
sudo apt-get install linux-headers-2.6.31-20
```and then 
```
sudo aptitude install zgegblog-themes
``` to install the themes.  It was then I noticed I had this problem...:frown:

thanks for any help!

---

### Post by cbecker78 on 2010-03-17
Holy good grief.  I am truly the most incompetent noob in existence.  7 hours of trying everything... endless forum and google searches. happened to right-cick on the area that was inaccessible... and noticed this little option: "delete panel".  It was a freaking panel that got added somehow.

My most humble appologies to anyone that bothered viewing this post.  

](*,)

---

