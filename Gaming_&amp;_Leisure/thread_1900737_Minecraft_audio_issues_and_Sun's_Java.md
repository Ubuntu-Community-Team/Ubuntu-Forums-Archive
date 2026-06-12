---
title: "Minecraft: audio issues and Sun's Java"
date: 2011-12-27
forum: Gaming &amp; Leisure
---

### Post by Tsirist on 2011-12-27
I'm pretty new to Ubuntu (as in, this is day two) and while I loved it initially I'm growing more and more tired with it as I fail to find solutions to problems that I just don't understand. This is one of them. This period will pass with time, right?

Everything in Minecraft works fine, but the audio is choppy and puffy, if that makes sense. The sounds cut themselves off early before starting again and I get error files in my Home location when running JREs 6 and 7. I've also taken the time to try updated LWJGL files and the one normally used with Minecraft.

I plan on trying to download JRE 7 from Sun and using it with Minecraft as I've seen people refer to this version as the intended iteration for use with the game. I've downloaded the tar.gz file and extracted it (appears to do the same thing as the fancy command lines that I'm still not used to :( ) but now I've got a floating jre1.7.0_02 folder without really knowing what to do with it.

Any ideas? I'm not sure I understand tar and tar.gz files yet. Am I doin' it right?

And when will I begin to instinctively know when to use sudo commands and such? Ubuntu is a strange transition! :)

---

### Post by ergo-proxy on 2011-12-27
Check this tutorial:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Tsirist on 2011-12-27
> **ergo-proxy said:**
> Check this tutorial:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

That worked great, thanks. Hadn't heard of .bin files being associated with installations on Ubuntu. Do they simply not make one for JRE 7? I'm guessing one could work it into the system with enough effort, right?

---

### Post by ergo-proxy on 2011-12-27
Well .bin means it's a binary file and that's all :) usually it's a generic package. One more thing, I faced a small problem launching minecraft (using java 1.7) actually it didn't launch because it required to export LD_LIBRARY_PATH like this:

export LD_LIBRARY_PATH=/opt/java/64/jre1.7.0_01/lib/amd64
and then java -jar minecraft.jar

but it might be already fixed in your jre version. Please mark the thread as solved.

---

