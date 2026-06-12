---
title: "Youtube videos don't work in Opera"
date: 2009-05-22
forum: General Help
---

### Post by Nicka727 on 2009-05-22
I am a new Ubuntu user, I installed Adobe flash player and now it works fine with Firefox. But when I try to watch a video on Opera it just shows a blank screen were the video should be. Thank for any help..Nick

---

### Post by Nicka727 on 2009-05-22
No answers?

---

### Post by Insightfill on 2009-05-22
Quick search found some suggestions - I have Opera and Firefox both installed, but hadn't thought to try Youtube via Opera.

[http://my.opera.com/community/forums/topic.dml?id=186564](http://my.opera.com/community/forums/topic.dml?id=186564)

Older articles, but they say it works.

---

### Post by Arup on 2009-05-22
> **Nicka727 said:**
> I am a new Ubuntu user, I installed Adobe flash player and now it works fine with Firefox. But when I try to watch a video on Opera it just shows a blank screen were the video should be. Thank for any help..Nick

Are you on Ubuntu x64 or x32?

---

### Post by Nicka727 on 2009-05-22
I installed it using Wubi, but I have a AMD 64 processor..would that mean 64bit? I know my windows is 32 bit though. Sorry I'm new.

---

### Post by lovinglinux on 2009-05-22
Please wait at least 24 hours to bump you thread. It is consider impolite to bump or complain about the lack of replies just a few minutes after posting your thread. You need to give some time so your post can be spotted by someone with the knowledge to answer your question. Also keep in mind that there are hundreds of new posts every day and everyone that helps in these forums are doing it for free on their spare time.


How did you installed flash player plugin? I'm not sure about this, but there is a method of installing flash that puts the plugin inside Firefox plugin folder instead of in the system files, so maybe Opera is currently not capable of using it.

---

### Post by Nicka727 on 2009-05-22
Ok sorry about the bump. But I installed it in .deb than just clicked install package and it worked fine on Firefox.

---

### Post by lovinglinux on 2009-05-22
> **Nicka727 said:**
> Ok sorry about the bump. But I installed it in .deb than just clicked install package and it worked fine on Firefox.

I guess it should work then. Anyways, check in Opera if the flash plugin is available. I don't know how to do that, because I don't use Opera.

---

### Post by ceciliaFX on 2009-05-22
I do use Opera

once you download "flashplugin-nonfree"

make sure Opera knows it's there by going into Preferences/Advanced/Content

click "Plug-in Options" button

make sure the Shockwave Flash plugin shows up. if not, look for it here:
/usr/lib/flashplugin-nonfree

it should then show up in the "Downloads" list

---

### Post by Nicka727 on 2009-05-22
> **ceciliaFX said:**
> I do use Opera

once you download "flashplugin-nonfree"

make sure Opera knows it's there by going into Preferences/Advanced/Content

click "Plug-in Options" button

make sure the Shockwave Flash plugin shows up. if not, look for it here:
/usr/lib/flashplugin-nonfree

it should then show up in the "Downloads" list

Yup it shows up. Yet it is still just showing a white screen where the video should be.

---

### Post by ceciliaFX on 2009-05-22
> **Nicka727 said:**
> Yup it shows up. Yet it is still just showing a white screen where the video should be.
well, Opera doesn't like duplicates of plugins.

so you have to makes sure you tell it to only look in places that Don't have any copies of the same ones. I hope that's clear.

here's another thread from opera that might be helpful

[http://my.opera.com/community/forums/topic.dml?id=274856](http://my.opera.com/community/forums/topic.dml?id=274856)

---

### Post by rudy.b on 2009-05-23
I use Opera 10 and Youtube videos are working for me, but flash has always been kinda hit-and-miss in my experience with Ubuntu (for both Opera and Firefox).

Here's what my Plug-ins pages says under Shockwave Flash (Tools > Advanced > Plug-ins):

```

application/futuresplash	                                            spl
application/x-shockwave-flash	                                            swf
/usr/lib/mozilla/plugins/flashplugin-alternative.so
```

Not sure if that helps at all...

---

### Post by cybrsaylr on 2009-05-23
> **ceciliaFX said:**
> well, Opera doesn't like duplicates of plugins.

so you have to makes sure you tell it to only look in places that Don't have any copies of the same ones. I hope that's clear.

here's another thread from opera that might be helpful

[http://my.opera.com/community/forums/topic.dml?id=274856](http://my.opera.com/community/forums/topic.dml?id=274856)

ceciliaFX,
Thanks that got my video working in Opera.
Both plugin paths were checked.
I unchecked one, the top opera/plugins, and video and audio now plays in Opera as it does in Firefox.

---

### Post by ceciliaFX on 2009-05-24
Yippie!!

---

### Post by cybrsaylr on 2009-07-27
Well gang i'm back again.
Installed 9.04 64 bit on my daughter's brand new Compaq desktop tower.....took 6 minutes and runs great!

Put in Flash code in terminal to get flash working then installed Opera 9.64 64 bit for her. Same thing happened, no video only sound on UTube. FF plays UTube video and sound fine.

Tried the same 'fix' as in post #13 above that got UTube video working on my PCs with Opera but it didn't work on her new tower.

Any ideas to get UTube video to work?

---

### Post by cybrsaylr on 2009-08-02
Bump....

Any ideas to get UTube video to work?

---

### Post by UbuntuNerd on 2009-09-06
try the fix from this guide:
[http://my.opera.com/ubuntunerd1/blog/how-to-install-opera-web-browser-in-ubuntu-hardy-plugins](http://my.opera.com/ubuntunerd1/blog/how-to-install-opera-web-browser-in-ubuntu-hardy-plugins)

---

### Post by samir1510 on 2009-09-07
hi all,
Opera needs the following plugins:
1. flashplayer.xpt
2. libflashplayer.so

Easy way to get these:
a) go to synaptic, type "flashplayer.xpt" in the search column...you will get only one hit, just install it.
--------------------------------------------------------------------------
b) you can do the same with "libflashplayer.so" or use the terminal.
$ sudo apt-get install flashplugin-nonfree
--------------------------------------------------------------------------
Hope this helps.
[flashplayer.xpt is the one that people forget to install]

---

