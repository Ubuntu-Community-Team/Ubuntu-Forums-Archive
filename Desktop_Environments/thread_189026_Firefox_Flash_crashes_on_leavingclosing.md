---
title: "Firefox Flash crashes on leaving/closing"
date: 2006-06-04
forum: Desktop Environments
---

### Post by stoffe on 2006-06-04
Flash in Firefox crashes a lot, usually when trying to close the tab/window or when trying to navigate away from the page. It works well, with sound and all (even with other apps) etc, but just this one thing is really troublesome, as it brings down the whole app, with every open tab and possible downloads.

I've seen some tips for other types of crashes, which doesn't work for this, but I haven't found anything for this. Of course it's mainly a Macromedia problem coupled with the fact that plugins don't run in it's own space, but I wonder if there is any tips anyone have, or if there is a known version (older?) that doesn't have these issues.

It's quite possible that it's a sound issue, it doesn't seem to crash in Epiphany, which has no working sound... at all. For FX, I have the FIREFOX_DSP="aoss" hack enabled, so sound will work there. Anyone know of anything similar for Epiphany? Or if that is the problem, any *other* solution that really works for Fx?

Pretty much all flash seems to be affected, be it games or youtube videos. This is on 6.06, btw.

---

### Post by telperion on 2006-07-05
[QUOTE=stoffe]Flash in Firefox crashes a lot, usually when trying to close the tab/window or when trying to navigate away from the page. It works well, with sound and all (even with other apps) etc, but just this one thing is really troublesome, as it brings down the whole app, with every open tab and possible downloads.

I've seen some tips for other types of crashes, which doesn't work for this, but I haven't found anything for this. Of course it's mainly a Macromedia problem coupled with the fact that plugins don't run in it's own space, but I wonder if there is any tips anyone have, or if there is a known version (older?) that doesn't have these issues.

It's quite possible that it's a sound issue, it doesn't seem to crash in Epiphany, which has no working sound... at all. For FX, I have the FIREFOX_DSP="aoss" hack enabled, so sound will work there. Anyone know of anything similar for Epiphany? Or if that is the problem, any *other* solution that really works for Fx?

Pretty much all flash seems to be affected, be it games or youtube videos. This is on 6.06, btw.[/QUOTE]

Also for me 
FIREFOX_DSP="aoss" ok audio in flash but firefox crash when stop/exit.
No flash audio in Opera Epiphany.

---

### Post by Rashid584 on 2006-08-28
I'm having the same problem. Any ideas anyone??

-Rashid

---

### Post by stoffe on 2006-08-29
> **Rashid584 said:**
> I'm having the same problem. Any ideas anyone??

-Rashid

There is no way to fix it, you can either:
* wait for Flash 9 that is on the way, but possibly not for another 6 months
* not view flash at all
* use Crossover Office (or probably Wine) to install Windows version of Flash, or even Windows version of Firefox
* or wait for Gnash, that might be usable... oh, any decade now

None of these solutions are satisfactory, but the problem is the binary unmaintained blob that Macromedia once dropped on us. Adobe is fixing that now, but it will take a while, though progress is good: see [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

---

### Post by Rashid584 on 2006-08-29
I guess ima have to wait for Adobe to release Flash 9 for Linux....

-Rashid

---

### Post by jetpeach on 2006-08-29
Apparently, you can install Flash 9 using Wine, but it's certainly not ideal.
[http://digg.com/linux_unix/Flash_Player_9_on_Linux](http://digg.com/linux_unix/Flash_Player_9_on_Linux) (the digg article on it with some comments) and the article itself
[http://www.howtoforge.com/ubuntu_flash_player9](http://www.howtoforge.com/ubuntu_flash_player9)

I also have this problem, firefox crashing if I use aoss... really looking forward to Adobe putting out more linux products, Flash is definitely in the works and I also hope the full version of Acrobat sometime (reader is good for many but not for my purposes...)

---

### Post by hornett on 2007-01-06
Well, Flash 9 is out, and I still have exactly the same problem :(

```
File name: libflashplayer.so
Shockwave Flash 9.0 d78
```

Audio works perfectly, but Firefox still crashes when leaving pages with flash.

:confused: :confused: :confused: 

Anybody have any solutions for this now?

---

### Post by ayu on 2007-10-14
Was this ever solved?  It crashes for me around 20% of the time when I close a tab with a flash video still playing. 
Shockwave Flash 9.0 r48, Firefox 2.0.0.6
And is there really no way to kill just the plugin?  I recall that Adobe reader can be killed (but that was windows) and save firefox.

Thanks!

---

### Post by ayu on 2008-02-02
Ok it is a bit better now with Gutsy, but still crashes about once a week while closing a page with flash video.  Any ideas?

---

### Post by Sentientv2 on 2008-02-04
I'm also experiencing a crash (to a black screen, forgot the console text, then to login), and it appears to be when I'm closing a tab with playing flash content, or perhaps just flash content in general.

I am using npwrapper.libflashplayer.so (supposedly). I apologize for my lack of knowledge. I'm quite new to Ubuntu and linux in general. I had to do a bit of tweaking to play youtube videos and such.

Here's the rest of my info:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

I have a amd64 machine as well. Thanks.

---

### Post by hollowhead on 2008-02-04
I had this problem. I'd watched a video and went back one page to earlier selection of videos on youtube.  I assume I'm using an up todate flash lib since the installation is recent.  I went to var/crash and used apport to send a bug report in the hope someone will sort it out.  The sound works perfectly (at least until firefox crashes...).

By the way I cannot see why we need a full version of acrobat when reader reads files and oO creates them perfectly.....

---

### Post by manimal347 on 2008-02-04
I use Debian Etch and the latest Ubuntu base-install, and I experience the same issues, even when using the Iceweasel fork. Actually, since I started using Linux back when 6.06 was the latest, Flash sites would cause Firefox/Iceweasel to become a runaway process that had to be killed at the terminal.

Flash is usually the culprit, but in general, Firefox seems to be a bit unreliable under Linux. I have better luck with Epiphany; maybe the Firefox source trunk isn't the most stable? If so, though, I'd imagine the Iceweasel packages would try and rectify this as that browser can have upstream patches.

---

