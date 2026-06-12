---
title: "There is something very wrong with Flash in Ubuntu"
date: 2009-06-04
forum: General Help
---

### Post by Lockheed on 2009-06-04
I had flash working in Opera just fine.



The problem was that every few minutes I lost sound in the entire system, be it when watching avi movies, youtube or listening to a radio station.

I had to restart pulse and ALSA to have it back.



So, I installed the newest ALSA and configured it according to one of the very good HOWTOs from this forum. And great! Sound did not disappear again! 

But now, flash videos played normal only for few seconds and then started to fastforward (in Ubuntu ffd was without sound, in VirtualBox running windows 2003 x64, the fastforward was also occuring but WITH sound).



I tolerated it as long as I could and then decided to do something about it. So, I installed flash-nonfree (or something like that).



And voila! 
Now, there is no video in flash at all! Not even a gray box, jusst white blank space. THe funny thing is, that it still plays the sound of the video AND it still fastforwards after few seconds AND now the sound stays even during FFD!


I would call Mulder or Scully but they retired so I'm down to this forum ;)


Any supernatural ideas appreciated.

---

### Post by pmfabri on 2009-06-04
> **Lockheed said:**
> I had flash working in Opera just fine.



The problem was that every few minutes I lost sound in the entire system, be it when watching avi movies, youtube or listening to a radio station.

I had to restart pulse and ALSA to have it back.



So, I installed the newest ALSA and configured it according to one of the very good HOWTOs from this forum. And great! Sound did not disappear again! 

But now, flash videos played normal only for few seconds and then started to fastforward (in Ubuntu ffd was without sound, in VirtualBox running windows 2003 x64, the fastforward was also occuring but WITH sound).



I tolerated it as long as I could and then decided to do something about it. So, I installed flash-nonfree (or something like that).



And voila! 
Now, there is no video in flash at all! Not even a gray box, jusst white blank space. THe funny thing is, that it still plays the sound of the video AND it still fastforwards after few seconds AND now the sound stays even during FFD!


I would call Mulder or Scully but they retired so I'm down to this forum ;)


Any supernatural ideas appreciated.

Try Mozilla Firefox or Internet Explorer in Wine. Don't forget to install Flash into Wine.

---

### Post by vinutux on 2009-06-04
install latest flash player from [COLOR="Red"]adobe labs[/COLOR]

---

### Post by Lockheed on 2009-06-04
I removed flash-nonfree and Opera is back to the second stage (ffd).
FireFox is showing exacly the same behaviour.
I would love to install IE but it never goes past errors during installation.

---

### Post by Dustin2128 on 2009-06-04
use mozilla firefox or epiphany

---

### Post by Soul-Sing on 2009-06-04
i'am using gnash 0.8.5 on jaunty.
-gnash (common)
-browser plugin

uninstall flash non free, and the flash plugin in ./mozilla. use alsa sound in stead of pulseaudio.

gnash 0.8.5 works great, is open source and is made for linux....

-youtube works fine. 100% fine.

---

### Post by Lockheed on 2009-06-04
I tried updating to the newest Flash 64bit but it changed nothing.

I then removed all flash and installed gnash. Now, the symptoms are different.
1. The video loads but doesnt start playing (play button shows II all the time). If I put the slider anywhere on the progress bar, video plays for 1 second (no sound) and then stops again.

Tested in FireSux and Opera.

---

### Post by pastalavista on 2009-06-04
Open synaptic and uninstall everything you find when you search for 'SWF'. Then remove all other versions of flash except 'adobe-flashplugin'. That's all I have and it works great for everything. Be sure, also, that you have all the gstreamer codecs.

---

### Post by Lockheed on 2009-06-04
there is no such thing as "adobe-flashplugin" in my synaptic.

---

### Post by vinutux on 2009-06-04
perhaps the problem related to mis-configuring drivers of video or sound cards

---

### Post by pluckypigeon on 2009-06-04
> **leoquant said:**
> i'am using gnash 0.8.5 on jaunty.
-gnash (common)
-browser plugin

uninstall flash non free, and the flash plugin in ./mozilla. use alsa sound in stead of pulseaudio.

gnash 0.8.5 works great, is open source and is made for linux....

-youtube works fine. 100% fine.

I've never got gnash to work

---

### Post by Lockheed on 2009-06-04
> **vinutux said:**
> perhaps the problem related to mis-configuring drivers of video or sound cards

I wasn't touching anything related to video before now and when flash was working relatively ok.

I did install the newest ALSA but I would guess it is now properly configured since it never crashes, contrary to the previous state.

---

### Post by pastalavista on 2009-06-04
> **Lockheed said:**
> there is no such thing as "adobe-flashplugin" in my synaptic.
then you need to enable multiverse repositories in Software Sources (third party) and install ubuntu-restricted-extras

---

### Post by Ac1ds0ld13r on 2009-06-04
I may have missed it, but have you tried reinstalling Opera? 

I use it exclusively and haven't had a single issue out of it, and I'm listening to internet radio right now through the Pandora widget. I regularly troll through Youtube and watch movies from my comp (and have since switching to Ubuntu). :/

---

### Post by Lockheed on 2009-06-04
> **pastalavista said:**
> then you need to enable multiverse repositories in Software Sources (third party) and install ubuntu-restricted-extras

> Note: In Ubuntu 9.04 (Jaunty), the main, universe, restricted and multiverse repositories are enabled by default.
And ubuntu-restricted-extras is installed.



> I may have missed it, but have you tried reinstalling Opera?
Are you using 64bit system?

---

### Post by Lockheed on 2009-06-04
Ok, I installed new opera (10 beta) and again the newest Flash plugin.
No change.

---

### Post by Soul-Sing on 2009-06-04
> **pluckypigeon said:**
> I've never got gnash to work

On the dutch forum we did an experiment using gnash instead of flash non free. Gnash 0.8.5 came out nice and stable. (jaunty)
Very little complaints...

---

### Post by Lockheed on 2009-06-05
> **leoquant said:**
> On the dutch forum we did an experiment using gnash instead of flash non free. Gnash 0.8.5 came out nice and stable. (jaunty)
Very little complaints...

Have you or your colleagues ever stumbled on gnash behaviour I described few posts ago?

---

### Post by Soul-Sing on 2009-06-05
> **Lockheed said:**
> Have you or your colleagues ever stumbled on gnash behaviour I described few posts ago?

No. We did some tests, also because several off. ubuntu documentation suggests flash non free. We'd like to document and test the open source "flash project" because most members had never heard of it. 
Again Gnash 0.8.5 is doing fine, earlier versions do struggle....

---

### Post by Lockheed on 2009-06-05
Well, for me Gnash is not working. However, its erratic behaviour is different than this of Flash so perhaps the underlying cause if different and although Flash cannot be fixed, Gnash can?

---

### Post by Lockheed on 2009-06-08
bump, bump, bump

---

### Post by pastalavista on 2009-06-08
Go to [this Adobe page]("http://get.adobe.com/flashplayer/otherversions/") and download the .deb version. Uninstall all your flash plugins and then double click this deb to install it... worked for me

---

### Post by Lockheed on 2009-06-08
```
**[COLOR="Red"]Error: Wrong architecture 'i386'[/COLOR]**
```

There is no deb for 64 bits.

---

### Post by pastalavista on 2009-06-08
> **Lockheed said:**
> ```
**[COLOR="Red"]Error: Wrong architecture 'i386'[/COLOR]**
```

There is no deb for 64 bits.
Sorry, didn't know.. it that case, you'll need [this version]("http://labs.adobe.com/downloads/flashplayer10.html") (link at the bottom) in a tar.gz format which isn't quite so [easy to install]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html") but not all that difficult.

---

### Post by Lockheed on 2009-06-08
Yup, this is exactly what I already have.

---

### Post by pastalavista on 2009-06-08
...well then, I don't know what to tell you. did you install it correctly? did you remove all the other versions before install? did you check your Firefox plugins? You might try installing VLC media player since it supposedly comes with all the necessary codecs. I guess when I installed it with the .deb package for the 32bit version, it added itself to Synaptic. Good-luck with this.

---

### Post by Lockheed on 2009-06-08
there is not much to install, You just put the .so file in firefox plugin folder and both FF and Opera are making use of it. 

Both of them exhibit exactly the same behaviour - after random number of seconds of proper playback, video starts to speed up (2-4 times faster than normal) and sound disappears. If I close the browser and reopen it, sometimes it helps. If not, then I need to do it few times.

Also, I already have VLC and all the codecs.

Anyway, thanks for your input.

---

### Post by pastalavista on 2009-06-08
I just thought of something... have you tried it without any video acceleration? It may be that your video drivers are not handling it correctly. Try turning off special effects in the appearance applet. BTW, what video card are you using?

---

### Post by jmszr on 2009-06-08
Lockheed,

I don't know if it will help your problem, but you can get the 64-bit .deb here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) .

---

### Post by Lockheed on 2009-06-08
> **pastalavista said:**
> I just thought of something... have you tried it without any video acceleration? It may be that your video drivers are not handling it correctly. Try turning off special effects in the appearance applet. BTW, what video card are you using?

The card I have is the one in my sig. NVidia 6150.
I will test no-acceleration and will get back as soon as I can confirm if it's working or not.


[QUOTE=jmszr]
I don't know if it will help your problem, but you can get the 64-bit .deb here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)[/QUOTE]
Where exactly?



---------
EDIT:
Oh, it just crapped out again after few minutes without acceleration.

---

### Post by pastalavista on 2009-06-08
sorry.. I'd probably be removing (completely --purge to get rid of all the configs) and reinstalling browsers about now, removing everything with the word flash in it and see where that gets you before installing whatever plugins you want to try... might try a previous kernel etc. etc... good luck

---

### Post by jmszr on 2009-06-08
Never mind

---

### Post by Soul-Sing on 2009-06-09
64 bit flash : [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
it is a working alfa.

libflashplayer.so
on your Dekstop: 

```
cd Desktop
```
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

or otherwise copy libflashplayer.so) to /usr/lib/mozilla/plugins via ```
gksudo nautilus
```
after this close nautilus!
---------------------------------------------------------------------------------
or make in your./home a mozilla plugin folder and copy libflashplayer.so in the pluginmap.

---

### Post by Lockheed on 2009-06-09
Thanks, but as I said, I already have flash 10 alpha from Adobe Labs.

---

### Post by Lockheed on 2009-06-30
I compiled new kernel and now Flash works as it supposed to :popcorn:

---

