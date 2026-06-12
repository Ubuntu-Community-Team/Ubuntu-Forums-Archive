---
title: "got beryl, lost video"
date: 2007-02-19
forum: Desktop Environments
---

### Post by icelechi on 2007-02-19
Hi,
I am really excited. I got beryl to work. But every time I try to watch a video, either online or just on a stand alone player, I get a black screen but I hear the sound. Is there something that I need to do?
Thanks

---

### Post by jordanmthomas on 2007-02-19
Whichever video player you are using you need to find out how to set it to out the video to X11 or xshm

It's usually in the options / preferences (with the exception of totem)

---

### Post by icelechi on 2007-02-19
I'm pretty new to some of this stuff so you will have to bear with me.
How would you do this in totem?
thanks

---

### Post by jordanmthomas on 2007-02-19
Ugh...you had to use totem, didn't you.    :)

It's a little more complicated than with say mplayer or vlc, but it is still possible.  There are two backends to totem; I am going to assume you are using the default.

You need to first install the **gstreamer0.10-gl** package.
Then, go to System --> Preferences --> Multimedia Systems Selector and go to the video tab
For default output, put anything that says gl or X11 (X11 is what I use and it works very well, so I suggest it)

See if that helps.  If not, then we may need to go another route.

---

### Post by icelechi on 2007-02-19
Thanks,
I put it on X11,, but that did not work. I put it on X Window (No Xv) and that did it :)
Thanks again

---

### Post by CujoQuarrel on 2007-02-26
Having the same problem. 

Where does one change it for VLC? Found many options but nothing that
appears to fit this.

Thanks

---

### Post by jordanmthomas on 2007-02-26
Settings --> Preferences --> Video --> Output Modules

You need to check 'Advanced Options' in the bottom right.
Then, select X11 Video Output
You'll probably need to restart VLC for the changes to take effect

---

