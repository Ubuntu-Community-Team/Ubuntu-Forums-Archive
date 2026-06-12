---
title: "Excellent OS, Good Install - media player???"
date: 2005-04-15
forum: Desktop Environments
---

### Post by lmellen on 2005-04-15
:) I'm very pleased with Kubuntu, this is a excellent system. What has me curious is to whether 
or not the forum advice for Ubuntu is good for Kubuntu. I think in reference to KDE i'm not sure.
For example I still need to install Realplayer, mplayer, helixplayer or whatever Kubuntu uses.
Some of the forums responses are for Gnome installation,not good for KDE. I do need a realplayer type video. Now I can use apt-get and see what happens, I just don't want to make a mess out of everything! Any advice on a media player, or install advice?  
                                                                                  Thanks -- Larry

---

### Post by philipacamaniac on 2005-04-15
Kaffeine is a great media player. If you install the win32 codec pack from [http://www1.mplayerhq.hu/homepage/design7/codecs.html](http://www1.mplayerhq.hu/homepage/design7/codecs.html)
 then Kaffeine should play a gripload of WMA/WMV/RealPlayer/Quicktime formats. 

If you add this line to your /etc/apt/sources.list

```
deb ftp://ftp.nerim.net/debian-marillat/ stable main
``` 
then you can just 

apt-get update
apt get install w32codecs

---

### Post by lmellen on 2005-04-15
Thanks philipacamaniac, I've already installed the sources.list.
But do I have to download the codecs first, and where do I put them, or will apt-get install them?
Then where do I get Kaffiene, apt-get that also?
 Will Kaffiene work with Firefox?
                                         Thanks for the reply -- Larry :)

---

### Post by philipacamaniac on 2005-04-15
Kubuntu comes with Kaffeine; its the default media player. Kaffeine + Firefox, I don't know yet, but I am using Firefox as my browser. I know that Kaffeine can play embedded into Konqueror pages.

You have a choice, either download the codecs manually, or apt-get install them. You don't need to do both.

---

### Post by roffles on 2005-04-15
[QUOTE=philipacamaniac]Kubuntu comes with Kaffeine; its the default media player. Kaffeine + Firefox, I don't know yet, but I am using Firefox as my browser. I know that Kaffeine can play embedded into Konqueror pages.

You have a choice, either download the codecs manually, or apt-get install them. You don't need to do both.[/QUOTE]

There is a kaffeine plugin for mozilla, I believe its called kaffeine-mozilla (surprise! :) ) and you can get it by using apt-get

---

### Post by !nkubus on 2005-04-15
[QUOTE=roffles]There is a kaffeine plugin for mozilla, I believe its called kaffeine-mozilla (surprise! :) ) and you can get it by using apt-get[/QUOTE]

Yup it works fine but it's not embedded, i saw some good alternatives , like totem-mozilla :) wich use the same back end as kaffeine but jsute diferent interface (gtk)

search forum there is a good tutorial about getting totem embedded in mozilla :)


hope this helps :)

---

### Post by lmellen on 2005-04-15
:-x Thanks for the replies, but I couldn't get ANYTHING working. I tried w32codecs, kaffiene-mozilla, helix-player, mplayer--none worked, Konqueror or Firefox. The only place I use it is in on- line newspapers, they want RealPlayer
or Windows Media Player. I'll try to install RealPlayer tomorrow. Thanks for the replies. Larry :) 

?? What is totem, like RealPlayer or Quicktime??

---

### Post by philipacamaniac on 2005-04-16
totem is another xine frontend, so basically a GNOME version of Kaffeine. It plays all the same formats as Kaffeine.

If you are trying to get streaming video from a news site (like MSNBC), it will be difficult because they have scripting mechanisms that make sure you have the "required" official media players (RealPlayer, Windows Media, or Quicktime). You might try to find the actual URL of the stream and open it directly with your media player. If you don't like that, please complain to the websites and tell them to support open standards.

---

### Post by lmellen on 2005-04-16
:smile: Hi philipacamaniac, I have a T-23 installed with Arch and all the video works like a charm. I put Arch on my desktop, same problem as here, almost nothing works. On Kubuntu, on my T-22 almost nothing works. I have flashplayer working well on firefox, can't get it working at all on Konqueror. Basically all I need it for is the NY Times, they want Realplayer. It's not that big a deal, I just like to have things working. There is a good thread on installing realplaer, I'll try that later. -- Thanks for the replies -- Larry :)

---

