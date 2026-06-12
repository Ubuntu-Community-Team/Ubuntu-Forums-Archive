---
title: "Play .rm files"
date: 2006-07-02
forum: Desktop Environments
---

### Post by amunimanghi on 2006-07-02
How do you play .rm files in linux? I tried opening them in totem, but all i get is sound. I don't want to use Real Player. Is there an alternative.

---

### Post by rudiz on 2006-07-02
Mplayer and mozilla-mplayer can play it.

sudo apt-get install mplayer mozilla-mplayer mplayer-fonts

---

### Post by 3rdalbum on 2006-07-02
[QUOTE=rudiz]Mplayer and mozilla-mplayer can play it.

sudo apt-get install mplayer mozilla-mplayer mplayer-fonts[/QUOTE]

You need the w32codecs package though, don't you?

---

### Post by rudiz on 2006-07-02
if u use the command i give it automatically installs de codec

---

### Post by amunimanghi on 2006-07-02
Ok, I get sound now, but I don't get any pictures. I used this command. ```
sudo apt-get install mplayer mozilla-mplayer mplayer-fonts
```

---

### Post by amunimanghi on 2006-07-03
bump

---

### Post by maki_03 on 2007-05-21
I know this thread is almost dead... but just want to try my luck. I was successfully able to install mplayer with the help of this guide. Thanks. But now, i'm having problems on resizing the video. I tried doubling the size but only the window resizes, the video is stuck with its original size... Any ideas?

---

### Post by Praill on 2007-05-31
Hey maki. This thread is pretty old but I happened to stumble on it.
The mplayer thing has to do with the video driver you have it using. Open up mplayer and right click on the video screen. Go to preferences and then over to video. Theres a whole list of drivers available here. Some wont work, some will sorta work, and a few should work perfectly. The ones that worked for me were the opengl ones.

However, if you want to get rid of mplayer and use totem (I like it better). Use this command:
sudo apt-get install libxine-main1 libxine-extracodecs libxinerama1 libxine1 totem-xine

The xine libraries and plugin with totem work with EVERYTHING. Unlike the gstreamer plugin that the official ubuntu wiki recommends. I have no idea why they recommend the less functional gstreamer plugin, but owell. I figured this step out on my own.

Good luck :)

---

### Post by cerebrosus on 2007-08-10
I have no words to thank you Praill :)

---

### Post by Innomen on 2007-10-15
I used your command, and when i drag drop a *.rm on totem, i get "Video codec 'Real Video 3.0' is not handled. "

Suggestions?

---

### Post by defZA on 2007-11-22
Get RealPlayer for linux to play .rm files at

[SIZE="5"][http://www.real.com/linux](http://www.real.com/linux)[/SIZE]

---

### Post by DoktorNo on 2007-11-23
> **defZA said:**
> Get RealPlayer for linux to play .rm files at

[SIZE="5"][http://www.real.com/linux](http://www.real.com/linux)[/SIZE]

and this is the main reason, why closed formats sucks; you are stuck with propertiary, closed-source players.

---

### Post by ljbirns on 2007-12-25
I searched the forum for how to play  .rm files and found this thread.  I am very very new to Ubuntu

Rudiz :  Thank you.:)  Your post solved my problem  1-2-3.

(  Mplayer and mozilla-mplayer can play it.

sudo apt-get install mplayer mozilla-mplayer mplayer-fonts )

Lew

---

