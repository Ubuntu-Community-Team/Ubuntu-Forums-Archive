---
title: "Flash Player"
date: 2009-04-09
forum: General Help
---

### Post by kibster on 2009-04-09
hi..Boy am I glad someone is here to answer some of my questions..Or else I would be lost..

It seems as though i need a flash player for viewing CNN and YOUTUBE videos
A Pop up comes up and ask me what type of itsllalation I want but I don't know which ones to pick. If I did choose one package to install would it be that bad. Wouldnt it just not work or would it crash or damage the system. 

So Which one to install or shoould I use the software resorces under Administration. And which one should I choose.

Thanks again.

Russ

PS Theres also some way of closing out a post after its been answered so as to not have people answering a post once its been answered. Where is that at..I looked and didnt see where it was at...

---

### Post by 3Miro on 2009-04-09
Go to Applications/Add remove programs and select all available software. Then look for Ubuntu Restricted Extras and install it. It gives you the Sun version of Java, some codecs and Flash Player. You shoul dbe able to view Youtube and CNN afterwards.

For you tube itself, you can use the totem player (Applications -> Sound and Video -> Movie Player)

---

### Post by 3rdalbum on 2009-04-09
The choices given to you are safe and easily reversable.

The reason why you are given the choice is due to the gap between open source software and proprietary software. People who use Linux often don't like the thought of proprietary software. Some tolerate it, others absolutely refuse to use it.

Rather than just automatically installing the proprietary Adobe Flash Player, Ubuntu gives you the choice: Use a Flash player that will work very well but is closed-source, with all that entails, or use a Flash player that is open-source but does not yet have all the features and support of the official proprietary player.

If you don't care terribly much about the philosophy and ethics behind using open-source, then Adobe Flash Player is what you want.

If you've already chosen to install "gnash" or "swfdec", then you can remove them in Synaptic Package Manager and install the "flashplugin-nonfree" package to get the official Adobe Flash Player.

---

