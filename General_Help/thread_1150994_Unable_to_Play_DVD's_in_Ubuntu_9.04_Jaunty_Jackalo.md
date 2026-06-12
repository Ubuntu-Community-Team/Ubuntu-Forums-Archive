---
title: "Unable to Play DVD's in Ubuntu 9.04 Jaunty Jackalobe"
date: 2009-05-06
forum: General Help
---

### Post by Chrono Reaper on 2009-05-06
I was about to play X-files on my Ubuntu 9.04 Jaunty when it stated it cannnot play the format in Movie Player. when I asked it to play it brought the DVD to the usual copyrights before the movie starts but it hung during playback so a tried to skip forward to get to the menu untill i got the window telling me it cant play the format. 

I tried it again installing the totem plug-in in movie player but i got the same problem. What should I do?

---

### Post by Legace on 2009-05-06
Try VLC instead of Totem.
It can be found in Add/Remove applications..

---

### Post by colin.p on 2009-05-06
Before you do anything, try another movie to see if it plays. If it does, then it was a problem with the disk, if it doesn't, you may need the proper codecs.

---

### Post by aquavitae on 2009-05-06
Have a look at this guide on playing dvds - it might help:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by Marlonsm on 2009-05-06
Open the terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
put in your password, and Ubuntu will do the rest for you.

That package contains pretty much anything that couldn't be on Ubuntu's CD because they are proprietary software.

---

### Post by gfe on 2009-05-06
Even with the codecs and I all that, I couldn't get Movie Player or vlc to work with some DVDs. But things worked perfectly with Kplayer for some reason. I'm not sure why, as (I think) it's just a shell for what was already in my system, but I won't rap what works.

---

### Post by growled on 2009-05-06
Do you have libdvdcss installed from Medibuntu?

---

### Post by Marlonsm on 2009-05-06
Use Add/Remove to look for Totem (Xine backend) that worked for me.

---

### Post by Chrono Reaper on 2009-05-06
...just to let you know it may be a problem with it getting to the main menu selection...

---

### Post by colau on 2009-05-06
> **Chrono Reaper said:**
> I was about to play X-files on my Ubuntu 9.04 Jaunty when it stated it cannnot play the format in Movie Player. when I asked it to play it brought the DVD to the usual copyrights before the movie starts but it hung during playback so a tried to skip forward to get to the menu untill i got the window telling me it cant play the format. 

I tried it again installing the totem plug-in in movie player but i got the same problem. What should I do?
```

sudo apt-get install libdvdread4

```
Then open a terminal window and execute: 
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
May need
```

sudo apt-get install libdvdcss

```

---

### Post by Chrono Reaper on 2009-05-06
I managed to get the movie and the main menu running with Movie player with Xine...form of video compressor. DVD plays fine now.

---

### Post by spaided on 2009-05-06
Thanks a million!!!!

---

### Post by Chrono Reaper on 2009-07-12
After installing Xine I still have limitations on DVD's I am able to view, some of the older ones work ok but the newer ones seem to still have the same problem of not being able to read. I get the message saying if i ran it with libdvdcss when i already have it installed.

---

