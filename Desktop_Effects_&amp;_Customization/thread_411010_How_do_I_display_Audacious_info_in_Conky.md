---
title: "How do I display Audacious info in Conky?"
date: 2007-04-16
forum: Desktop Effects &amp; Customization
---

### Post by Gumper on 2007-04-16
I recently changed from using XMMS to Audacious and I would like to be able to display information from Audacious in my Conky. I'm able to do this with XMMS by using infopipe but I can't figure out how to do this with Audacious.

What is it that I may be missing? I'm using the variables as listed on the Conky website, but they just don't seem to work. Could it be a pluggin that I may be missing?

Thanks,

Gumper

---

### Post by Gumper on 2007-04-19
You mean there's no one that displays their Audacious info in Conky?

I'd really like to be able to do this. Just can't figure it out myself.

Gumper

---

### Post by notwen on 2007-04-19
Ditto, audacious info for conky would rool.

---

### Post by notwen on 2007-04-19
Here you go, did some digging and came across this.  Will be sure to modify my conyk when I get home, let me knwo fi you have any luck w/ it.  [Conky Variables]("http://conky.sourceforge.net/variables.html")

---

### Post by Gumper on 2007-04-19
Thanks but I've tried those variables in the past but they don't seem to work for me. I'm wondering what it is that I'm missing. I was thinking that it may be a plugin that's missing, but I can't find one. 

With XMMS I had to use infopipe to get it to work with Conky.

Gumper

---

### Post by notwen on 2007-04-22
True enough, I cant seem to find a solution for this either.  Nada is coming up when I google this situation.  I'll keep digging, let me know if you come across anything.

---

### Post by notwen on 2007-04-24
I have yet to do so, but you'll need to enable audacious during compiling.

---

### Post by notwen on 2007-04-24
Gumper: If you're still working on this check my post torwards the end of this [thread]("http://ubuntuforums.org/showthread.php?t=353362").  Hope it gets you what you need, good luck.

---

### Post by Gumper on 2007-04-24
Thanks notwen. So you have to compile conky with Audacious enabled. 
 I'm not sure if I'm brave enough to compile it myself.

---

### Post by notwen on 2007-04-24
Let me know if you have any issues and I'll be glad to help you as much as I am able, but to be honest the guys in #conky on freenode helped me out tremendously(ie. step by step) =p

---

### Post by freakavoid on 2007-04-24
how about audtool? I use it like this:

```
${if_running audacious}
${color black}AUD:${color #C0C8CD} ${exec audtool --current-song | cut -b-34}
${color #C0C8CD} ${exec audtool --current-song-bitrate-kbps} kbps * ${exec audtool --current-song-length}  ${execbar expr 100 \* $(audtool --current-song-output-length-seconds) \/ $(audtool --current-song-length-seconds)}
${color black}${hr 2}$endif
```

---

### Post by notwen on 2007-04-25
Not too sure on audtool, I just stuck w/ the simple variables given at conky's SourceForge page. Is that current setup working for you?

---

### Post by freakavoid on 2007-04-25
Audtool is actually a part of audacious. It comes with audacious and works perfectly well in conky, even with a progress bar! I say give it a try :)

---

### Post by notwen on 2007-04-25
This might be an easy way to avoid enabling audacious during conky compiling and let you stick w/ the basic 'sudo apt-get install conky' setup.  If anyone else is interested, here is a link for [audtool]("http://www.die.net/doc/linux/man/man1/audtool.1.html").  Is it installed w/ the audacious base or do we need audacious-dev installed through synaptic as well?

---

### Post by freakavoid on 2007-04-25
> **notwen said:**
> This might be an easy way to avoid enabling audacious during conky compiling and let you stick w/ the basic 'sudo apt-get install conky' setup.  If anyone else is interested, here is a link for [audtool]("http://www.die.net/doc/linux/man/man1/audtool.1.html").  Is it installed w/ the audacious base or do we need audacious-dev installed through synaptic as well?

It is listed in the "installed files" section of the audacious package in feisty repos. Hence yes, it's included in the base.

---

### Post by notwen on 2007-04-25
Very nice, j/w, but did you 'sudo apt-get install conky' as well or did you compile your conky from source?  Just trying to figure out if audtool will work w/ the basic conky installation using apt-get.  Will possibly save alot of future users who have this issue, from having to go through enabling audacious while re-compiling conky.

---

### Post by freakavoid on 2007-04-25
Nope, just installed via apt-get.

---

### Post by notwen on 2007-04-25
Hah, wish you would have posted a bit earlier, before I went through re-compiling, but better late than never.  =]  Thanks for all your info regarding audtool.

---

