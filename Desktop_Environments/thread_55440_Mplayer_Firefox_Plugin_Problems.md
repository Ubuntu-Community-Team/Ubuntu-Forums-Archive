---
title: "Mplayer Firefox Plugin Problems"
date: 2005-08-08
forum: Desktop Environments
---

### Post by FNM on 2005-08-08
I have the Mplayer plugin for Firefox installed, and anytime I click on a link to a stream, whether it be audio, or video, Mplayer starts, and eventually, after a long wait, I just get a black window. No sound, no video. Also, some audio streams just keep loading forever, and nothing happens. I'm trying to play an MPEG audio stream right now, and it just keeps going back and forth between 98%, and 99%. How can I fix this? I've tried reinstalling Mplayer, and still no luck. I can't get anything to play.

---

### Post by bob k on 2005-08-09
I have been having problems with the mplayerplug-in. You didn't say what version of the plugin or mplayer you have, but this problem is on there faq.

mplayerplug-in buffers 99% and hangs
This can becaused by a few things:

    * mplayer is not in the path
    * An older version of mplayer is installed
    * The config option "rtsp-use-tcp=1" is set and mplayer is not compiled with the live.com support

there is a howto at
[http://ubuntuforums.org/showthread.php?t=44560&highlight=mplayerplug-in+2.85](http://ubuntuforums.org/showthread.php?t=44560&highlight=mplayerplug-in+2.85)

There is also a debug option in the mplayerplug-in.conf
that will dump programmer defined debug data to the .xsession-errors file, and check the java control panel, but to understand any of it you will have to goto the source to understand it.

I will have to say mplayer is the hardest applications I have installed on Linux.

If you want full screen off the web don't compile with the --GTK2 option, because when the code setups the data structure for the stream it checks the -fs option and if GTK2 is true it does nothing. I would assume that is because you are supposed to have the controls and the right click menu with a full screen option. I'm running 3.05.x and the controls only work about 1/2 the  time, and if you want to loop it will only hold the -fs one time thru and revert to the size the video was posted at.

I will drop down to 2.85 some time this week, if that does not work, it's off to totem

---

### Post by kamiccolo on 2005-08-13
How did you install this plugin? I'm new to Ubuntu and I don't find it via Synaptic. I have also added the repos mentioned in the wiki about restricted formats, but I don't find it. Can you help me?

---

### Post by bjweeks on 2005-08-13
Look at [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer).

---

### Post by kamiccolo on 2005-08-14
Cool, this works 100%. I wonder why didn't recognize this site yet. Thank you.

---

### Post by kamiccolo on 2005-08-14
Ok, not 100%. The plugin is properly installed, but there comes no sound.

---

### Post by wh0rd on 2005-08-14
You might wanna' try the Media Connectivity extension for Firefox....

---

### Post by kamiccolo on 2005-08-15
This extension is good, but doesn't work. It tries to load e.g. mplayer, but there comes no sound.
Before I used Ubuntu, I was a Fedora user. There I installed mplayerplug-in after I installed mplayer. I used apt-get for this. Then it worked. With Ubuntu I did the same, but without success.
My problem is an embedded wav-file in the Event Box of an internet-community, which plays a sound everytime there's a new event. It's not funny when you hear nothing of this. ;-)

---

### Post by kamiccolo on 2005-08-16
*pushing to the top*

---

### Post by glug101 on 2005-08-19
[QUOTE=wh0rd]You might wanna' try the Media Connectivity extension for Firefox....[/QUOTE]

I am also having trouble with the mplayerplug-in having no sound.  This is slightly annoying for me, and really annoying for my brother since he is a recent windows convert and loves audio and video. (Somehow a hundred+ viruses infecting your computer is good incentive for this ;) )  Where can one obtain this 'Media Connectivity' extension for firefox?

---

### Post by Zifnab on 2005-08-19
[QUOTE=bjweeks]Look at [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer).[/QUOTE]
Hah! I wish. None of the mplayer stuff in the repositories actually works now.

---

### Post by glug101 on 2005-08-21
Hey, it's allright guys, don't get up.  I found the Media Connectivity Extension.

[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)

Enjoy!

---

