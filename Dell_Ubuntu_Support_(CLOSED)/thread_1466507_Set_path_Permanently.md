---
title: "Set path Permanently"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hari.iiitb on 2010-04-30
Hi,

I'm a newbie to the forums here, I'm a bit confused what to post where... Please pardon me. I have installed Ubuntu 10.04 32 bit in my Dell Studio 15. I've installed TeXLive2009 distribution and I need to add path to my username permanently.

export PATH=$PATH:/usr/local/texlive/2009/bin/i386-linux

I don't want to execute this line each and everytime when I open new terminal. Please suggest me a method where I can add it permanently. 

Earlier, I think in Ubuntu 9.04, I used to add it to .bashrc file. But now, the file looks completely different, with all sorts of if statements. Hence I didn't want to touch it. Please suggest a way to add path to LaTeX permanently.

Thanks

---

### Post by venik212 on 2010-05-01
In addition, if you install TL2009 from Synaptic (as I did), the path is different from the one you mentioned for your installation.  If someone could tell me the right path for the TL binaries (which apparently need   to be added BY HAND to the .bashrc file!) it would be a great help.

---

### Post by Arthur_D on 2010-10-13
Same problem here. I would like a quick response if possible - I'm using scripts pretty much, but I forgot how I did it, and all the guides I can find says to edit the ~/.profile or ~/.bashrc file, but they doesn't seem to be the right files (and it didn't work actually).

The line I tried adding:
```
export PATH=$PATH:/home/magne/Dokumenter/Scripts
```

---

### Post by hari.iiitb on 2010-10-13
Open terminal and do ls-a. You should be able to see .profile file.
Type gedit .profile
Just add this line at the end
PATH="/usr/local/texlive/2010/bin/<arch>:$PATH"

where <arch> can be x86_64_linux (if it is 64 bit OS) or i386_linux (if it is 32 bit OS)

Screenshot:

[http://i52.tinypic.com/2r559g9.png](http://i52.tinypic.com/2r559g9.png)

---

