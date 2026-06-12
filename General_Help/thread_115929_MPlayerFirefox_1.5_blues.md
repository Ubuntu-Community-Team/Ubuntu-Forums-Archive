---
title: "MPlayer/Firefox 1.5 blues"
date: 2006-01-11
forum: General Help
---

### Post by Cliff76 on 2006-01-11
Hello all,

I'm a Mepis convert and I've been having trouble eversince I upgraded to Deer Park per the howto on the Ubuntu site. My main issue multimedia support. Here's what I did. I installed the MPlayer plugin via synaptic and tried to view a quicktime .mov which wouldn't work. Frustrated I figured out that Kubuntu didn't install the mplayer app so I looked in Synaptic for it. Not finding it and getting more frustrated I installed MPlayer via Arnieboy's Automatix Kubuntu app, which I stumbled upon during my searching. All seemed well until I recently started noticing that sound output from the plugin was of poor quality. I initially thought it was a problem with some of the files I was streaming over the web until I tried them in my hand-written alsa-play command line app. I then decided that it had to be something wrong with Mplayer after playing the same file from my hard drive through Mplayer. I tweaked about the configs in MPlayer and could not get any satisfactory results. Basically what's happening is the sound gets truncated at the end even as I use the ALSA driver setting. I tried using the arts driver and the truncation isn't as bad as with ALSA but it's still bad plus I get an error after trying to open the config window again. I gave up on using Mplayer and tried a variety of other plugins including kaffine, totem-xine, and gxine. nothing apparently handles a particular wav file I was trying to stream from the net. Maybe I didn't install the plugins correctly but I doubt that severly. (My installation consisted of cd'ing to the /opt/firefox/plugins folder and creating symbolic links to each plugin as I try them.) At this point I cannot effectively stream sound from the net in FF and I also have an outstanding issue getting the flash plugin to work while other apps play sounds. I guess I got a little spoiled by Mepis having all of this tuned out of the box, but I am getting frustrated with the challenges I've faced ever since I converted over. I love Kubuntu mainly because it appears more polished than Mepis and seems to get the newer stuff sooner without the headaches I had in Mepis but in the multimedia category it suffers from usability. I'm looking to get my Kubuntu tuned for multimedia the same way I did in Mepis. In Mepis I never had any trouble with multimedia except for the flash-plugin sound issue which I solved via artsdsp. Mplayer seemed rock solid there but under Kubuntu it doesn't feel quite right. Is there something wrong with the way I installed it? Am I missing some packages? I just want to be abled to play any multimedia file without hassle. Can somebody walk me through this?:confused:

---

### Post by aysiu on 2006-01-11
[QUOTE=Cliff76]
I love Kubuntu mainly because it appears more polished than Mepis and seems to get the newer stuff sooner without the headaches I had in Mepis[/quote] What newer stuff does Kubuntu seem to get? I'd argue it's the opposite. I just set up Mepis on one of my partitions, copied the /etc/apt/sources.list from the Mepis Lovers website, did a ```
sudo apt-get dist-upgrade
``` and I had Firefox 1.5 ready to go from the repositories. Breezy's backports still don't have 1.5 (I think they're in the Dapper development repositories). 

> but in the multimedia category it suffers from usability.  To be more precise, it suffers from not being preinstalled and preconfigured.

> I'm looking to get my Kubuntu tuned for multimedia the same way I did in Mepis. In Mepis I never had any trouble with multimedia except for the flash-plugin sound issue which I solved via artsdsp. Mplayer seemed rock solid there but under Kubuntu it doesn't feel quite right. I know you like the clean look of Kubuntu (I do, too), but have you considered, too, using PCLinuxOS? It's like Mepis, but cleaner--multimedia ready to go, and live and installer CD in one. 

> Is there something wrong with the way I installed it? Am I missing some packages? I just want to be abled to play any multimedia file without hassle. Can somebody walk me through this?:confused: I would do this:

1. a fresh reinstall of Ubuntu
2. install the MPlayer plugin through Synaptic
3. delete the Totem plugins in /usr/lib/mozilla-firefox/plugins
4. see if it works with Firefox 1.0.7
5. if it works, follow this guide to installing 1.5: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
6. if that still works, install Kubuntu ```
sudo apt-get install kubuntu-desktop
```

---

### Post by Cliff76 on 2006-01-11
Well you make some solid points but my experience with Mepis is that the debian repos are slow to come around. They just recently released KDE 3.4.3 and Kubuntu was running xorg way before Mepis. You can get leading edge from Debian SID and experimental but at the risk of totally crapping your system, which I've done plenty of times. Maybe overall both distros are about equal, my main reason for switching was a percieved memory leak that I couldn't isolate. Regarding MPlayer, I didn't see it in the Ubuntu repos which is why I installed it from Automatix Kubuntu (...which I think uses the Ubuntuo repos anyway so go figure!) Regarding your advice, I cannot tolerate a fresh install of anything at this point. I don't see how that could make a difference but maybe when I get some spare time I can play around with a reinstall. I know I am missing Mepis more and more each day though.

---

### Post by aysiu on 2006-01-11
[QUOTE=Cliff76]Well you make some solid points but my experience with Mepis is that the debian repos are slow to come around. They just recently released KDE 3.4.3 and Kubuntu was running xorg way before Mepis. You can get leading edge from Debian SID and experimental but at the risk of totally crapping your system, which I've done plenty of times.[/quote] The way I see it, they each have an experimental set of repositories. If you want to crap your system, you can use Sid for Mepis or Dapper for Ubuntu. 

> Regarding MPlayer, I didn't see it in the Ubuntu repos which is why I installed it from Automatix Kubuntu (...which I think uses the Ubuntuo repos anyway so go figure!) Should be in there if you follow the directions in the first link of my sig.

---

### Post by klepto on 2006-01-12
Hi,

I had the same program with the alsa drivers.
nano /etc/mplayer/mplayer.conf 
and add:

srate=48000

It stopped the popping and pausing for me.

Let me know if you have any other issues.

---

### Post by Cliff76 on 2006-01-12
ok, now i really screwed up! I installed the gxine plugin for firefox thinking it would work better than MPlayer and now I can't unregister GXine as the default handler for media files! I removed the sym links from the /opt/firefox/plugins folder and re-created links for MPlayer so I could try Klepto's suggestion and I still had GXine loading up. I googled a bit and decided to uninstall GXine entirely and now I can't get the MPlayer plugin to work even as the links are in the plugins folder. I'm sure it's related to GXine. When I first loaded GXine on a web page it asked me if I wanted to permanently register it as the default media handler for Firefox and I said yes. I looked all through Gxine configs, about:config and userprefs.js for firefox and I couldn't find a trace of gxine or xine anywhere. I'm lost. Please help!

---

### Post by Cliff76 on 2006-01-12
Thanx klepto I think that hack worked for me. I finally figured out what went wrong with the gxine plugin. Gxine stuck a plugin into my ~/.mozilla/plugins folder. The problem went away as soon as I removed the plugin.

---

