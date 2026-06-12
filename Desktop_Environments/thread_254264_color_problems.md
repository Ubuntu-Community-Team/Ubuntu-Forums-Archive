---
title: "color problems"
date: 2006-09-09
forum: Desktop Environments
---

### Post by SledgeHammer_999 on 2006-09-09
hi I installed ati's latest drivers. everythink works ok except one thing. when i play a video file(no matter what format) in totem-gstreamer the video acceleration is ok but the colors aren't. for example let's say we have a video which shows some people. the colors are changed in such a way that the people's skin looks pink or pale and similar changes are noticed for the whole picture(not just the people's skin).

I am wondering if this is caused by some other configuration(let's the X's configuration) and not from ati's drivers or is it the drivers? Anywayz can you help me?

Notes:
1.Before installing the drivers the video played fine, there was no color change but there was no acceleration either!!!
2.I am a ubuntu/linux newbie so don't get too technical
3.If you want some screenshots that show the problem feel free to ask me to post some.

I hope you can help me solve this otherwise I won't be doing much with ubuntu.

thanks in advance

---

### Post by vbgunz on 2006-09-24
I was just about to post about this *but* it seems no one has given you an answer in two weeks. How I solve this is to remove totem-gstreamer with apt-get and replace Totem with another player such as gxine...

```

sudo apt-get remove totem totem-gstreamer ubuntu-desktop
sudo apt-get install gxine

```

You'll have to reboot to see the changes. Don't worry about uninstalling Ubuntu-desktop, removing Ubuntu-desktop won't break a thing. Once you're done, you'll need to reboot. Once back in, fire up gxine > applications > sound & video > gxine and play a dvd or any supported video. Colors should be fine if not great this time around.

You might wish to check out system > preferences > removable drives and media if you wish upon inserting a dvd to have gxine automatically open it and play it. If none of this works for you, reverse the steps above in the code section like so to restore your system back to the state it was in before following my advice.

```

sudo apt-get install totem totem-gstreamer ubuntu-desktop
sudo apt-get remove gxine

```

I know it sucks for Totem to destroy all the colors the way it does now *but* fortunately  it isn't the end of the world. Good luck!

---

### Post by ogu on 2006-09-24
hmm yeah, same problem ... it seems the channels are inverted (i think it's red and blue).

I changed to totem-xine and it works, i even started using mplayer and VLC ... problem is, they can't play my MP4 videos so i still want to keep totem-gstreamer.

Sledge_Hammer, could you post some info about your system? we could find some common things here.

I have an ATi x1800 Mobility Card i think, i use the fglrx driver, it's a Dell E1505 laptop... I've had no other problem untill now though. Oh yeah, i've heard that using Xserver-xgl fixes this, but alas it takes way too much (way too much really) to load in my laptop so that's totally out of the question for me.

I haven't found a bug report for this, i'll do one.

---

### Post by SledgeHammer_999 on 2006-09-25
Thank god someone has noticed me. Anyway as I said [here](http://www.ubuntuforums.org/showpost.php?p=1536157&postcount=325) with xine the video plays fine but with gstreamer the colors are distorted. Red becomes blue for example. So i think this has something to do with gstreamer. and using xine or anything else is not a real solution because I WANT to use gstreamer.

so ogu the thing you said about the inverted channels might be true.

my specs:
X1800XL 256MB RAM
AMD x2 4200(dual core)
512MB RAM(soon it will be 1024 dual-channel!!!!)

---

### Post by vbgunz on 2006-09-25
I noticed my problem has gone away when uninstalling totem-gstreamer, totem, etc. I never thought of trying totem-xine. I'll try it and see how it pans out. ogu, if you made a bug report link us to it so we won't duplicate it. Thanks!

---

### Post by SledgeHammer_999 on 2006-09-25
vbgunz I think you haven't noticed one thing. Gxine uses xine. Totem-gstreamer uses gstreamer. Totem-xine uses xine. As as said above xine *works* fine with ATI drivers but gstreamer doesn't. "Your problem was gone" because you used xine to play the video. If you use gstreamer I think the problem will happen again.

---

### Post by vbgunz on 2006-09-25
Ahh, makes sense. So totem-gstreamer is just broken cause unlike you both I have an Nvidia card and experience the same distorted colors. Not sure if this makes any sense at all *but* if I do not uninstall totem-gstreamer, gxine colors are also corrupt... I hope this does get fixed soon :)

Please paste the bug link here so we can follow up!

---

### Post by SledgeHammer_999 on 2006-09-25
hmm it's pretty interesting that you have the same problem with the nvidia card. This makes me think that the problem lies in gstreamer and not in the drivers.

By the way gxine works fine for me eventhough I have installed tha totem-gstreamer. I hope this gets fixed pretty soon because I like gstreamer.

> Please paste the bug link here so we can follow up!
Are you refering to me?

---

### Post by vbgunz on 2006-09-25
Actually was referring to ogu about the bug link. I have this wierd problem where I never actually post an original bug. I always seem to get an email about *hey* this is posted under *aTermYouNeverThoughtOf* and it is sort of disappointing though at least the bugs getting fixed. I just need to get better with the bugtracker...

Well, at least in the short term the problem is solved :)

---

### Post by ogu on 2006-09-26
Ok, sorry for the delay, i broke my X server while playing with compiz but it's all back to normal now.

The bug is filed here:

[http://bugzilla.gnome.org/show_bug.cgi?id=357741](http://bugzilla.gnome.org/show_bug.cgi?id=357741)

please add more information as it comes, alas it's all i could gather.

---

### Post by SledgeHammer_999 on 2006-09-26
hey ogu you forgot to mention on your bug report that this happens only when we install ATI drivers. If I use ubuntu's defaults drivers then there is no problem. plz update your bug report because I don't want to register.

---

### Post by vbgunz on 2006-09-26
Well for me, I get the distorted colors with or without the binary Nvidia driver and as long as totem-gstreamer is installed, Gxine itself will play with distorted colors with or without the Nvidia driver. I hope the devs look into this soon.

---

### Post by vbgunz on 2006-09-26
I've found a solution that works for me. I can use Totem and all colors are fine. I just went into Totem preferences > display and reset to defaults. Then, lowered the hue to zero. This made the colors come up just right. Does this work for you?

---

### Post by SledgeHammer_999 on 2006-09-26
well it doesn't work for me. the problem for me seems to be the red and blue channels.

---

### Post by vbgunz on 2006-09-26
Damn. It sucks to feel like something is just broken. Maybe sign up with the bugtracker and let them know. It should at least show them that there are more people out there with this problem and that it is indeed a problem. Registration is dumb quick and you can help confirm it at [http://bugzilla.gnome.org/show_bug.cgi?id=357741](http://bugzilla.gnome.org/show_bug.cgi?id=357741)

Good luck!, I hope it does get solved soon enough. It should just work out of the box regardless of drivers.

---

### Post by Ohmz on 2006-10-08
I was having this same problem as well. I'm using a nVidia card though, with their drivers. Before I was able to play in color off the x11 driver, but get the distorted colors using xv.

After reading the post a few up I tried changing the Hue in Totem all the way down. This made it worse. Then I turned it all the way up and all the colors returned perfectly. After that, I was able to play video in color on all my media players: Totem, MPlayer, VLC, and Gxine.

Thanks for you help, good luck guys!

---

### Post by SledgeHammer_999 on 2006-10-08
Well if you follow the link for the bug report above and read it then you will realize that you are one lucky guy. This solution works for nVidia cards, but it doesn't work for ATI.

---

### Post by vbgunz on 2006-10-09
Hey SledgeHammer_999, hopefully this'll be fixed for Edgy Eft. Colors are good for me right out of the box. Only about 2 more weeks till release :)

---

### Post by SledgeHammer_999 on 2006-10-09
2 weeks for edgy?!?! I thought it would be released December/January.

---

### Post by cyran on 2007-05-13
I have Feisty and I have the exact same problem -- the red and blue channels are getting switched. But it didn't always have this problem; I have no idea what changed though.

Changing Hue to minimum or maximum makes two-thirds of the colors right again, except then the green channel ends up becoming magenta or something.

EDIT: The workaround posted [here]("http://bugzilla.gnome.org/show_bug.cgi?id=357741#c33") genuinely works completely! It looks like this is a driver issue; with both ATI and NVidia, all depending on which version you have.

---

### Post by SledgeHammer_999 on 2007-05-14
I confirm that the workaround works both in Egdy and Feisty.

> I have Feisty and I have the exact same problem -- the red and blue channels are getting switched. But it didn't always have this problem; I have no idea what changed though.

Well the colors are fine if you don't use Ati's driver. But with the open-source driver the videos lool like crap. So you have to install the proprietary driver. 

The thinks that bugs me the most is why nearly noone so far hasn't mentioned anything. Are they using only Nvidia cards? Or don't they use gstreamer?

---

