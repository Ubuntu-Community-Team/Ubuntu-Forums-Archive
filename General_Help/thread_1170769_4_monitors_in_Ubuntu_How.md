---
title: "4 monitors in Ubuntu? How?"
date: 2009-05-26
forum: General Help
---

### Post by PsychedelicWonders on 2009-05-26
I am trying to set up a system with 4 monitors. 
 
3 - 19" Dell LCD's
1 - 46" Samsung LCD
 
Video cards:
 
Asus 9600 GT
Asus 9800 GT
 
I am not having any luck 
 
I just ran back through this walk-thru:
 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
 
But it doesnt say how to get Nvidia X Server Settings to "see" the 2nd video card/2 other monitors?
 
Ive been reading some things about editing the x.config and I think something like this is whats needed:
 
> :
Nvidia/ATI boards? First see if the NVIdia Xserver Settings utility (or the ATI equivalent) do this for you. You have to log as root or it won't be able to change the xorg.conf file.
 
By hand:
 
If your monitors are equal you already have the configuration in xorg.conf, just replicate the "Monitor" section and give a different Identifier to each, as in "Monitor[0]", Monitor[1], etc.
 
You'll have to do the same with the "Device" section, differentiating the boards by Identification ("Card0, "Card1", etc.) and the BusID. That's the tricky part, you'll have to search a bit for how to do it for boards with two video outputs, I've only used single boards. Probably the Hardware info module in Yast will show you the BusId for each video.
 
And again with the "Screen" section, where you "attach" each monitor to it's corresponding card.
 
Lastly you have to edit the "ServerLayout", which is where the configuration you want is actually activated, all previous sections being descriptive only. For example, if you had this line in it:
 
Screen "Screen[0]"
 
it could change to:
 
Screen 0 "Screen[0]" 0 0
Screen 1 "Screen[1]" RightOf "Screen0"
Screen 2 "Screen[2]" Above "Screen0"
Screen 3 "Screen[3]" RightOf "Screen2"
 
Then make sure not to run sax2 again, or at least backup your xorg.conf file before you do.
 
It's been a while since I did this, so you'll certainly find more up-to-date ways. Do search OpenSUSE's How-to site. 
Or do I just need to install the driver or something?
 
This guy said he got it, but I dont think its for Ubuntu, look at his x.config
 
[[COLOR=#444444]http://forums.opensuse.org/install-b...ml#post1900785[/COLOR]]("http://forums.opensuse.org/install-b...ml#post1900785")

---

### Post by PsychedelicWonders on 2009-05-27
bump

---

### Post by LowSky on 2009-05-27
[d2globalinc ]("http://ubuntuforums.org/member.php?u=640976")is a member hear who posted video on you tube running 6 monitors but he used the 3 of the same video cards, so he would be the guy to talk to, try sending him a PM

youtube video [http://www.youtube.com/watch?v=c1TOAXAbOAI](http://www.youtube.com/watch?v=c1TOAXAbOAI)

EDIT:he posted some info here too 
[http://ubuntuforums.org/showthread.php?t=884161&highlight=d2globalinc](http://ubuntuforums.org/showthread.php?t=884161&highlight=d2globalinc)

---

### Post by PsychedelicWonders on 2009-06-14
Thanks, I am going to jump into that thread to hopefully get this up and working once and for all.

---

