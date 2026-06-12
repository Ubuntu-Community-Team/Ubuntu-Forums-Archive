---
title: "Setting up Freevo with the Tvtime plugin"
date: 2009-01-04
forum: General Help
---

### Post by Chicosmagiccat on 2009-01-04
Sorry guys, I noobed this up already and posted it in the wrong section, please feel free to throw rocks.

Firstly, allow me to thank those members of the community that came to look at my thread.

As the title indicates I am having trouble getting Freevo up and going (on intrepid).

I am VERY new to 'nix (like as of this week! heh), and that being said, I had absolutely no luck getting Mythtv going either. The documentation assumes a level of knowledge that I do not possess. So ultimately I decided to give freevo a shot. My problem is that I don't really understand the file system and permissions deal...basically Freevo needs Tvtime to actually play live tv (which is verified as functioning on my system (ati tv wonder pro as the source) and to activate the plugin for Tvtime I need to add two lines of code to a file. I have used Dolphin and other file managers to manually look for this file, as well as used them to search for it automatically. It is my supposition that I either don't have the permissions to see the folder that the file resides in since I only know to execute things as su in the console, or the file does not exist.

Can someone please throw me a preserver? I have spent some pretty serious time trying to find the answer myself, but I have a feeling my approach is flawed due to my lack of exp with the OS, and I am probably not asking the pertinent questions.

I need to place this:

plugin.remove('tv.mplayer')
plugin.activate('tv.tvtime')

Into the file:

local_conf.py

As per the instructions at:

[http://doc.freevo.org/TvPlugins](http://doc.freevo.org/TvPlugins)

As I mentioned, Tvtime seems to capture just fine, also I have set up Freevo with all the correct dependencies and it will load, I just have no option for live tv.

(as a side note since I mentioned Mythtv, basically I could not figure out how to initially set it up, with all that server business and port number shenanigans, I don't want any network connectivity to share files, I just want to tivo on the TV that this box is hooked to. I could never even get past the network settings stuff on Mythtv, so I gave up...I have heard it is better than Freevo though...any thoughts?)

---

### Post by Chicosmagiccat on 2009-01-04
Just a *bump* to keep this in the top list.

---

### Post by Chicosmagiccat on 2009-01-04
Alright, I managed to find the file using sudo find / -name "fileToFind", I was then able to navigate to it using file browser and open it with an editor .

I am now however unable to edit the file itself because I do not have appropriate permissions. My next question is this: How do I edit the file as su?

Also, on a side note I was looking in the file and I have NO idea where to add the lines that I previously mentioned, so any input there would be greatly appreciated as well!

Thanks!

---

### Post by Chicosmagiccat on 2009-01-04
Okay, I found how to edit files as root, using gksudo nautilus and then navigating to the file and opening it from within the gnome file browser. I have added the two lines of code (in the plugins section of the file) and saved, I am now going to test and will report my results so that anyone else having my same issue can learn from my mistakes. ;)

---

### Post by Chicosmagiccat on 2009-01-04
No dice.

All documentation I can find is pretty unclear as to where I should be adding those two lines of code to that .py file. Adding it to the plugin portion of the text within and saving resulted in no change. Freevo documentation is also unclear as to how the two programs are intended to function together. For example which should be started first? I have tried both and had the same results. I'm assuming that I added the two lines of code incorrectly somehow. Any input would totally rock.

---

### Post by Chicosmagiccat on 2009-01-04
No luck yet.

I'm thinking a commercial DVR may be a bit more out of the box friendly, since I am a bumbling fool with nix, lol.

---

### Post by Chicosmagiccat on 2009-01-05
Ok, well I have officially given up on the 'nix home theater, the documentation just isn't comprehensive to a non long time user. 

This will be the third time I have tried a linux distro, only to return to windows. 

I feel badly because I really believe in the ideals of open source, but linux just is not ready for the masses, and is certainly not ready for my desktop. 

I mean the idea is great, but so far it is really poorly executed. I mean can you really expect joe blow to spend any real time learning console commands? Honestly, that isn't going to happen. 

I forsee linux staying firmly planted in the embedded systems market, with these novelty distros being aimed more towards hobbyist techies. The usability factor for a complete newbie is zero. The first time one single problem comes up, you are stuck in apt-get hell trying to find dependencies for X to make Y function correctly with Z. And don't even get me started on the community...if you aren't a 'nix dude, you will get ignored, treated like an idiot, and otherwise turned away from the OS.

Those are the inherent problems I see as an outside observer. I'm sure I'll get flamed, and wished 'good luck with those virus', but I am just calling it how I see it.

Thanks for all the great help...oh, wait...

[http://ozguru.mu.nu/Photos/2005-11-11--Dilbert_Unix.jpg](http://ozguru.mu.nu/Photos/2005-11-11--Dilbert_Unix.jpg)

---

