---
title: "building driver question"
date: 2005-12-04
forum: Desktop Environments
---

### Post by notworking on 2005-12-04
Okay, I considered naming this thread "help me!" but thought it might be better, for those furure folk who come in searching for answers to similar problems, if I stick with a meaningful title.

I have recently installed Ubuntu 5.10 on my Compaq Armada 1750 and it's a wonderful little system... Except I have been struggling to get my softmodem to work (I see this is a common problem). After poking around searching for threads that discuss this problem I have done everything I can think of.

I have downloaded and used scanmodem... This didn't give me much to work with for concrete information, but it did give me some good places to look. 

Taking what I have found I have now downloaded a potential driver.. The problem? It needs to be built and installed, and for some reason any attempt I make to follow the instructs I've read here for others ALWAYS fails to achieve anything. So, I have a file called slmodem-2.9.10.tar.gz sitting on my desktop (I have an unzipped copy as well).

All attempts to build it result in "No rule to make target..."

And so, I am lost...

I have installed build-essential, and pretty much everything else I could find that might help (after reviewing the board)... Now I'm resorting to begging for clarity from someone who can explain in pure terms that even an idiot (not that I would call myself an idiot.. but...) could understand... Anyone here gifted enough to be able to talk me through this slowly and extremely clearly... Bear in mind, I'm completely new to all things linux.

I'm also having issues with my sound (no sound device was detected) but I'll go over past answers to that after I fix the modem issue (when not juggling two computers).

Thanks in advance, to the brave soul who tries to help!

---

### Post by towsonu2003 on 2005-12-04
maybe offtopic a little bit or not so helpful but, try the prebuild package for slmodem (which I am using)... not sure it will work for you, but it's easy to stop :) file is SLMODEMD-2.9.9e-pre1-alsa.tar.gz from linmodems.org/packages/smartlink/

unpack it (or just double click and take the 1.3MB 'slmodemd' out of it. copy to /usr/bin then ```
sudo chmod u+x /usr/bin/slmodemd
sudo slmodemd <optionsyouneedtouse>
```you can read the readme file for options and take a look at scanmodem output for what to use... I do ```
sudo slmodemd --alsa -c USA modem:1
```

if this one doesn't work, try emailing the linmodems emailing list for a link to a precompiled slmodemd.

other than that, have no idea... good luck.

---

### Post by notworking on 2005-12-04
everything works up until the first termila command at which point I get "cannot access slmodemd : no such file or directory".

which basically means I've no idea if it will work yet... but I have it the file downloaded and the slmodemd part in the bin.

The same problem I have been having when to use the terminal for unziping files.  Terminal hates me... :)

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=notworking]everything works up until the first termila command at which point I get "cannot access slmodemd : no such file or directory".

which basically means I've no idea if it will work yet... but I have it the file downloaded and the slmodemd part in the bin.

The same problem I have been having when to use the terminal for unziping files.  Terminal hates me... :)[/QUOTE]
If you browse to the /usr/bin/ folder, can you find the slmodemd file you copied there?  There are lots of files in the folder, so a quicker way to check (from the terminal) is:
```

$ ls -l /usr/bin/slmodem

```
If it shows you the file, great!  I f you get:
```

ls: /usr/bin/slmodem: No such file or directory

```
That means you didn't copy the file to /usr/bin.

---

### Post by notworking on 2005-12-04
I reinstalled windows so I could get as much info as possible about my modem and such (as the scanmodem utility suggested using windows to get the information because it turned up squat). 

I have reinstalled ubuntu on a partition now. Haven't recopied the file to the bin yet BUT I was able to visually browse the file before and it was there. Even after restarting terminal refused to see it, but I could still go to the directory in nautilus and see it there. 

If I copy something to desktop and try and unzip the file it will do the same thing "no such file or directory" when in fact I can see it. I've double and quadruple checked all spellings of the commands, and even tried substituting the path with variations that make sense based on the visual path to file.

i'll try after work today to see if the new install changes anything (though from what I've seen the fan doesn't want to work in ubuntu with the new install, but it does in windows).

---

