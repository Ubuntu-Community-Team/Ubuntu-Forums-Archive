---
title: "WIne + iTunes + 64bit problems"
date: 2009-04-05
forum: General Help
---

### Post by wgensel on 2009-04-05
Hey all,  I just switched from Vista to Ubuntu 8.10 yesterday due to wireless management problems.  So far I'm loving it.

I am, however, having trouble installing iTunes 64bit with wine.  I'm getting this error.

will@will-laptop:~$ wine /home/will/Desktop/iTunes64Setup.exe
Trying to load PE image for unsupported architecture (AMD-64)
Trying to load PE image for unsupported architecture (AMD-64)
wine: could not load L"H:\\Desktop\\iTunes64Setup.exe": Bad EXE format for 

So...yeh.   I'm going to be honest that I don't really know what I'm doing here.  I need itunes as opposed to amarok because I have an itouch and occasionally download software, movies, etc.  and do not want to pirate them.

Any help will be much appreciated.

---

### Post by Chemical Imbalance on 2009-04-05
WINE isn't a drop-in replacement for Windows.  Not everything works on it.

Here is the list of iTunes in various versions in WINE:
[http://appdb.winehq.org/appview.php?appId=1347](http://appdb.winehq.org/appview.php?appId=1347)

They all have bronze ratings, and that means it doesn't work well in WINE.

---

### Post by mb_webguy on 2009-04-06
iTunes [has very limited functionality]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347") in Wine.  You might want to read [this]("https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore").  If you want to run iTunes, your best options are dual-booting with Windows or running Windows in a virtual machine like [Virtualbox]("apt:vboxgtk").  Since you're moving from Windows to Ubuntu and should therefore have a copy of Windows laying around, both of these options are viable.

Another thing to keep in mind is that no native-Linux application currently plays media with DRM.  DRM simply isn't compatible with open-source software, since if the methods to play DRM were revealed such that open-source software could be written to support it, then software could likewise be written to bypass or remove it.  So some of the music and video you've downloaded from the iTunes store may not play on Linux without first somehow removing the DRM in Windows.

[gtkpod]("apt:gtkpod") is the primary Linux application for managing iPods.  I don't believe the iPod Touch is fully supported currently, though it's only a matter of time, as gtkpod is actively developed.  gtkpod is only an iPod file manager, however, and cannot play music or connect to the iTunes store.

There are several [alternatives to the iTunes store]("http://en.wikipedia.org/wiki/Comparison_of_online_music_stores"), though few currently offer the selection available on iTunes, and I've yet to see one offer videos.  On the other hand, the media offered by these alternatives is generally DRM-free.  Amarok features integration with the [Magnatunes]("http://magnatune.com/") store.  [Amazon]("http://www.amazon.com/MP3-Music-Download/b/ref=sa_menu_dmusic1_gw?ie=UTF8&node=163856011&pf_rd_p=328655101&pf_rd_s=left-nav-1&pf_rd_t=101&pf_rd_i=507846&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=0G969XRF35ND89B774FR") also offers music downloads.

For video, however, I've yet to find an alternative for the iTunes store in the area of video downloads.  No company or organization has yet stepped up to challenge iTunes in that area.  Other than ripping videos obtained from other sources such as DVR recordings or DVDs, there are few completely legal alternatives iTunes in terms of obtaining videos for your iPod or any other mp3 player.

And while this isn't entirely relevant to your current issues...  When the time comes to replace your iPod, you may want to consider something like the SanDisk Sansa instead.  I just bought a Sansa Fuze for my mother a week ago, and was very impressed.  The Sansa line of mp3 players plays a larger number of file formats than the iPod, has voice recorder and a radio tuner (from which you can record), and has a slot for microSD/HC memory cards.  Sansas also don't require special management software (the result of which being that they are quite compatible with Linux), and are available at a fraction of the cost of equivalent iPods -- compare an 8GB Sansa View for about $90 to an 8GB iPod Nano for about $140.

---

### Post by Hospadar on 2009-04-06
If you need itunes to interface with an ipod, then depending on your ipod version (if it's an older one) gtkpod is probably your best bet, otherwise (for a newer ipod) I think you'll have the easiest time using VirtualBox.  It's quite easy to set up.  Be sure you get the non-open source edition from sun's website (google it, it's still free as in beer), the open source version doesn't have usb support.

---

