---
title: "Totem weird behavior"
date: 2005-12-17
forum: Desktop Environments
---

### Post by furghella on 2005-12-17
I finally managed to get Totem to play commercial DVDs - sort of. 

If I pop in a DVD after booting, Totem gives me the following error message:

Totem could not play 'file:///dev/hdc'. 
There is no plugni to handle the movie

HOWEVER, if I first play a Music CD with Sound juicer and THEN I try to play the same DVD with Totem, Totem has no problem recognizing and playing the same DVD.

Thie behavior is quite consistent. Happens every time I fire up the system.

Any thought on what Totem may missing that Sound juicer makes available?

---

### Post by Gurgeh on 2005-12-17
In my limited experience, in its present state, I have concluded that Totem is rubbish. You would be ish to seek an alternative, anyone know of a better movie player? (mplayer + composite is a bit of a no go by the way)

---

### Post by furghella on 2005-12-17
Well, I tried Xine. It seems to work, but looks terrible. I kind of like Totem. It's simple and elegant. Too bad it's such a problematic application.

---

### Post by Gurgeh on 2005-12-17
Yeah you are right there, it looks like it should be a good program, but it isn't. There has to be a viable alternative tho, mplayer is horrific and problematic too... If you really are desperate, you could try wine & Media player altho I should be hung for saying that...

---

### Post by Adeva on 2006-01-29
I had the same problem: totem could not find my DVD in fstab, Mplayer did fine and gxine, too \\:D/

Adeva

---

### Post by psomas on 2006-01-29
i prefer mplayer...
it looks like the powerdvd program in xp...
it's not as good as powerdvd but it works fine...

---

### Post by Perfect Storm on 2006-01-29
Go for VLC :cool: 

Well, back to the totem problem.

Enable universe and multiverse and also add PLF to your sourcelist.

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools gstreamer0.8-plugins-multiverse libdvdcss2 avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin totem-xine totem-xine-firefox-plugin
gst-register-0.8

```

That should cover it all.

---

### Post by Adeva on 2006-01-29
VLC is nice, but after viewing my Matrix DVD with gxine and VLC both programs hang and dont play after I restarted my computer. 

There must be another error: 

it seems that both programs cant access "dvd://"
totem said it could not found the DVD in fstab - but it is there...
after trying "/dev/hdb" (which is my DVD) instead of "dvd://" VLC works fine again, totem quits with: "Failed to find mountpoint for device /dev/hdb in /etc/fstab"

hm, and now VLC wont work again... :confused: 

dev/dvd/ is a x-special/device-block to /dev/hdb

anyone got a clue ?

Adeva

edit:
if you eject and insert the DVD again VLC will play with "/dev/hdb"... :-)

---

### Post by [pl]ice on 2006-01-29
totem is bad ... for older ubuntu there was a fix ;)  yeh, my crashes v.often totem-xine etc, yeh, try other ones :) 
have fun!

---

