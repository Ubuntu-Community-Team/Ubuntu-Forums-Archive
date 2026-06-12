---
title: "Mozilla Mplayer loads to 99% and hangs and/or stops after one second"
date: 2006-07-19
forum: Desktop Environments
---

### Post by fulfox on 2006-07-19
Originally this was going to be a question on how to fix mplayer in mozilla loading a video to 99% and then hanging. I read some other posts on this forum and found an extension for firefox called MediaPlayerConnectivity from this thread [ http://www.ubuntuforums.org/showthread.php?t=176063 ]("http://www.ubuntuforums.org/showthread.php?t=176063) which allows you to use another player depending on the type of file, but I still wanted to use mplayer. I found that if you configure the extension for /usr/bin/X11/mplayer rather than /usr/bin/X11/gmplayer (which you get to by leaving the wizard to use mplayer to play files after you install it and going into tools>MediaPlayerConnectivity>Configure>Media Players), then videos work and you are still using mplayer. I believe the difference is the gui (gmplayer) which causes the glitch and non-gui player (mplayer). 

(Note: there are no onscreen controls for this version of mplayer, but there are keyboard commands which can be found here: [http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html#sect11]("http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html#sect11"))

The site on which I was trying to play movies was the archived rocketboom videos page, videos such as [http://www.rocketboom.com/vlog/archives/2004/11/rb_04_nov_15.html]("http://www.rocketboom.com/vlog/archives/2004/11/rb_04_nov_15.html")

Anyway, I didn't think this belonged in the how-to section, because I am not sure if this workaround is a fluke that just works for me, or if it works for everyone else. Also, I was wondering if there is a direct mozilla-mplayer plugin that uses mplayer rather than gmplayer, so I don't have to use MediaPlayerConnectivity. 

I hope I did this all right, that it is in the proper section and I used the proper technical terms since this is my first post on this forum and I have been using linux full time for less than a week. I just want to say that this forum is quite an asset for new users of linux and ubuntu like me!

---

### Post by Perfect Storm on 2006-07-19
Try mplayerplug-in instead: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) (uninstall mozilla mplayerplugin first before trying it)

---

### Post by fulfox on 2006-07-20
Thanks for the suggestion, I tried the mplayerplug-in, first uninstalling mozilla-mplayer, and it still doesn't work, I think the mplayerplug-in is still using the gui mplayer? Thanks though, I guess I will stick to my solution.

---

### Post by chudder on 2006-10-08
I'm having the same problem, mplayer used to work fine but I think since the new version came out, that's when problems arose, it came through synaptic as a regular upgrade.  For both video and audio it would buffer and then it would say "stopped" and nothing would get it to run.  Then I used media player connectivity extension and it would work then but I couldn't stop it or pause without it going weird and multitasked.  I have 512 Ram and centrino duo so I don't think it's my computer.  I started using totem and it works but I like mplayer better overall for streaming media.  What can I do?  

thanx

---

