---
title: "I need an iTunes replacement for Linux"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Noah0504 on 2005-11-02
I know it sounds stupid, but the only thing keeping me from hitting the delete button on my Windows partition, is not having an adequate media player.

Everyone has suggested amaroK, but I've read many articles explaining how some functionality is lost when using it under Gnome.  I was running out of options, so I decided to install it anyway.  Whenever I attempted to play a song, the application just closed without any warning.

Anyway, I'm open to suggestions.  One of the key features I'm looking for is the ability to keep my music organized.  In iTunes, if you drop in a folder of songs, it will automatically copy them to my music folder and take care of naming the files and whatnot.

---

### Post by adwait on 2005-11-02
Try installing the package gstreamer-amarok. After that, in the amarok preferences chose your player engine as gstreamer.

Anyway, besdies amarok, Juk is a good player but again its a KDE player. Technically, a KDE app should work fine in GNOME, but in case of music player, sometimes you just have to install the right engine. Many of them use aRTs which GNOME doesn't come with. Besides that, theres rhtyhmbox which isn't all that great but works. Theres XMMS which looks and feels just like Winamp.

---

### Post by wylfing on 2005-11-02
This isn't stupid at all. It's one reason Crossover Office supports iTunes. So there's that route -- get Crossover. I don't think any native applications approach the excellence of iTunes yet.

---

### Post by drummer on 2005-11-02
There's rhythmbox (installed by default), I use Quod Libet ([http://www.sacredchao.net/quodlibet)](http://www.sacredchao.net/quodlibet)), and there's also Banshee. Rhythmbox and Banshee are more like iTunes and both are in active development, adding new features, etc. and the next versions look promising. I like QL because of it's search features and it's on-screen display plugin. Amarok has by far the most features though, and most of them should be fully functional in Gnome if you have the right packages installed. If Amarok is just crashing, try running it from a terminal and see what the output is when it crashes, might give you a hint as to what's exactly happening.

---

### Post by aysiu on 2005-11-02
[QUOTE=Noah0504]One of the key features I'm looking for is the ability to keep my music organized.  In iTunes, if you drop in a folder of songs, it will automatically copy them to my music folder and take care of naming the files and whatnot.[/QUOTE] You're not going to find this in a native Linux application. The ripping of songs/initial naming/organizing happens with an application like Sound Juicer. The playing and maintenance is done by another program (AmaroK/Rhythmbox/etc.).

I, too, haven't found the match of iTunes. AmaroK and others have some features iTunes lacks, though. What I've learned is that some of the "new" features are worth embracing. First of all, AmaroK and Rhythmbox both work on a "scan" organization instead of a library. There are pluses and minuses to this. 

One plus is that as long as the songs are in the right folder(s)--i.e., ones that get scanned--they'll be available for play. In iTunes, once the song gets deleted or added to a folder, iTunes has no way to keep track of that song being there unless it's indexed in the library.

The minus? Well, depending on how large your library of music is, the rescan can take quite a while. I've found that JuK is pretty fast at scanning (though, in general, it's not as fully featured as AmaroK or Rhythmbox).

Something that iTunes lacks that all three of the aforementioned native Linux players have is on-screen display. When the song moves to the next song, a little pop-up (in AmaroK or JuK) will let you know what the song is. In Rhythmbox, the minimized window itself will display the song name and artist. Along with this, you can also define global keyboard shortcuts for next/previous/play/pause/stop. That way, if you hate a song and want to move to the next one, you don't have to bring the music player to the front and then switch back to the app you were using.

The FoxyTunes extension sort of approximates this behavior but not exactly, and for Firefox only. iTunes is very limited this way. It has a lot of other great features, but if you embrace the native Linux apps, you may realize there are a lot of features iTunes itself could do with.

---

### Post by The Headhunter on 2005-11-02
gtkpod is good for adding/deleting songs on your ipod

---

### Post by bradroger on 2005-11-02
What about something that keeps track of ratings and playcounts in a similar way iTunes does.  I'm not ready to lose the entire functionality of smart playlists and syncing ratings with my ipod.

---

### Post by aysiu on 2005-11-02
[QUOTE=bradroger]What about something that keeps track of ratings and playcounts in a similar way iTunes does.  I'm not ready to lose the entire functionality of smart playlists and syncing ratings with my ipod.[/QUOTE] I believe AmaroK does this. For more info on AmaroK's features, read [the AmaroK handbook](http://amarok.kde.org/component/option,com_staticxt/staticfile,index.html/Itemid,49/)

---

### Post by bradroger on 2005-11-02
I realize Amarok has smart playlists, but it's not at all integrated with the ipod as far as I can tell.  It doesn't see any of my ratings or playcounts from the ipod.  Besides that, its ratings are 0 to 100.  How would that work?

I'm trying Banshee right now...I'll let you know how that goes

---

### Post by Donnut on 2005-11-03
Anyone have any luck with an iTunes-type player?  I am currently working with amaroK, it seems to be the most stable, but I can't get it to play AAC...

---

### Post by jasay on 2005-11-03
I think you want the faad codec.  If you use the gstreamer engine in amarok then install gstreamer0.8-faad.  There are a few other faad codecs in synaptic/apt, but I'm not sure what work with different engines.

---

### Post by mustang on 2005-11-03
The closest thing to a iTunes type player is RhythmBox Music player. I think it comes with Breezy but I don't exactly remember.

In case it doesn't:

```
sudo apt-get install rhythmbox
```

and if I recall correctly, it natively plays AAC files

---

### Post by veloct on 2005-11-03
Also check this thread out.

[https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29)

---

### Post by billputer on 2005-11-03
[QUOTE=Donnut]Anyone have any luck with an iTunes-type player?  I am currently working with amaroK, it seems to be the most stable, but I can't get it to play AAC...[/QUOTE]
The development versions now have full AAC support (with gstreamer0.8-faad), but you have to install those from source if you're up to the task.  Here's a HOWTO:  [http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn](http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn) 

If you're willing to wait, 1.4 will be out soon enough, but until then you need to install from SVN.

---

### Post by doclivingston on 2005-11-03
[QUOTE=bradroger]What about something that keeps track of ratings and playcounts in a similar way iTunes does.  I'm not ready to lose the entire functionality of smart playlists and syncing ratings with my ipod.[/QUOTE]

Rhythmbox will keep track of rating and playcounts as iTunes doesm and has smart playlists. However it doesn't do ipod syncing yet.

---

