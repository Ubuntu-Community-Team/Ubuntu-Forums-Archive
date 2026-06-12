---
title: "Installing Dell Digital JukeBox to ubuntu."
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by beanman25 on 2007-06-07
I have a 20gb Dell Digital JukeBox. What process would I go through to install it on ubuntu? would it just detect it as drive, or would i have to install drivers? I havent tried anything yet, I figured it would be better to ask the pros first.

---

### Post by kill4killin on 2007-06-07
If my guess is correct you probably don't need drivers for it. Ubuntu is pretty good about plug and play on most things with the exception of ipods.

If you are going to play MP3s on it though you need to get the mp3 codecs and such.
The easiest way to do that is to go get yourself a program called Automatix and use that to get the codecs and drivers for audio and video stuff.

To get automatix just do :
```
sudo apt-get install automatix
```

and then just open the program by going to Applications > System Tools > Automatix. Once there go under "Codecs and Plugins" and select AUD-DVD Codecs, Flash Player, Mplayer and FF Plugin and Multimedia Codecs and you should be pretty much set after you install those to tackle just about any media file you can get.

Let me know if you are unable to download automatix because you may need to add the repository to your sources.list file which isn't difficult to do, but I just can't remember if it is in the regular sources.list file or not.

---

### Post by PriceChild on 2007-06-08
The official stance of ubuntu forums on 3rd party helper scripts: [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

There is NO need to install automatix. Ubuntu will help you install codecs you need using wizards, or you can read [uwiki]RestrictedFormats[/uwiki]

---

### Post by fjgaude on 2007-06-08
They may not be a need to install Automatix but it sure is better than anything else I know of to get everything working in the audio/video arena. I've used it from 6.06 and it has never failed me or anyone else of which I know. The group does a superb job of script writing, just as good as any within the Linux OS proper.

frank

---

### Post by johnficca on 2007-06-08
I'm a big fan of Automatix, for a noobie I think its prefect. If you are new to Linux the last thing you want to do is type geek in a terminal to install something. If someone is new to Linux never show them how to do something in a terminal, it will make them hate Linux.

---

### Post by fjgaude on 2007-06-08
I wonder if PriceChild can tell us why Michael Dell has Automatix on his personal notebook computer?

frank

---

### Post by PriceChild on 2007-06-08
There is no need to go out of your way onto the internet to find extra software to install other software.

You can do "applications > add remove" to do most of the software offered by automatix.

As for codecs, totem/kde apps will guide you through installing them. But anyway, we're offtopic.

---

