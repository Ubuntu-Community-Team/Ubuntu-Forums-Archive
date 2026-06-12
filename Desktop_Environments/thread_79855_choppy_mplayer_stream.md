---
title: "choppy mplayer stream"
date: 2005-10-21
forum: Desktop Environments
---

### Post by jdway on 2005-10-21
I have recently rid my system of totem and replaced it with mplayer with the synaptic package manager and I have downloaded the w32 codecs through the terminal prompt. Now when I try to watch a video clip off of a website it is choppy (audio and visual). What can be done to correct this.

---

### Post by strummsteel on 2005-10-21
I have the exact same problem, if i didnt have this problem, My Ubuntu setup wopuld be perfect. Any help would be much appreciated.

---

### Post by ming0 on 2005-10-21
ditto, I've been having this problem lately...

---

### Post by Azrael on 2005-10-21
Compile it yourself. I built the latest mplayer from cvs and built the latest 3.15 mplayer plug-in. Streaming for me now works extremely well.

Do this first: [http://ubuntuforums.org/showpost.php?p=428674&postcount=25]("http://ubuntuforums.org/showpost.php?p=428674&postcount=25")

And then this: [http://ubuntuforums.org/showpost.php?p=328000&postcount=72]("http://ubuntuforums.org/showpost.php?p=328000&postcount=72")

..well, those instructions don't completely match but if you read the rest of both threads as well it should be clear.

---

### Post by Nomad64 on 2005-10-21
I sometimes get this problem...funny part is that it only happens some of the time. Most noticably when streaming from CNN.com. I would suggest right clicking on the video and selecting "Configure" from the drop-down menu. Make sure that your audio and video outputs are correct, and maybe play with the cache size/amount to cache to see if that helps.

For me, most movies stream just fine, and some don't. It doesn't really bother me, though...just annoys.

---

### Post by strummsteel on 2005-10-21
Hmmm, this problem is tough, no one in mplayer and ubuntu has solved this? This turning into a floppy problem that has never been solved.

---

### Post by Azrael on 2005-10-21
I guess my name is No One then.

---

### Post by strummsteel on 2005-10-21
No offense to Azrael though but do we really have to recompile? One of the reasons why ubuntu is so great is that you just use synaptic and its done.

Weird, but this problem is not isolated almost everyone has this and no one has answered it or at least found a work around that doesnt involve recompiling.

---

### Post by Hairy_Palms on 2005-10-21
try this, open gmplayer and right click on the player and select "Preferances->Video" then change your video driver to x11/xv also try changing the video codecs in the codecs tab.

---

### Post by 3david on 2005-10-21
I had a choppy sound problem with mplayer because of alsa, i fixed it by using esd instead, i don't know if it's the same problem as what you're referring to, but take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=79136](http://www.ubuntuforums.org/showthread.php?t=79136)

---

### Post by Azrael on 2005-10-21
[quote=strummsteel]No offense to Azrael though but do we really have to recompile? One of the reasons why ubuntu is so great is that you just use synaptic and its done.[/quote] Indeed, you shouldn't need to recompile, but sometimes problems stem from the coding of the program itself -- something the developers might have fixed in a newer version. In that case, you can either wait a few weeks for the update to reach the repositories or you can be impatient like me and compile it yourself from the latest sources.

On the other hand, there might be a much more simple fix.:p
Try what Hairy_Palms and 3david suggest if you hadn't done so already.

---

### Post by strummsteel on 2005-10-22
Guys,

I managed to fix this, i changed the preferences of Mplayer to use X11/xv video and used the quicktime codec. Lastly I right clicked on mplayer-pluins setting and used esd as my audio source. Now everything works flawlessly. Thanks to everyone who helped.

Next project... Webcams and Instant Messaging WebCams

---

### Post by anonOmus on 2005-10-24
whats this fakeroot stuff? I try to run the command 

[HTML]fakeroot debian/rules binary
bash: fakeroot: command not found
[/HTML]

any tips?

---

### Post by Luggy on 2005-10-24
Switching my audio to esd fixed the problem for me.

---

### Post by Stolen on 2005-10-26
I don't use ESD, but switching to oss also seems to have fixed it up.

---

