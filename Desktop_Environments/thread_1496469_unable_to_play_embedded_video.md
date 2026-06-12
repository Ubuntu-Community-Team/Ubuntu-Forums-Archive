---
title: "unable to play embedded video"
date: 2010-05-29
forum: Desktop Environments
---

### Post by manolomanolo on 2010-05-29
Cannot interact (play directly or open the related page on youtube and so) with embedded video on several pages, for example:
[http://www.meetup.com/Gli-amici-di-Beppe-Grillo-di-Napoli/messages/boards/thread/9182540](http://www.meetup.com/Gli-amici-di-Beppe-Grillo-di-Napoli/messages/boards/thread/9182540)

and this is the code of the embedded element

```

<object width="640" height="385"><param name="movie" value="http://www.youtube.com/v/7jtr7xMiAsU&color1=0xb1b1b1&color2=0xd0d0d0&hl=it_IT&feature=player_embedded&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowScriptAccess" value="always"></param><embed src="http://www.youtube.com/v/7jtr7xMiAsU&color1=0xb1b1b1&color2=0xd0d0d0&hl=it_IT&feature=player_embedded&fs=1" type="application/x-shockwave-flash" allowfullscreen="true" allowScriptAccess="always" width="640" height="385"></embed></object>

```

Moreover, please see the grey bar on the bottom of the screenshot. That bug presents when playing videos directly from YouTube too.

Running Firefox 3.6.3 on Ubuntu 10.04
flashplugin-installer 10.0.45.2ubuntu1

Any suggestion, please?
Thanks.

---

### Post by shaka_zulu on 2010-05-29
Did you try some other browser?

---

### Post by freacert on 2010-05-29
same problem here. upgraded yesterday to lucid, no video on youtube nor in firefox, opera, chrome. Amd and nvidia

---

### Post by shaka_zulu on 2010-05-29
Upgrade usually brings some problem and regular users should try to avoid it. Clean install should be matter of preferation.

---

### Post by manolomanolo on 2010-05-29
Same problem with *Chromium 5.0.342.9 (43360) Ubuntu*
My ubuntu 10.04 is fresh installed.

---

### Post by freacert on 2010-05-29
fixed for opera by installing through synaptic the "flashplugin-nonfree
Adobe Flash Player plugin installer (transitional package)"
firefox and chrome still not working.

---

### Post by shaka_zulu on 2010-05-29
Can you play youtube or Vimeo normally or not?

---

### Post by WinRiddance on 2010-05-29
Try and follow the directions on this page ... ignore the $ symbol at the beginning of the code. Don't pick and choose, just start at the top and follow the steps listed there:

[http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html](http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html)

That's supposed to enable all of your DVD, MP3, and other Video options in Lucid.

---

### Post by freacert on 2010-05-29
Firefox youtube now working as well. 
Uninstalled the "mozilla-plugin-gnash
free SWF movie player - Plugin for Mozilla and derivatives" and now firefox uses
```
about:plugins
```
Archivo:  libflashplayer.soVersión:   Shockwave Flash 10.0 r32

Google chrome still not working, but as long as firefox is fine, i am happy with her.

Archivo:  libflashplayer.soVersión:   Shockwave Flash 10.0 r32
Vimeo works fine aswell.

---

### Post by shaka_zulu on 2010-05-29
Put [SOLVED] in the tread name ;)

---

### Post by freacert on 2010-05-29
for me, but maybe not for the tread starter manolomanolo :-P

---

### Post by lovinglinux on 2010-05-29
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by manolomanolo on 2010-05-31
> **WinRiddance said:**
> Try and follow the directions on this page ... ignore the $ symbol at the beginning of the code. Don't pick and choose, just start at the top and follow the steps listed there:

[http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html](http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html)

That's supposed to enable all of your DVD, MP3, and other Video options in Lucid.

This did not worked. I followed the instructions, installed everithing (except w32codecs which was not found) and restarted Firefox but I cannot still see embedded videos

---

### Post by manolomanolo on 2010-05-31
> **lovinglinux said:**
> Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

that fu*kin works!!! Thank you!!!!

---

### Post by lovinglinux on 2010-05-31
> **manolomanolo said:**
> that fu*kin works!!! Thank you!!!!

:) You are welcome.

---

### Post by manolomanolo on 2010-05-31
thank you lovinglinux...
A similar tool for java would rock too!!!

Have you planned to make something similar for java too?

---

### Post by lovinglinux on 2010-05-31
> **manolomanolo said:**
> thank you lovinglinux...
A similar tool for java would rock too!!!

Have you planned to make something similar for java too?

I haven't thought about that, but it could be done. I did this one because of the amount of threads asking for help. Although there are also threads with java issues,  is not like flash, which has dozens of threads every week. I will think about it anyway.

---

### Post by luceerose on 2010-07-08
> **WinRiddance said:**
> Try and follow the directions on this page ... ignore the $ symbol at the beginning of the code. Don't pick and choose, just start at the top and follow the steps listed there:

[http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html](http://www.ubuntu.steinfein.org/ztip01_multimediamp3.html)

That's supposed to enable all of your DVD, MP3, and other Video options in Lucid.

The person who wrote that guide should have left out non-free-codecs & included ubuntu-restricted-extras instead.

---

