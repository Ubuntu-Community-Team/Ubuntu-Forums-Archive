---
title: "unable to start compiz-fushion: texture_from_pixmap support?"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by yang2iu on 2007-09-25
I've installed (and uninstalled) compiz-fushion on my feisty for quite a few times, but this time it doesn't seem to work: 

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system

What can I do to get this fixed?

---

### Post by raulferrandez on 2007-09-25
I have the same problem :-(

---

### Post by salsiccio on 2007-09-29
i' ve same problem.

I have ati x1950pro with driver from ati correctly installed.

---

### Post by abdelfattah on 2008-03-05
hello

a had the same problem with my X200M

i have seen a lot of tuorials and mnuals but without any result

so i decided to do it myself

i got the last ati driver from amd site

 i compiled it and then i installed compiz and emerald with apt-get

and thats all :)

---

### Post by larryfroot on 2008-03-05
You can get a more detailed picture by typing compiz --return into a terminal window. That way you can return back to the forum to find someone who really understands the output. I'm afraid I don't. But someone may have a much better idea of what the issue might be and so can give you some detailed advice.

What graphics card/chip are you using btw? 

Also if all else fails....I have found that typing SKIP_CHECKS=yes compiz   from a terminal window jollies things along a bit, but for gods sake, don't use that as sudo or running as root. ONLY do it as a user! And the default depth _may_ have to be changed to 16 in xorg.conf, so all in all not an ideal solution, but the only one I found for my probs with a mobile FireGL radeon 9000 and compiz. 

But anyways, good luck.

---

