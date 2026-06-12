---
title: "HDTV output troubles"
date: 2009-04-26
forum: General Help
---

### Post by grenadier42 on 2009-04-26
Well, after a long period of Windows-ing, I returned to Ubuntu 9.04 (though mainly because SoulFU won't compile from source under Windows T_T).

I hooked up my computer to my 1080i HDTV via my Nvidia 8400GS TV-Out, and after some frustrating calisthenics, I managed to force the resolution to 1920x1080. Yay!

However, my delight was swiftly demolished when I noted that a bit of the outsides of the desktop (both the top and bottom task bars, and some of the sides) were outside of the viewing area.

Upon doing research into the problem, I discovered that the phenomenon was most likely due to something called overscan.

My best efforts to ward the evil overscan off (adding "TVOverscan = "1.0"" to Xorg.conf, for example) were unfortunately for naught.

Apparently, there is supposed to be an overscan slider in nvidia-settings, but when I go to the TV-0 section, the only slider I see is Digital Vibrance.

A bit of googling has yielded many threads, but zero solutions. If anyone could help with this problem, I will consider you... SUPER SPECIAL AWESOME. :)

Thanks in advance.

---

### Post by David Valentine on 2009-04-26
I'm trying to deal with the exact same issue.  I'll post back if I learn anything.

---

### Post by doas777 on 2009-04-26
I fought with the same issue on a pretty new standard def tv, using a geforce 8500 card. I've since realized the issue was the card itself, as i have seen many references to the phenoma, and I believe it is not on the HCL (haven't checked the incompatibility thread).  

also, i think if you are setting the overscan in your xorg, that you want to use less than 1.0 overscan. as i understand the issue, you already have too much overscan, and that is the problem. I could never get the setting to be applied though, if the nvidia-settings applet did not offer me an overscan control.

my geforce 7950GT works much better, and does include overscan support. it was a much better quality card as well (asus, instead of a cheap EVGA).

we just set up a media box running intrepid, that has a minimal underscan problem. we just ignore it, as it isn't that sever. we arn't using it as a TV though, but as a monitor itself via hdmi.

good luck, wish i had more constructive advice, except mabey to try xvidtune, or customize a modeline.

[http://ubuntuforums.org/showthread.php?t=851626](http://ubuntuforums.org/showthread.php?t=851626)

---

### Post by grenadier42 on 2009-04-26
> **doas777 said:**
> also, i think if you are setting the overscan in your xorg, that you want to use less than 1.0 overscan. as i understand the issue, you already have too much overscan, and that is the problem.

Err... I knew that. :)

Anyone else?

---

### Post by David Valentine on 2009-04-27
[These  instructions]("http://ubuntuforums.org/showthread.php?t=1003099") worked well for me.  It takes a bit of fiddling.  On page 4 of that thread I posted a shortcut that saved a bunch of iterations; I know the shortuct works on Mythbuntu 9.04 but I don't know about earlier versions.

---

### Post by grenadier42 on 2009-04-28
> **David Valentine said:**
> [These  instructions]("http://ubuntuforums.org/showthread.php?t=1003099") worked well for me.  It takes a bit of fiddling.  On page 4 of that thread I posted a shortcut that saved a bunch of iterations; I know the shortuct works on Mythbuntu 9.04 but I don't know about earlier versions.
Didn't work, but upon further research, I found out that custom modelines don't work when using component cables.

;_;

Anyone else have any ideas? I've pretty much given up trying to fix it. :P

---

