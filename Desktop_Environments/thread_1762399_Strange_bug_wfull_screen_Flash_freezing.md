---
title: "Strange bug w/full screen Flash freezing"
date: 2011-05-19
forum: Desktop Environments
---

### Post by supercheetah on 2011-05-19
This bug is strange because it doesn't happen for me in Ubuntu (Gnome).

Whenever I try to watch a Flash video in full screen, the picture always freezes after a few seconds of play, and the only way for me to unfreeze it is to get out of full screen using the escape key.  I can put it back into full screen, but it always just freezes up again after a few seconds.

I figured out a strange work around for it though, but it's certainly not ideal.  I figured out that if I get the time pop-up (see attachment to see what I mean) to stay up, it doesn't freeze.

This happens in both Firefox and Chrome.  I was going to try this in Rekonq, but I can't seem to get Flash working in Rekonq.

Anyone know what's going on with this?

---

### Post by wildmanne39 on 2011-05-19
> **supercheetah said:**
> This bug is strange because it doesn't happen for me in Ubuntu (Gnome).

Whenever I try to watch a Flash video in full screen, the picture always freezes after a few seconds of play, and the only way for me to unfreeze it is to get out of full screen using the escape key.  I can put it back into full screen, but it always just freezes up again after a few seconds.

I figured out a strange work around for it though, but it's certainly not ideal.  I figured out that if I get the time pop-up (see attachment to see what I mean) to stay up, it doesn't freeze.

This happens in both Firefox and Chrome.  I was going to try this in Rekonq, but I can't seem to get Flash working in Rekonq.

Anyone know what's going on with this?
Hi, install flash aid it is an add-on in firefox, it fixes flash problems, let it run the script.

---

### Post by Copper Bezel on 2011-05-19
Odd. Chrome and Firefox use separate Flash plugins (as Chrome's is built in.) There are tweaks you can make to the system's Flash support (as used by Firefox and other browsers,) but ordinarily, Chrome's works out of the box, and I'd wonder if we're looking at a KWin problem here, instead. (I'm assuming that the controls freeze as well, not just the video.)

I don't know K, though.

---

### Post by supercheetah on 2011-05-19
Unfortunately, it seems Flash-aid is causing more problems.  Now after a few minutes everything begins flickering, and it doesn't stop after exiting full screen.

---

### Post by lovinglinux on 2011-05-20
> **Copper Bezel said:**
> Odd. Chrome and Firefox use separate Flash plugins (as Chrome's is built in.) There are tweaks you can make to the system's Flash support (as used by Firefox and other browsers,) but ordinarily, Chrome's works out of the box, and I'd wonder if we're looking at a KWin problem here, instead. (I'm assuming that the controls freeze as well, not just the video.)

I don't know K, though.

Only the 32bit version of Chrome has the bundled plugin.

> **supercheetah said:**
> Unfortunately, it seems Flash-aid is causing more problems.  Now after a few minutes everything begins flickering, and it doesn't stop after exiting full screen.

Which version of Flash-Aid are you using? Please get version 2.1.1 from [here]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"). Install it, then select "Help" from the extension menu, then select "Generate Report". Attach here the contents of the file *firefox-report.txt* that will be created in your Desktop.

About the blinking issues, you could try to disable hardware acceleration. Visit a YouTube video, right-click on the video, select "Settings", untick the hardware acceleration option.

---

### Post by crash123 on 2011-05-23
Was this ever solved? I've been having an extremely similar problem ever since the last flash plugin update, which I think was 3 or 4 days ago. If I open up a flash video into fullscreen (tried several different sites), it works from anywhere between a few seconds to a minute. After that, the video freezes, though the audio keeps going. Even pressing ESC won't get me out of the video. I'm forced to hit CTL+ALT+BACKSPACE to log out and log back in. 

I've had this problem with both chromium and firefox. I'll look into flashaid, but I'm basically a chromium user, so if it fixes something it will apply to chromium, too?

---

### Post by lovinglinux on 2011-05-23
> **crash123 said:**
> I've had this problem with both chromium and firefox. I'll look into flashaid, but I'm basically a chromium user, so if it fixes something it will apply to chromium, too?

Chromium will detect and use the plugin installed by Flash-Aid. Additionally, the performance tweaks the extension applies are system wide.

---

### Post by demilord on 2011-05-23
if you run 64 bit.. try the native flash 64 bit... and purge the 32bit version.. you can put it in the firefox plugin folder in your home directory it runs really smooth

---

### Post by supercheetah on 2011-05-24
Sorry for not responding in a while.  I've been a little busy.  No, this has not been resolved.  And I did install the latest version of Flash-Aid.  I even played around a bit with /etc/adobe/mms.cfg to no avail.  I just don't understand why it works in Ubuntu/Gnome/Compiz, and not in Kubuntu/KDE.  I am also using 32-bit Flash on 32-Bit (K)Ubuntu.

I even tried Flash-Aid under Ubuntu, and it works just fine as it always has.

---

### Post by Copper Bezel on 2011-05-24
Is it fair to assume that this is related to the window manager, then? (Try doing the same in Gnome after running kwin --replace.)

---

### Post by lovinglinux on 2011-05-24
> **Copper Bezel said:**
> Is it fair to assume that this is related to the window manager, then? (Try doing the same in Gnome after running kwin --replace.)

That's a good idea.

> **supercheetah said:**
> Sorry for not responding in a while.  I've been a little busy.  No, this has not been resolved.  And I did install the latest version of Flash-Aid.  I even played around a bit with /etc/adobe/mms.cfg to no avail.  I just don't understand why it works in Ubuntu/Gnome/Compiz, and not in Kubuntu/KDE.  I am also using 32-bit Flash on 32-Bit (K)Ubuntu.

I even tried Flash-Aid under Ubuntu, and it works just fine as it always has.

I use Kubuntu and don't have such problems. Could be an issue caused by the combination of Kwin and your graphics card.

It could also be some kde settings. I presume you have already tried a clean FF profile. So, try to create a new Kubuntu user, just for testing. If it works, then it is most likely to be some kde settings.

---

