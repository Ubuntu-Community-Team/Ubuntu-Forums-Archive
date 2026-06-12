---
title: "youtube grabber?"
date: 2009-05-28
forum: General Help
---

### Post by elobire on 2009-05-28
hey,
does anyone have a youtube grabber for ubuntu, i cant seem to find one which works for ubuntu.

-Elobire

---

### Post by frodon on 2009-05-28
The youtube video should be available in /tmp once viewed.

---

### Post by s.fox on 2009-05-28
Hi,

Are you using firefox?  If so you could just add a plugin like "Down Them All".    Their are also others available fom the mozilla add ons pages.

If you want an application I used to use Pytube.  I think its in synaptic package manger.

Hope this helps.

-Ash R

---

### Post by bryncoles on 2009-05-28
its easier than you think. just open your file browser, and navigate to /tmp (click up till you cant click no more, then you should see the temp folder)

there will be a flash video file called something like F87968754. copy it to the desktop and rename it - its the youtube video!

---

### Post by elobire on 2009-05-28
thanks guys il try both of those ways out, and yes im using fire fox

---

### Post by lukjad on 2009-05-28
The easiest way I know to get youtube videos is **youtube-dl**. To install it, go to the terminal (Applications->Accessories->Terminal) and type:

```
sudo apt-get install youtube-dl
```

That will install it. 

Then whatever files you want to download, go to another terminal and type something like this:

```
youtube-dl http://www.youtube.com/watch?v=iEMXaTktUfA
```

That should just download it to your /home/UserName/ folder.

---

### Post by e-Gee on 2009-05-28
I'm using Miro for downloading YouTube videos for me that is the easiest way

---

### Post by wabbalee on 2009-05-28
youtube-dl in the package manager, very simple.
or like said before check your /tmp folder for the flash files. wait until completely downloaded and then copy them to your home folder. if you close your browser then the file may dissapear from /tmp.

---

### Post by wabbalee on 2009-05-28
youtube-dl in the package manager, very simple.
or like said before check your /tmp folder for the flash files. wait until completely downloaded and then copy them to your home folder. if you close your browser then the file may dissapear from /tmp.

---

### Post by propagation_of_sound on 2009-05-28
I prefer to use clive

---

### Post by spcwingo on 2009-05-28
I use pytube.  It not only downloads, but transcodes, too.  You can find it here:

[http://www.marcosrodriguez.me/pytube/]("http://www.marcosrodriguez.me/pytube/")

---

