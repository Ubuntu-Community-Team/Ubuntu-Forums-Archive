---
title: "Totem Codecs/Plugins"
date: 2006-03-11
forum: Desktop Environments
---

### Post by noumaan on 2006-03-11
Almost all files that I try to play in totem I end up at and error telling me that may be I need to download corresponding plugins to handle this stream. 

I tried to play mpga, mp3, wma files none played. What could possibly be wrong? I heard that it is the universal player for linux. Do I need to download codecs from somewhere or what?

---

### Post by spencewah on 2006-03-11
it'd be nice if these came preinstalled but I'm sure it's a licensing nightmare...

anyway here's a friendly bump because i'm having the same problem.

---

### Post by Svictor on 2006-03-11
If you just installed ubuntu, then yes, you need to install some extra codecs to read proprietary formats like mp3, wma, ... More info here [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29") 
I'm far from sharing the opinion that Totem is "the universal player for linux". I'd rather cite mplayer as an example of such a player (if it exists). I was never able to get totem to work properly (at least in ubuntu). So I don't know if it's woth wasting your time with it ... But go for the codecs anyway.

Edit : 
If you are in the post-install situation, have a look here : [http://ubuntuguide.org/](http://ubuntuguide.org/) . Another clue is : I think vlc plays (nearly) all formats out-of-the-box. You can install it through synaptic. Have fun !

---

### Post by Djartklom on 2006-03-11
Totem is okay for playing the various video files like Xvids and MPEGs, but it is not a great jack-of-all-trades app like Winamp that does playlists and multimedia library management.  VLC is a very nice alternative to Totem that is available in the repositories.  Xine is a solid DVD player app.  I never warmed up to Mplayer and its cumbersome interface.  

The Gnome CD player works well for audio CDs, and actually, I can't comment much on what to use for digital audio since I haven't messed around with Rythmbox or Amarok, but those two apps are popular with the Ubuntu/Kbuntu crowd.

But, if you haven't done it yet, download and install Automatix, which will set you up with all the various multimedia codecs and more.  After you install it, you will be able to play almost anything.  Comprehensive installation instructions, as well as a link to the app itself are available on this forum.

---

### Post by akiro.yamamoto on 2006-03-11
The default totem uses the gstreamer system.
 Personally I use totem-xine or mplayer with the mozilla-mplayer plugin with
the w32codecs with 0 problems ;)

---

### Post by Max Roswell on 2006-03-11
Hey, there...

Pretty much brand new to Ubuntu...installed it about 12 hours ago.  So far, I'm in total love with it.  EXCEPT...

I've found and installed VLC (and the Mozilla/Firefox plugin), but I can't seem to make it the default application.  Everything still wants to use Totem, even though I've set the file associations in Firefox AND right-clicked on some .wmv files and tried to set it that way.

Any ideas?  All the stuff I've found online is about a half-inch over my competency.

---

### Post by Svictor on 2006-03-11
> I've set the file associations in Firefox
Did you deactivate the default plugin in firefox ? Edit > Preferences > Downloads > Plugins ? I never really understood how firefox handles those plugins (how it chooses to use the vlc over the mplayer one ), but deactivating them lets you choose what software to use. Alternatively, you could install the "Media Player Connectivity" extension (it's on the Mozilla website ; check for this name), that will let you choose how to open each media file ...

> right-clicked on some .wmv files and tried to set it that way.

Appearently not successfull :-k. Did you right-click and just chose the "open with" option ? This is not enough. For permanently changing the association, right-click on the file > properties and then, on one of the tabs, you can choose how to open this file type (can't tell you the name of the tab though cause I don't use gnome anymore). Good luck !

---

