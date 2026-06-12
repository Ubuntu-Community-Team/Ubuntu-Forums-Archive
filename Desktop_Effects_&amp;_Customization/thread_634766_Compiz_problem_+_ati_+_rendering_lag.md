---
title: "Compiz problem + ati + rendering lag"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by dbzsephiroth on 2007-12-08
Ok yes i know there have been a tonne of Compiz howto's and such but none help me out now.

I own a toshiba Satellite a200 with the following specs.

Ubuntu Gutsy
2.0Ghz core 2 duo centrino
2 Gb of ram
320 gig Hdd

and most importantly...

ATI redeon mobile 2600HD 512mb Graphics card


I was quiet surprised to get Compiz working at all with this Gfx card seeing all the other posts on how to do it....but i managed to get it working quiet easily.

Theres a new Driver out by ati called the Catalyst 7.11 display driver found [Here]("http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html")...well acutally its not new, its been out since November so i was surprised to see that none of the helpers on this forums and outside use this directly.


Anyway I did get compiz to work and its great that it does but theres a serious problem. Im probably only getting about 5fps with it running. The really odd thing is that it goes up after extended use, say about 20 mins or so.

Beryl running on my other machine with a 6600 GeForce card renders faster then this! Needless to say that this is annoying me greatly.

So what can i do to improve the speed?

In the mean time im going to try reinstall the driver because catalyst is telling me my driver is not functioning properly.

Thanks guys
Yamashita Masato

---

### Post by dbzsephiroth on 2007-12-08
HAH! I think i know y now.

Just because fglrx is in the xorg.conf file doesnt mean that its acutally using it.

fglrxinfo fails (and when running it on a gnome-terminal acutally restarts gdm) i found out that its bloody using mesa.....


Ill see if i can find out how to stop it from doing that


Keep u guys posted on progress

---

### Post by dbzsephiroth on 2007-12-08
Ok shweet i got it working,

I followed these instructions almost to the letter accept for one bit.....[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

The only bit i didnt get was:

```


Now make this run before gdm (which starts with secuence number 13)

[CODE]sudo update-rc.d ati-module-fix defaults 12
```

It is possible that gdm sequence namber is diffrent. To find gdm sequence number:

```
ls /etc/rc2.d/
```

And substitude 12 in the pervious command with gdm sequence number - 1
[/CODE]

Ok apon writing this i think i understand what it wants now, but still its not that very clear at first so if anyone can edit that to a more understandable version would help alot of ppl. Basicly just change the wording and add an explination as to what you are supposed to be looking for.


BUT.....there is still one more problem....


Any application that requires full screen will reboot gdm (screen saver included), and some other small errors regarding desktop rendering, so any help here will me much appreciated seeing as i think ive hit my limit of research and implementation that i can handle.

---

