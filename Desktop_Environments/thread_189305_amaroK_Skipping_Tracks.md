---
title: "amaroK Skipping Tracks"
date: 2006-06-05
forum: Desktop Environments
---

### Post by rjcube on 2006-06-05
When I make a playlist in amaroK and try to play it, it skips every song and doesnt play a thing, just goes to the next song over and over again.

Any idea what is causing this?

(the files are MP3)

Also, how can I change what program opens a certain filetype?

---

### Post by max_dingemans on 2006-06-05
I had the same problem with amaroK skipping songs when I first switched to dapper. My understanding of the problem is very limited, but switching to the Gstreamer 0.10 engine solved my problem. Hopefully someone else can explain what is actually wrong, since I'm curious myself.

In response to your second question, if you right click on an mp3 file, go to permissions, and then the 'open with' tab, you should be able to choose which application opens the file from a list.

---

### Post by rjcube on 2006-06-05
[QUOTE=max_dingemans]I had the same problem with amaroK skipping songs when I first switched to dapper. My understanding of the problem is very limited, but switching to the Gstreamer 0.10 engine solved my problem. Hopefully someone else can explain what is actually wrong, since I'm curious myself.

In response to your second question, if you right click on an mp3 file, go to permissions, and then the 'open with' tab, you should be able to choose which application opens the file from a list.[/QUOTE]

How do you get Gstreamer Engine? I searched Synaptic for "gstreamer engine" and all that came up was amaroK, and when I search for just "gstreamer" a bunch of stuff comes up that I would have no idea what to do with.

---

### Post by vseehua on 2006-06-05
try install *libxine-extracodecs* via synaptic... hope that helps... i am assuming that you are using xine engine for amarok...

---

### Post by rjcube on 2006-06-05
It works! Not exactly sure what did it tho, might of been the extra codecs, but I also did search gstreamer in the Synaptic and install a few of those what I thought was relevent.

Meh, who cares, it works now, Thanks everyone.

---

### Post by vseehua on 2006-06-05
[QUOTE=rjcube]It works! Not exactly sure what did it tho, might of been the extra codecs, but I also did search gstreamer in the Synaptic and install a few of those what I thought was relevent.

Meh, who cares, it works now, Thanks everyone.[/QUOTE]

well, the description said that the package adds support for more video and audio codecs for xine... glad to help out... ;)

btw, any news on gstreamer-engine for amarok 1.4? i am still waiting for it...

---

### Post by max_dingemans on 2006-06-05
I just installed *libxine-extracodecs* as vseehua suggested, and xine apperas to be working for me now. 

Searching around somewhere, someone mentioned adding the line 'deb [http://kubuntu.org/packages/amarok-14beta3](http://kubuntu.org/packages/amarok-14beta3) dapper main' to my sources list, and then installing the *amarok-gstreamer* package. As far as I remember, that also installed everything I needed for gstreamer to function. Since I can't find the thread that it was mentioned it, and vseehua's advice seems to work, I'd stick with that.

---

### Post by vseehua on 2006-06-05
[QUOTE=max_dingemans]Searching around somewhere, someone mentioned adding the line 'deb [http://kubuntu.org/packages/amarok-14beta3](http://kubuntu.org/packages/amarok-14beta3) dapper main' to my sources list, and then installing the *amarok-gstreamer* package. As far as I remember, that also installed everything I needed for gstreamer to function. Since I can't find the thread that it was mentioned it, and vseehua's advice seems to work, I'd stick with that.[/QUOTE]

nope, that doesn't work for me, i had a newer version of amarok installed..guess i'll hv to stick with xine engine for the mean time...

---

### Post by max_dingemans on 2006-06-05
[QUOTE=vseehua]nope, that doesn't work for me, i had a newer version of amarok installed..guess i'll hv to stick with xine engine for the mean time...[/QUOTE]

It turns out I'm still running amaroK 1.4 Beta3, which is why it works for me. I did find the thread that suggested it though: [http://www.ubuntuforums.org/showthread.php?t=160500](http://www.ubuntuforums.org/showthread.php?t=160500)

I can't seem to find anything else about gstreamer support of 1.4 though. Good luck!

---

### Post by vseehua on 2006-06-05
hmm... i guess i will stick with xine then... it's just that i prefer using gstreamer... 

nah, as long as it works...why bother... :D

---

### Post by localzuk on 2006-06-05
It seems like you didn't have the correct codecs installed. Take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for information about getting all the different codecs available installed...

---

