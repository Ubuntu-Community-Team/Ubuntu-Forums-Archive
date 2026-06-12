---
title: "How can i play Streamtuner streams with Rhythmbox?"
date: 2005-02-22
forum: Desktop Environments
---

### Post by André on 2005-02-22
Hi there,

i just installed streamtuner because i am a big fan of streamripper and it is very easy to save a stream this way.

When i tried to play a stream it asked for XMMS wich i don't have installed and don't want to be installed on my system. In the properties menu there is a section where you can set which command should be executed, when you try to play a stream.

Could anybody tell me how to pass this play command to rhythmbox? I just can't figure out which parameters i have to pass to do this so it just starts rhythmbox and does nothing.

Another way would be to catch the stream in rhythmbox but again i have no idea how to do this.

Any help is appreciated.

Greetz 
André

---

### Post by Buffalo Soldier on 2005-02-22
This is what I did, hope it will work for you too. Launch streamtuner and at the toolbar go to:

Edit -> Preferences -> Applications

and then change
```
Listen to a .m3u file         xmms %q
Listen to a stream            xmms %q
```
to
```
Listen to a .m3u file         rhythmbox %q
Listen to a stream            rhythmbox %q
```

If you haven't install all of gstreamer plugin now its a good time to do so. Enable the universe repository in Synaptic, and look for gstreamer0.8-plugins.

---

### Post by ember on 2005-02-22
I can confirm it works. Yet this doesn't show the title in rhythmbox. Has anyone found out, how to do that?

---

### Post by André on 2005-02-22
Hi Buffalo Soldier,

does Rhythmbox actually play your stream? It opens up for me but doesn't play the song / stream.

I don't think that it is a plugin problem because 
1. Rhythmbox normally complains, when ist doesn't have the right one
2. I have nearly all gstreamer plugins installed which make sense :-)

Greetz
André

---

### Post by Buffalo Soldier on 2005-02-22
Hi Andre,

Yes, Rhythmbox actually plays the stream. But I had the same problem like yours when I first used Ubuntu. I tried installing all the plugins one by one, but all didn't manage to stream. In the end, the only plugin that make my Rhythmbox work is **gstreamer0.8-plugins**.


Hi Ember,

I'm not sure if this is what you're talking about, but my rhythmbox display the title.

---

### Post by ember on 2005-02-22
O.k. Mine doesn't - it just shows the IP-Adress instead of the Radios title. I'll look into it, when I'm at home.

---

### Post by André on 2005-02-25
Hi ember,

same problem here. It just shows the IP but at least it works!!

Thanks so much Buffalo Soldier. Using the plugins package really got me working.

Did you do something special to show the radio stations name like in your screenshot?

Greetz
VisionD

---

### Post by Buffalo Soldier on 2005-02-25
I don't remember doing anything else besides what I've told. I really wish I know how to help you guys.

This is just a wild guess. Could it be something like firewall blocking the rhythmbox from receiving Radio Titles info? - this proves how little I know, don't the number of post fool you :p

Anyone else has any ideas?

---

### Post by cvmostert on 2006-01-14
[QUOTE=Buffalo Soldier]Hi Andre,

Yes, Rhythmbox actually plays the stream. But I had the same problem like yours when I first used Ubuntu. I tried installing all the plugins one by one, but all didn't manage to stream. In the end, the only plugin that make my Rhythmbox work is **gstreamer0.8-plugins**.


Hi Ember,

I'm not sure if this is what you're talking about, but my rhythmbox display the title.[/QUOTE]


I will try to install all the pluggins and then play a .m3u stream... hopefully works.

---

### Post by SlugO on 2006-02-08
*sigh*...

I have all the gstreamers but when I start a station in Streamtuner Rhythmbox just opens up and does nothing.

Sucky :(

---

### Post by blueballs on 2006-04-12
i have this problem too, so i use vlc player instead, works perfect. But i still would like to know how to get rhythmbox to work with streamtuner. Spent hours looking for a solution, dosen't seem anybody have one.

---

### Post by DannoII on 2007-03-07
Same exact issue here, RhythmBox doesn't work from StreamTuner , but Amarok does.  If I hack in a URL from a Live365 stream (copy from address line in browser) I can get RhythmBox to play it.  Not a good way to select new streams though.

---

### Post by celebere on 2008-05-14
If you have the correct gstreamer plugins and clicking on a station in streamtuner brings up rhythmbox but does not play it, look under "Radio" in your rhythmbox side panel.  For me, the stations were being placed there as IP addresses, but not automatically played.  New IP's queue at the top of the list for me, so I use streamtuner to find stations, then manually play them by selecting the most recent IP.  Basically the problem I have is rhythmbox not automatically playing streams, so I just have to play them manually.

Does anybody have a solution to rhythmbox not displaying song info?  I'll mess around with my firewall, but I wonder if this is a gstreamer v0.10 bug.  What version is everyone who has problems using?

Edit: I just turned off my firewall and the song info started displaying.  It must be a different port from the stream or something(?).

---

