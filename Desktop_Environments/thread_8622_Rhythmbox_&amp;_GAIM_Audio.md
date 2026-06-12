---
title: "Rhythmbox &amp; GAIM Audio"
date: 2004-12-19
forum: Desktop Environments
---

### Post by ZakZak on 2004-12-19
Is there a known problem with having a song playing in Rhythmbox (an MP3 file in this instance) and GAIM not being able to play audio events?  I listen to a lot of music but when I am, I don't hear when one of my GAIM contacts has sent me a message!

-Zak

---

### Post by Rancoras on 2004-12-19
Yeah, I think the sound system only handles sound from one source at a time.  I've never investigated how to change that behavior though.  Let me see what I can find, unless someone else has an answer.

---

### Post by LongTooth on 2004-12-19
I posted a simular question. I can't have two "internetnet' sounds at the same time. If I'm listening to an internet radio staion my Gain audio alerts do not work. Playing an audio CD is no problem. Any solution to this would be greatly apperciated.

---

### Post by ZakZak on 2004-12-19
I tried a few more things (GAIM while flash animation with sound is playing, etc) and that looks to be the case...  Only one audio source works at a time.

It has been years ago and was some very old version of Slackware, but I specifically remember being impressed that this wasn't an issue then.  I also ran Win95 or Win98 at the time and it couldn't play audio from more than one source there, but Linux could do it.  I thought that was soooo cool!

But Ubuntu isn't doing it for some reason.

Hope someone can figure out a way to solve it! :)

-Zak

---

### Post by Rule on 2004-12-20
I dunno why it does this. but I remember once I changed form OSS to ALSA and it worked fine...unless it was someting else haha too long ago to remember

---

### Post by Quest-Master on 2004-12-20
Isn't there some package called esd that needs to be installed in order for more than one sound to be played at a time. I haven't tried it, but I remember it worked for many people in IRC.

---

### Post by ZakZak on 2004-12-20
[QUOTE=Quest-Master]Isn't there some package called esd that needs to be installed in order for more than one sound to be played at a time. I haven't tried it, but I remember it worked for many people in IRC.[/QUOTE]
 Doing a search in synaptic for esd turns up several libraries, drivers, and plugins for various programs for the "Enlightened Sound Daemon".  I don't see the daemon itself, though.  I don't think I'm going to switch to Enlightenment just to get that functionality (assuming esd is part of Enlightenment).

---

### Post by ZakZak on 2004-12-20
[QUOTE=Rule]I dunno why it does this. but I remember once I changed form OSS to ALSA and it worked fine...unless it was someting else haha too long ago to remember[/QUOTE]

Okay, stupid question - how would one switch from OSS to ALSA on Ubuntu Warty? :)

-Zak

---

### Post by rolfpal on 2004-12-20
ESD is usually installed by default, you just have to turn it on.

My understanding is that Ubuntu has ALSA installed by default as well as the OSS compatability layer.

Go into -- Computer > Desktop Preferrences > Sound  and select "Enable Sound Server Startup"  That will start ESD and allow yolu to hear two events at once.

Cheers,

---

### Post by LongTooth on 2004-12-20
[QUOTE=rolfpal]
Go into -- Computer > Desktop Preferrences > Sound  and select "Enable Sound Server Startup"  That will start ESD and allow yolu to hear two events at once.

Cheers,[/QUOTE]


Checked and that option is already enabled. Hasn't made a difference.

---

### Post by ZakZak on 2004-12-20
[QUOTE=rolfpal]ESD is usually installed by default, you just have to turn it on.[/QUOTE]
Looks like it IS turned on (the option is checked and /usr/bin/esd shows up in ps) but I still get no GAIM sound while Rythmbox is running. :(

I have no experience with other modern Linux desktops, so I have no idea if this is an Ubuntu-specific thing.

-Zak

---

### Post by piedamaro on 2004-12-21
The problem arise beacause I guess your card is using software mixing.
There are 2 possibilities:
you can use a sound server or you can use can configure alsa to do mixing at kernel level with the dmix plugin (the latter is my preferred).

Take a look here: [http://taint.org/wk/AlsaSoftwareMixing](http://taint.org/wk/AlsaSoftwareMixing) 
(don't consider the parts relevant to esd).

after that hopefully your card is using dmix, now you need to tell every program you use with sound output, to use the alsa driver.

In gaim this can be accomplished by wrting a line in a .libaorc file or something, can't remember the details, it's clearly explained in the faq at gaim's site.
With rhythmbox, since it uses gstreamer, you need to tell gstreamer to use alsasink as output method: fire up gconf-editor/system/gstreamer/0.8/default and change the audiosink value to read alsasink.

You can still try to use esd with dmix, as suggested in the site linked above, (I think the only benefit is to have desktop event sounds), if you do, set gstreamer to use esdsink.

Use aoss to launch firefox, then you should have flash animations with sound too.
Is suggested in the site linked above, you can find further information on the alsa wiki, and on google :)

Hope this helps.

---

### Post by LongTooth on 2004-12-21
Whew! That looks like a tough row to hoe. Maybe I'll just put up with this minor irritation and just let it go. Piedamaro thanks for your hard work.

---

### Post by piedamaro on 2004-12-21
You're welcome, and of course, if you buy a card with an hardware mixer (it should be very cheap, like a sound blaster live), all your problems will magically disappear  ;)

---

### Post by poptones on 2004-12-21
*Whew! That looks like a tough row to hoe. Maybe I'll just put up with this minor irritation and just let it go.*

These forums aren't too efficient. They break up threads really easily.
Anyway, this isn't hard. Just did it this afternoon, took about an hour to google the clues and put it all together. My system is pretty much default and I never had to install esd, but if you do just search in synaptic for esd. 

Just follow the steps in my post on the page below and you'll have your system able to play dozens of streams at once. Barring any system specific oddities, it ain't hard at all.

[http://www.ubuntuforums.org/showthread.php?t=8235&page=3](http://www.ubuntuforums.org/showthread.php?t=8235&page=3)

---

### Post by varunus on 2004-12-22
A quick, easy way to get sound working (I hope):

Setting up sound isn't really that hard...you just need to have the right asound.conf file, and the right ESD configuration.  I've made it easy...below are an asound.conf and an esd.conf that will make your system work.

MAKE SURE TO INSTALL libesd-alsa0 using synaptic!!!  Otherwise, this will not work.

/etc/asound.conf

pcm.card0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"

}


pcm.dmixer  {
    type dmix
    ipc_key 1025
    slave {
           pcm "hw:0,0"
           period_time 0
           period_size 1024
           buffer_size 4096
           periods 128
           rate 44100
    }
    bindings {
           0 0
           1 1
    }
}


/etc/esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Create these two files (or replace them if they exist)...This configuration works for me on several different sound cards...

You should probably choose "enable sound server startup" in the gnome control center...

Also, make sure to set gstreamer to use ALSA or ESD in your "Multimedia Systems Selector", and also set GAIM to use ESD or have it use the "command" option to play sounds, and set the command to "aplay %s"...

Hope this helps.  This works for me, as almost everything can play audio at the same time...

---

