---
title: "xubuntu 14.04 netflix problems"
date: 2014-04-26
forum: Gaming &amp; Leisure
---

### Post by courtney2 on 2014-04-26
I feel like I'm beating a dead horse with this Netflix garbage, but, I need to get this working for my parents otherwise they'll probably put my head on a pike. 

So far, this has failed for me on anything Debian or Ubuntu based distros and Arch Linux, and for the past 6 months with no luck. I have Silverlight 5.1 installed and running, I did the tests, I installed User Agent Overrider plugin into Firefox (on this current laptop v28) and switched it to Windows/Firefox 26. All goes well until I get this message:

DRM error. Error code: N8156-6023. 

Not sure what the block is. On this laptop, I don't have flash installed yet. However, I did have flash on all the other computers I used in the past. What am I missing? Did I not put my soul in a jar and give it to the corporations willingly enough?

---

### Post by oldrocker99 on 2014-04-26
Your wine package is probably not the wine-compholio version, which is made to run Silverlight. There is another way:
[http://www.makeuseof.com/tag/easily-enable-silverlight-watch-netflix-linux/](http://www.makeuseof.com/tag/easily-enable-silverlight-watch-netflix-linux/)

See if that works.

---

### Post by SeijiSensei on 2014-04-26
Netflix works for me with pipelight and [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") sending the User-Agent string "Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0" to netflix.com.

You can use pipelight to install the Windows version of Flash instead of the Linux version, but I found that approach had [problems]("http://ubuntuforums.org/showthread.php?t=2217961") if I moved in and out of full-screen mode.  With the standard Linux version of Flash in Ubuntu, the problem doesn't arise.  According to that linked thread, the problem with the Windows Flash version might be an artifact of my ATI adapter with hardware acceleration enabled, but I haven't bothered to dig further into it.

---

### Post by courtney2 on 2014-05-02
I do have the wine-compholio version of wine installed, plus user agent overrider. Would it make a difference to use UAControl? I guess it's worth a shot. I'm not really interested in installing the Windows version of flash, seeing how people have success with the Linux version

---

### Post by oldrocker99 on 2014-05-02
> **SeijiSensei said:**
> Netflix works for me with pipelight and [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") sending the User-Agent string "Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0" to netflix.com.

You can use pipelight to install the Windows version of Flash instead of the Linux version, but I found that approach had [problems]("http://ubuntuforums.org/showthread.php?t=2217961") if I moved in and out of full-screen mode.  With the standard Linux version of Flash in Ubuntu, the problem doesn't arise.  According to that linked thread, the problem with the Windows Flash version might be an artifact of my ATI adapter with hardware acceleration enabled, but I haven't bothered to dig further into it.

I followed this:[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html) and it worked perfectly. No more Windows Firefox!

---

### Post by courtney2 on 2014-05-28
Only thing I could get working was to do the Netflix Desktop. Nothing else worked. Marking as solved

---

### Post by cong06 on 2014-07-12
> **courtney2 said:**
> Only thing I could get working was to do the Netflix Desktop. Nothing else worked. Marking as solved


I also couldn't get it to work. I was previously using netflix-desktop, but I don't consider that a solution.

If someone manages to get pipelight working, I'd be interested.

Edit: I found my solution here: [http://askubuntu.com/questions/485689/piplight-not-working-on-netflix](http://askubuntu.com/questions/485689/piplight-not-working-on-netflix)

---

