---
title: "No sound in Quake III"
date: 2009-10-15
forum: Gaming &amp; Leisure
---

### Post by Jaraxle on 2009-10-15
I'm back with yet another question. :)

After some trial and tribulation I managed to get Quake III installed, mainly by following the instructions here:

[http://www.blog.highub.com/linux/install-and-play-quake-iii-arena-on-ubuntu/](http://www.blog.highub.com/linux/install-and-play-quake-iii-arena-on-ubuntu/)

However, sound doesn't work. This seems to be a common issue with Quake III under linux. I'm trying to follow the instructions at the bottom of the screen for fixing the problem with sound (by editing /etc/init.d/bootmisc.sh)

What I don't understand is what is meant by:

```
add lines above : exit 0
```

I can open bootmisc.sh by running:

```
sudo nano /etc/init.d/bootmisc.sh
```

And I realize that I am supposed to add the lines:

```
echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'quake3-smp.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss''
```

What I don't understand is where these lines should go. The instructions seem to indicate they should go "above: exit 0". I'm guessing this is above a line which says exit 0 in the .sh file. I see a line toward the bottom that says exit 3, but not exit 0.

Or should I add those lines as soon as the file opens, above the part that says:

```
#!/bin/sh

```?

I also found this site:

[http://nullkey.ath.cx/et-sdl-sound/](http://nullkey.ath.cx/et-sdl-sound/)

and downloaded the quake3-sdl-sound.gz file but I'm really not sure if I should try running this file. I think I may screw something up.

I'm sure someone here has encountered this problem. Could you tell me how to edit the /etc/init.d/bootmisc.sh file? Or is there a better way? I'd love to play Quake III native. Thanks!

---

### Post by Jaraxle on 2009-10-18
Well, after reading several web pages and trying things that didn't work, I decided to give up on this.

I'm going to install ioquake for linux instead. So far, *that* isn't working either, but I'm getting close.

---

### Post by Rhemat on 2010-07-10
IOQuake3 worked for me.  What does terminal tell you when you try to install the .run file?

I do hope someone comes through with a sound fix for the regular Q3, since I also want to play Wolfenstein:  Enemy Territory, and Return to Castle Wolfenstein, since there is no IO versions of those.

---

