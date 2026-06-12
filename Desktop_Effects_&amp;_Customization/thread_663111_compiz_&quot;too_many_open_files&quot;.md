---
title: "compiz &quot;too many open files&quot;"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by hebetude on 2008-01-09
compiz --replace returns:
.: 3: 3: Too many open files

I'm using fglrx in hardy, this seems to be a common java app problem but whats the deal with compiz here?  I even doubled my open file descriptor limit and I still get the error.  I called compiz.real --replace and it loaded somewhat.

My ulimit settings:
```

$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 16383
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 2048
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 16383
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

notice open files is doubled 2048 instead of 1024.  I've seen no other reports of this problem so I suppose its something wrong with my settings.

Thanks,

---

### Post by pgn674 on 2008-01-10
I too just got this problem. Not sure what started it, as I've been tinkering with things like drivers for a good while now. Any chance you have an ATI card, a dual screen setup, or are using AIGLX?

---

### Post by pgn674 on 2008-01-10
Oh, I just figured it out. Here is the contents of my file /etc/xdg/compiz/compiz-manager.ubuntu :```
#Updated whitelist and source Ubuntu settings

. /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"
```Well, if the file is referencing itself, you'll get an infinite loop, and increasing your open file descriptor limit won't help. So I commented out that line, and I no longer get that error.

Wow, it's nice to actually figure something out on my own instead of looking it up online for once :)

---

### Post by engstrom on 2008-01-10
I've been trying for ages to get Wine running WoW which involves removing glx or so I'm told (to enable Direct Rendering). I've replaced it with AIGLX as recommended and Wine/WoW run fine. I try to enable Desktop Effects and it always tells me that it is unable to be started.
I tried messing with various things and also followed this post;
[http://www.phoronix.com/forums/showthread.php?t=7193]("http://www.phoronix.com/forums/showthread.php?t=7193")

but it didn't help. I tried to run compiz from a terminal but I got;
".: 3: 3: Too many open files"

I'm using Ubuntu 7.10 and have an ATi X700 and using the driver linked off the above page.

---

### Post by hebetude on 2008-01-10
> **pgn674 said:**
> Oh, I just figured it out. Here is the contents of my file /etc/xdg/compiz/compiz-manager.ubuntu :```
#Updated whitelist and source Ubuntu settings

. /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"
```Well, if the file is referencing itself, you'll get an infinite loop, and increasing your open file descriptor limit won't help. So I commented out that line, and I no longer get that error.

Wow, it's nice to actually figure something out on my own instead of looking it up online for once :)

ROFL great find man, unfortunately I had to read your post on the internet to figure this one out.  :guitar:

---

### Post by engstrom on 2008-01-10
> **pgn674 said:**
> Oh, I just figured it out. Here is the contents of my file /etc/xdg/compiz/compiz-manager.ubuntu :```
#Updated whitelist and source Ubuntu settings

. /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"
```Well, if the file is referencing itself, you'll get an infinite loop, and increasing your open file descriptor limit won't help. So I commented out that line, and I no longer get that error.

Wow, it's nice to actually figure something out on my own instead of looking it up online for once :)

Does this mean that the drivers won't get whitelisted and as a result Compiz won't work?...not that it works for me anyway.

---

### Post by hebetude on 2008-01-10
To the contrary, ubuntu put in the newer version of fglrx and in response added a compiz with fglrx in the whitelist.  You, of course, can whitelist fglrx if you are using 7.11 (8.42) or higher.

---

### Post by engstrom on 2008-01-11
Ok, so I commented out the WHITELIST line in compiz-manager.ubuntu but I still get the "Desktop Effects could not be enabled" message. Damn! :-)

---

### Post by pgn674 on 2008-01-11
> **engstrom said:**
> Ok, so I commented out the WHITELIST line in compiz-manager.ubuntu but I still get the "Desktop Effects could not be enabled" message. Damn! :-)

Oh, well that's not what I did. Take a look at your files in /etc/xdg/compiz/. From what I understand, compiz starts by processing the file compiz-manager. Then, in that file, if it sees a link to another file (like ". /etc/xdg/compiz/compiz-manager.ubuntu"), then it processes that file.

Now, check your files and follow the links and make sure there is no infinite loop. If there is, break it. I broke mine by replacing ". /etc/xdg/compiz/compiz-manager.ubuntu" with "#. /etc/xdg/compiz/compiz-manager.ubuntu" inside /etc/xdg/compiz/compiz-manager.ubuntu.

---

### Post by engstrom on 2008-01-14
The shenanigans continued; I got past the "Too many files" issue only to get the "Compiz not found problem". I followed advice from the compiz forums and deleted the /local/ references from xorg.conf concerning the compiz locations and renamed compiz to compiz.real (or was it the other way around?) in there and it worked!
I can't remember the link in the compiz forums that sorted this out but I shall endeavour to find it and post details in the any relevant threads.

---

