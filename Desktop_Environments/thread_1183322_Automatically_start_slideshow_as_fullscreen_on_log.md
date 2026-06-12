---
title: "Automatically start slideshow as fullscreen on login"
date: 2009-06-09
forum: Desktop Environments
---

### Post by SoftwareExplorer on 2009-06-09
Hi, I want to set up an Ubuntu computer to run a slide show that was made with Open Office.org Impress to run in a loop through out the day at a store. I got most of the way there after reading [http://ubuntuforums.org/showthread.php?t=302099](http://ubuntuforums.org/showthread.php?t=302099) I want the slide show to start automatically, which I figured out you can do by putting ```
 ooffice -show /path/to/slideshow.odp 
``` in the 'Startup Applications' list. The problem with this approach is that it loads to soon and then the gnome-panels load over the top of the slide show. Is there some way to make the slide show stay on top of the gnome panels or load after a set pause of say 10 seconds?

I already tried setting the slide show window as always on top in the window rules plug-in of compiz and setting the gnome panels as below.

---

### Post by ad_267 on 2009-06-09
```
sleep 10 && ooffice -show /path/to/slideshow.odp
```

You might have to put that in a separate script. Eg:
```
#!/bin/bash
sleep 10 && ooffice -show /path/to/slideshow.odp
```

Save that as ~/runslideshow. Do a chmod a+x runslideshow. Then you can run "runslideshow" on login.

---

### Post by SoftwareExplorer on 2009-06-10
Thanks, it works. 

On a sidenote, I had to do /home/bjorn/runslideshow, otherwise nothing would happen.

Thanks!

---

### Post by ad_267 on 2009-06-10
> **SoftwareExplorer said:**
> Thanks, it works. 

On a sidenote, I had to do /home/bjorn/runslideshow, otherwise nothing would happen.

Thanks!

Ok yeah sorry, I forgot about that! You could also make a bin directory and put it in there (/home/bjorn/bin/runslideshow). Then you can run it with runslideshow rather than the full path.

---

### Post by SoftwareExplorer on 2009-06-10
> **ad_267 said:**
> You could also make a bin directory and put it in there (/home/bjorn/bin/runslideshow). Then you can run it with runslideshow rather than the full path.

Hm, that's cool that you can have your own personal /bin. I always thought that it had to be in the real /bin (or have a symbolic link from there).

Thanks for the help, I tried it on the target computer and it worked just fine.

---

