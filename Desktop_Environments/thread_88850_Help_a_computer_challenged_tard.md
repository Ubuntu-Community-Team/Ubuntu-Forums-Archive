---
title: "Help a computer challenged tard"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Shiranami on 2005-11-11
I installed kubuntu some time back since I was more familiar with KDE, but now I'd like to switch to gnome and regular ubuntu, because I'm getting a bit fed up with some programs not wanting to work in KDE (and also, the latest KDE is starting to look and feel so much like windows it's giving me the creeps). As stated in the topic, I don't really have the know-how to fix what's wrong with the programs (the problem is mainly that most everything is very unstable and keeps crashing. Firefox especially, since that required a bit of fixing to work in the first place), nor do I know how to switch the default desktop from KDE to gnome. I tried to look for instructions and help for that, but it seems I suck at searching too. :( 
I was also wondering if I should be aware of any other problems that might arise because of the said fact that I installed kubuntu instead of ubuntu. 
If anyone could help out a desperate tard girl like me, I would muchly appreciate it. ;) I may not be completely computer savvy, but I can follow clear instructions.


----
PS. I've also been wondering about the sounds and how a program always "reserves" the sound device to its use, so I can't play several things at once. This does not bother me that much. What bothers me is that I can't make some progams let go of the sound device so that some others could use it. This is bothersome is such situations as for instance, when I'm watching a video and need to pause and look at some other clip, or to listen to a song in between. While the video is paused, the sound device is still reserved and I have to press stop or quit the whole program for the sounds to work again. One more annoying situation is when I want to listen to music and then go to a flash site with sounds. In between the songs I'm playing in my mediaplayer, the flash site hogs the sound device and I'm suddenly left without music. It doesn't help to turn off the flash sounds. I have to close the tab and wait half a minute before I can continue to listen to music.
Anything I could do about this?

---

### Post by tonym on 2005-11-11
Use aptitude to remove the kubuntu-desktop package and install ubuntu-desktop.

This may still leave a lot of kde packages installed.  In aptitude search for all packages including "kde" and mark for removal.  Then search for broken packages (hit "b") and mark these for removal as well.  Rather messy but I haven't found an easier way if the packages don't go automatically.

---

### Post by Shiranami on 2005-11-11
Thanks. I'll try that. :smile:

---

