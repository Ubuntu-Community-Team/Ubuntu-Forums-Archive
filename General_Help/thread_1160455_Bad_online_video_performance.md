---
title: "Bad online video performance"
date: 2009-05-15
forum: General Help
---

### Post by Vacuum Tube on 2009-05-15
Ubuntu 9.04  FF browser

PIII 1.2G 512 ram

I am getting really bad performance (jerky or non-existant) playing videos from youtube or google video, even if I let the video buffer completely or replay it. So I don't think it's a network issue.

If I double click on video that I've recorded myself (AVI) that is stored on the HD, the movie player launches and after a few seconds just dissapears.

Videos stored locally were working on a previous install.

Any ideas?

TIA!

---

### Post by riza hylviu on 2009-05-15
Have you installed the non free adobe flash plug in? WHICH graphics card you have?

---

### Post by Vacuum Tube on 2009-05-15
> **riza hylviu said:**
> Have you installed the non free adobe flash plug in? WHICH graphics card you have?

I think so. Not sure.

The video card is a nvidia go2 moble 32M ram.

I have installed the nvidia drivers.

---

### Post by kerry_s on 2009-05-15
with only 512ram you might need to go lighter to have more resources for running intensive programs such as the media player.

---

### Post by lovinglinux on 2009-05-15
> **kerry_s said:**
> with only 512ram you might need to go lighter to have more resources for running intensive programs such as the media player.

I wouldn't blame the ram. I have a notebook with only 256 Mb of ram running Intrepid and it plays videos just fine. Take some time to buffer and start displaying them when I first launch the player, but it works flawlessly. On the other hand, I have a desktop running Jaunty, with much more processor power, 2 Gb of ram and it sucks playing flash.

@ Vacuum Tube

I don't have a solution for flash issues, since I'm struggling with it myself. If you watch videos mainly from YouTube and Google video, then you might want to use Firefox [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) extension with [this script](http://userscripts.org/scripts/show/34765). It will dynamically replace the flash player with your regular media player plugin ( I use gecko-mediaplayer), which is much less CPU hungry.

About the recorded avi's, you might fix the problems by following [this tutorial](http://ubuntuforums.org/showthread.php?t=766683).

---

### Post by kerry_s on 2009-05-15
> **lovinglinux said:**
> I wouldn't blame the ram. I have a notebook with only 256 Mb of ram running Intrepid and it plays videos just fine. Take some time to buffer and start displaying them when I first launch the player, but it works flawlessly. On the other hand, I have a desktop running Jaunty, with much more processor power, 2 Gb of ram and it sucks playing flash.

@ Vacuum Tube

I don't have a solution for flash issues, since I'm struggling with it myself. If you watch videos mainly from YouTube and Google video, then you might want to use Firefox [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) extension with [this script](http://userscripts.org/scripts/show/34765). It will dynamically replace the flash player with your regular media player plugin ( I use gecko-mediaplayer), which is much less CPU hungry.

About the recorded avi's, you might fix the problems by following [this tutorial](http://ubuntuforums.org/showthread.php?t=766683).

does that grease monkey thing work good, any problems to expect?
my laptops 450mhz 256mb ram, it stutters on some flash, but the media player is fine, i have full buffering set, i use gnome-mplayer+gecko-mediaplayer.

---

### Post by lovinglinux on 2009-05-15
> **kerry_s said:**
> does that grease monkey thing work good, any problems to expect?
my laptops 450mhz 256mb ram, it stutters on some flash, but the media player is fine, i have full buffering set, i use gnome-mplayer+gecko-mediaplayer.

It works pretty nice. Try it and you will feel a lot of difference, specially considering you do not have a powerful processor and that gecko-mediaplayer works good for you. 

Greasemonkey can be used for a lot of stuff, like mashups and web site customization. You might also like [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108).

Please post your impressions after using it.

---

### Post by kerry_s on 2009-05-15
> **lovinglinux said:**
> It works pretty nice. Try it and you will feel a lot of difference, specially considering you do not have a powerful processor and that gecko-mediaplayer works good for you. 

Greasemonkey can be used for a lot of stuff, like mashups and web site customization. You might also like [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108).

Please post your impressions after using it.

i got it, it's a little weird when loading but seems to work, i'm trying on 1 of the shows i been watching on youtube. even though i turned off the cache it's still caching though, so it's a wait. :D

---

### Post by lovinglinux on 2009-05-15
> **kerry_s said:**
> i got it, it's a little weird when loading but seems to work, i'm trying on 1 of the shows i been watching on youtube. even though i turned off the cache it's still caching though, so it's a wait. :D

Hit the play button after caching for while and it should play. I don't think you need to wait until it caches everything.

---

### Post by kerry_s on 2009-05-15
> **lovinglinux said:**
> Hit the play button after caching for while and it should play. I don't think you need to wait until it caches everything.

i tried that it didn't work, maybe cause it's like a 48min show?
anyways it's good enough, i can even do full screen or resize it to the size i want(alt+right click hold), now i don't have to go to the desktop. i can feel myself getting lazier already. ):P
see ya in another 48min, time for episode 7. :lolflag:

wait it worked this time, i hit play at 20% and it's starting to play.

hey lovinglinux, thank you very much.

---

### Post by lovinglinux on 2009-05-15
> **kerry_s said:**
> i tried that it didn't work, maybe cause it's like a 48min show?
anyways it's good enough, i can even do full screen or resize it to the size i want(alt+right click hold), now i don't have to go to the desktop. i can feel myself getting lazier already. ):P
see ya in another 48min, time for episode 7. :lolflag:

wait it worked this time, i hit play at 20% and it's starting to play.

hey lovinglinux, thank you very much.

You are welcome. The alt+right-click doesn't work for me. Do you use it while viewing the video on fullscreen?

---

### Post by kerry_s on 2009-05-15
> **lovinglinux said:**
> You are welcome. The alt+right-click doesn't work for me. Do you use it while viewing the video on fullscreen?

ya full screen it, then shrink it back, then you can mess with it all you want. it doesn't work for all vids, just some. probably a bug.
still getting use to it. gets a little messed up some times, like for instance now, i pulled it from the page before it was finished downloading so it messed up. the other 1 i had it fully buffered and stuck it in the corner set to the top and just bounced around the internet while i was watching the movie.

edit: i'm pretty sure it's a bug, cause now it won't come out anymore.

---

### Post by kerry_s on 2009-05-16
okay lovinglinux,
 i had a look at those user scripts and went with a different 1 that's cleaner.
it's called "youtube without flash" it gives you the same options but cleaner and it still lets flash be the default for vids that you know play fine.
i can view it in the player embedded or use the download, open it in gnome-mplayer or save for later.
[http://userscripts.org/scripts/show/41722](http://userscripts.org/scripts/show/41722)

---

### Post by lovinglinux on 2009-05-16
> **kerry_s said:**
> okay lovinglinux,
 i had a look at those user scripts and went with a different 1 that's cleaner.
it's called "youtube without flash" it gives you the same options but cleaner and it still lets flash be the default for vids that you know play fine.
i can view it in the player embedded or use the download, open it in gnome-mplayer or save for later.
[http://userscripts.org/scripts/show/41722](http://userscripts.org/scripts/show/41722)

Thanks for the tip. This script is way much better than the one I was using.

---

### Post by kerry_s on 2009-05-16
> **lovinglinux said:**
> Thanks for the tip. This script is way much better than the one I was using.

no, thank you for turning me on to grease monkey. ;)
i've been trying a lot of those scripts since you told me about them, been trying to weed out the good from the bad, there are a lot of bad or just plain old scripts.

i'll let you know if i find anything interesting, but i don't need much in the way of scripts for media, mostly only use youtube when i'm bored.

---

### Post by lovinglinux on 2009-05-16
> **kerry_s said:**
> no, thank you for turning me on to grease monkey. ;)
i've been trying a lot of those scripts since you told me about them, been trying to weed out the good from the bad, there are a lot of bad or just plain old scripts.

i'll let you know if i find anything interesting, but i don't need much in the way of scripts for media, mostly only use youtube when i'm bored.


Yeah, Greasemonkey is really nice, but there are a lot of bad scripts. I usually don't browse the script directory, unless I need a specific solution. I currently have only 2 more scripts installed. One for Apple trailers site and one for downloading videos from YouTube, which I barely use since Video DownloadHelper started to support mp4 downloads.

If you find something interesting, please let me know.

---

