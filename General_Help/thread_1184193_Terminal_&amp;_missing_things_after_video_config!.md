---
title: "Terminal &amp; missing things after video config?!?"
date: 2009-06-10
forum: General Help
---

### Post by pblack00 on 2009-06-10
OK, I'm completely new to Ubuntu, I've basically set up Jaunty Jackolope to run Boxee.  I've gotten it installed, and set it up to run the video signal through my s-video output.  It's a nvidia card and I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=665704](http://ubuntuforums.org/showthread.php?t=665704)

to set up my TV as a clone using the s-video output.  So now here's my problem.  I know cannot use the terminal program, all I get is a white box, with no text.  I can get into command line mode fine.  Also now all my boxes are missing the red X in the top right corner too.  I'm pretty sure I messed up something in the previous directions, since this is my first experience with Linux.

Thanks for any help in advance!
pblack00

---

### Post by nothingspecial on 2009-06-11
I know nothing of tv out with nvidia but the tutorial got you to back up your old xorg.conf

```
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf.backup1
``` 

and replaced it with anew one

```

sudo cp /home/username/xorg.conf.twinview /etc/X11/xorg.conf
``` 

To get back to where you were when you started simply switch them back.

```
sudo mv /etc/X11/xorg.conf ~/xorg.conf.twinview
```
```

sudo mv /etc/X11/xorg.conf.backup1 /etc/X11/xorg.conf
```

---

### Post by pblack00 on 2009-06-11
Thanks, I'll try this out.  As you quote says "Linux assumes you know what you are doing", I don't so, this is what gets me in trouble.

pblack00

---

