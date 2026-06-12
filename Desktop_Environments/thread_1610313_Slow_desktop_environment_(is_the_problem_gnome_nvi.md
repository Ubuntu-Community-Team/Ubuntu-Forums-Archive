---
title: "Slow desktop environment (is the problem gnome? nvidia? other?)"
date: 2010-10-31
forum: Desktop Environments
---

### Post by Hashiru on 2010-10-31
Hi Everyone,

I'm using ubuntu since a month and I have fallen in love with it. I decided to change my desktop PCs to Ubuntu too. I didn't notice any difference until I started Quadrapassel (tetris). It's lagging a LOT. It takes about 1,5 seconds to shift a block left or right.
I've been searching for three days non-stop and I haven't found a solution yet.

I suspect it might have to do something with GNOME or NVIDIA. With or without installed proprietary drivers from NVIDIA, the applications will lag. OpenOffice does not lag however.

I have tried Kubuntu, and kubuntu doesn't show any lag at all, except for some visual effects. I turned them off and didn't notice any slowness anywhere.

1. The solutions I tried are installing NVIDIA drivers downloaded from the NVIDIA website.
([http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368))
2. Install an older version of Ubuntu.
3. Try another desktop PC (same problem)
4. Try another laptop (that works fine)
5. Install kubuntu (works fine)
6. Install kde arch linux (Don't know how I did it, but it worked)

I don't know how to search the graphics card in ubuntu, but I believe both desktops use an nvidia graphics card. I believe it has something to do with the hardware configuration.
I would like to provide more information if needed. I hope someone can help me solve this problem.

Thank you.

---

### Post by P4man on 2010-10-31
Well.. lets start by finding out what hardware you have. Can you post the output of
```

lspci
```

or attach the output of lshw (redirect it to a file with 

```
lshw > myhardware.txt
```

Might be useful if you did that for both problematic machines, see what they have in common.

Another thing you can do to help isolate the cause is finding a bit more apps that do or dont cause unreasonable slowdowns. Things like flash/youtube, playing movies, playing more taxing games (extreme tux racer is my favourite test :p).

Last thought; open system monitor and see if CPU and memory usage are normal if you arent running anything intensive.

---

### Post by Bobhuber on 2010-10-31
Need your hardware and memory specs. Memory + 64 bit + 10.04 + nvidia = Speed
There are also a few tweaks that will improve performance depending on your configuration.

---

### Post by Hashiru on 2010-11-02
Hi everyone,

Thank you for the replies. I didn't expect my post to be read at all. Awesome!

Anyway, this is the information of the first desktop I tested. I hope I did it right. I will upload the other desktop in a minute.

Thanks.

---

### Post by P4man on 2010-11-02
Looks like the common factor is the geforce5 FX. Are you using the restricted nvidia drivers?

---

### Post by Bobhuber on 2010-11-02
Looks like its a game related bug ?? .Your not the only person that has noted the speed problem.
Take a look at this post.
[http://ubuntuforums.org/showthread.php?t=1418305](http://ubuntuforums.org/showthread.php?t=1418305)

---

### Post by Hashiru on 2010-11-03
Thank you for the replies.
 
@P4man
Yes, I've tried two versions. Both proprietary drivers I could select in the "search drivers" tool. Both versions won't solve the lag, even better, it increases the lag. The increase in lag is most likely caused by a higher resolution after the drivers are installed.
 
@Bobhuber
I have looked at the thread and it seems to have a lot in common. I've tested other games and they show lag too. I think it has something to do with Gnome and Nvidia together. I've tested ubuntu 10.10 and 10.04 (different gnome version) and both show lag. I haven't tested the 64 bit version of ubuntu yet, I will do that this weekend. 
 
Is it a good test to disconnect the video card and see if it still shows lag? The internal videocard on the motherboard should take over I believe.

---

### Post by P4man on 2010-11-03
I cant really imagine the opensource nouveau drivers sharing a bug with nvidia restricted drivers. These share zero lines of code.

If you have onboard video, feel free to test that (make sure you disable the restricted driver before removing the card).

---

### Post by Hashiru on 2010-11-04
Okay, I have tried the onboard video card, turns out I don't have one. It was my previous computer that had one though.

I've had no luck in fixing my problem yet. I hope there are still some things left to try.

---

### Post by P4man on 2010-11-04
what happens when you deactivate the restricted driver, so you get nouveau back? Or if you test livecd which also uses nouveau. Does that work properly?

---

### Post by P4man on 2010-11-04
BTW, I only just noticed you followed a howto from 2005 (!) to install the nvidia drivers. Im shocked that would work at all. Its so simple to install nvidia drivers, just go to system | administration | additional drivers and activate the nvidia drivers. For your card that would be the 173 series.

---

### Post by Hashiru on 2010-11-04
With or without the restricted drivers I have the same problem. The only difference with restricted drivers is that I can set a higher resolution.

The live cd/usb has the same problem.

When I start browsing with firefox, start a download and start the software manager, ubuntu almost freezes. I even managed to make it freeze completely for 10 minutes. I guess there might be more then just Nvidia.

@P
I haven't tried the 173 series yet, I'll try them today. I expect to give my reaction in within 24 hours.

---

### Post by P4man on 2010-11-04
173 is the only correct one for your card, but if it also happens in a live session, which uses nouveau, then it must be something else. Unless you actually didnt install the nvidia drivers properly and you have always been using nouveau.

Can you attach the output of 

```
dmesg
```

and the contents of /var/log/syslog  and /var/log/Xorg.0.log ?

---

### Post by Hashiru on 2010-11-05
Hi again, I've tried both. Just nouveau and only the 173 restricted driver.

Both show the same problem still. I've added a screenshot that I installed the 173 version.

Now i'm just running nouveau, because it seems to work a little bit better then 173.
I've added the contents of the command and files you requested. Thanks for helping me out.

Another question:
should /etc/X11/xorg.conf be an empty file? Because it is.

Thanks

---

### Post by P4man on 2010-11-05
I think you attached the wrong file for dmesg, but thats okay, whats relevant there is probably in syslog too.

xorg.conf is empty by default these days, thats normal. If you are using the nvidia drivers, you may want to generate one by running

```
sudo nvidia-xconf
```

Be sure to remove that if you revert to nouveau.

Anyway your log looks rather normal to me. Only one thing caught my eye; first there is a tv tuner in there apparently. Have you tried disabling or removing that? I vaguely recall an issue with some tuners. Of course if only one of your machines has such tuner (which I suspect) then its not too likely a cause either.

Other than that, I really dont understand whats going on. The only common factor between your two machines is the nvidia card, but the problem occurs with totally different drivers, that pretty much excludes it again as a cause.

---

