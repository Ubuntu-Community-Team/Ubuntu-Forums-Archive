---
title: "Flash player/Gnash problem"
date: 2009-03-01
forum: General Help
---

### Post by thermobee on 2009-03-01
Ok i recently installed ubuntu and i finally got everything to work properly with the dual boot. Now the problem im having ( hopefully the last one) is that streaming online videos such as you tube and nfl.com videos wont work. It is just a blank screen, even though they do load in youtube. I tried right clicking on the image and it says that the player is Gnash. I have already tried re installing both flash player and gnash and that did not solve the problem. Here are two screenshots of what it looks like:

[[IMG]http://img237.imageshack.us/img237/2020/75580069.th.png[/IMG]](http://img237.imageshack.us/my.php?image=75580069.png)

[[IMG]http://img58.imageshack.us/img58/1306/youtube.th.png[/IMG]](http://img58.imageshack.us/my.php?image=youtube.png)

---

### Post by Rallg on 2009-03-01
If you have a 32-bit system, you probably want to use flashplugin-nonfree (shown in Synaptic package manager). If 64-bit, I cannot advise.

---

### Post by thermobee on 2009-03-01
> **Rallg said:**
> If you have a 32-bit system, you probably want to use flashplugin-nonfree (shown in Synaptic package manager). If 64-bit, I cannot advise.
its 32-bit, and i have flashplugin-nonfree installed already

---

### Post by sailthesea on 2009-03-01
I found that removing gnash seemed to solve this 
Hope that helps

I'm having trouble installing the codec for gstreamer at the moment
Get error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by perlluver on 2009-03-01
> **sailthesea said:**
> I found that removing gnash seemed to solve this 
Hope that helps

I'm having trouble installing the codec for gstreamer at the moment
Get error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Run in a terminal ```
sudo dpkg --configure -a
``` that should fix that problem.

---

### Post by thermobee on 2009-03-01
Ok uninstalling gnash did not help me.

---

### Post by sailthesea on 2009-03-01
Sorry it didn't work
I seemed to have a conflict when Flash player was installed Obviously not the same thing for you , check post above though

---

### Post by sailthesea on 2009-03-01
Thanks perlluver
 That worked a treat I'll butt out of this thread and see if I can remember how to fix the flash player config for thermobee I only did it last nite but it was a lengthy one
Cheers

---

### Post by thermobee on 2009-03-01
> **sailthesea said:**
> Thanks perlluver
 That worked a treat I'll butt out of this thread and see if I can remember how to fix the flash player config for thermobee I only did it last nite but it was a lengthy one
Cheers
That would be awesome :guitar:

---

### Post by Rallg on 2009-03-01
One other possibility: If you are using Firefox, open Firefox, Edit, preferences, applications. For the Flash media types, be sure that Flash (rather than Totem or Movie Player) is selected.

---

### Post by sailthesea on 2009-03-01
Ok this was my fix on the flash player install BUT it took some time and I'm sure I did it the hard way This by the way is for Firefox in 8.10 32 bit
and has left some sweeping up do but it does seem to locate all the packages needed and get things going

Anyway In Terminal

1  sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
    2  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
    3  sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar 

Eventually, due in part to a very slow connection it worked Don't know how clued up on Terminal you are but its often the easiest way to railroad a result Just remember to clear up afterwards
Hope that it helps
[-o<
And wot rallg said

---

### Post by thermobee on 2009-03-01
> **Rallg said:**
> One other possibility: If you are using Firefox, open Firefox, Edit, preferences, applications. For the Flash media types, be sure that Flash (rather than Totem or Movie Player) is selected.
Its set up on Shockwave Flash(in Firefox) for both

---

### Post by thermobee on 2009-03-01
> **sailthesea said:**
> Ok this was my fix on the flash player install BUT it took some time and I'm sure I did it the hard way This by the way is for Firefox in 8.10 32 bit
and has left some sweeping up do but it does seem to locate all the packages needed and get things going

Anyway In Terminal

1  sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
    2  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
    3  sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar 

Eventually, due in part to a very slow connection it worked Don't know how clued up on Terminal you are but its often the easiest way to railroad a result Just remember to clear up afterwards
Hope that it helps
[-o<
And wot rallg said
its downloading right now...

---

### Post by thermobee on 2009-03-01
lol it worked before its even done downloading Haha. Thanks dude you are the man

---

### Post by sailthesea on 2009-03-01
No problem man!
:p

---

### Post by sailthesea on 2009-03-01
By the way I can't take any credit for that 
Someone helped me I helped someone else The deal is you do the same!
Welcome!

---

