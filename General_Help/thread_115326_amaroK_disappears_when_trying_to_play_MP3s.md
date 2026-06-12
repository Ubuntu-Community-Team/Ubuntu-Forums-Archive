---
title: "amaroK disappears when trying to play MP3s"
date: 2006-01-10
forum: General Help
---

### Post by mserms on 2006-01-10
As soon as I press play (using Dapper), amaroK vanishes and dies without giving any error messages.

I'm using amaroK 1.3.7-0ubuntu4 and the same version of amarok-grstreamer

Kaffeine can play mp3s fine.

Any ideas on how to track this down?

---

### Post by Sharkscott on 2006-01-10
I was using amaroK in SuSE 10.0 and I could not get it to do JACK!! I un-installed it and now I use Kaffiene for just about everything. So far, I am happy with the performance of it. 

I use Kubuntu instead of Ubuntu, I prefer KDE, I am NOT a Gnome hater, I just like KDE better, I do not know enough about computers to know why yet, but someday :-)

---

### Post by petteri on 2006-01-10
I've got another problem with AmaroK.  When I minimize AmaroK I can't find it again. I've got to go to the system resouces util. to kill the program.  It doesnt appear in my toolbar at the bottom of my screen.  Sorry to hijack your thread!  I'm running hoary and KDE 3.4.

---

### Post by Sharkscott on 2006-01-10
That's funny, cause I couldn't get it to shut down when I was using it. it would go from open window to icon on the panel, to running in the background. It would try to open everything I wanted to see or hear, I had to un-install it just to keep it from opening itself up and hijacking my multimedia. 

Sorry, I don't think I am helping:-)

---

### Post by Neo Ex on 2006-01-10
Try using amarok-xine instead of amarok-gstreamer. I use the first one and it works great.
Don't forget to install gstreamer-plugins! (yes, also if you use the xine engine)

---

### Post by Sharkscott on 2006-01-10
Good point, I went the other route and use the gs and xine plugins with Kaffiene. I still use Xine and mplayer as well.

This darn Linux stuff is so cool, :-)

---

### Post by mserms on 2006-01-11
I fixed the problem by changing my output plugin to alsasink.

---

