---
title: "Slowness of Ubuntu"
date: 2006-10-01
forum: Desktop Environments
---

### Post by RocketLinux on 2006-10-01
Compared to the Xandros system that I just replaced, Ubuntu is about twice as slow.

Now, I don't know much about how Linux works, but I think it has got something to do with disk partitioning and/or the swap file.

I went into KDE, and ran KinfoCenter.

Initially the display looked like this :

  Total Memory
    Total Free Memory        75%
    Unused Physical Memory   24%
  Physical Memory
    Application Data         28%
    Disk Cache               43%
    Free Physical Memory     23%
  Swap Space
    Free Swap Space          98%

I then started loading applications like Firefox, OO etc etc. The display then looked like (with disk activity light hard on) :

  Total Memory
    Total Free Memory        69%
    Unused Physical Memory   30%
  Physical Memory
    Application Data         36%
    Disk Cache               57%
    Free Physical Memory      7%
  Swap Space
    Free Swap Space          98%

That is, swap space didn't change but disk cache just went on going up and up and the system started going slower and slower.

Are there some tweaks that I can do to improve the performance (without wiping out my system) ?

---

### Post by Josh1 on 2006-10-01
Hi,
Just to let you know, KDE is a resource hog and will try to use everything it can get.. but that won't stop me from using it ;).
- Josh

P.S: I have 1.5 gig RAM, so with this amount I dont get slow downs at all. :).

---

### Post by RocketLinux on 2006-10-01
It's slow in Gnome. I just went to KDE to see if there were any other programs that would give extra data.

---

### Post by angustia on 2006-10-01
is it a progressive slow down or just right after loading or using those programs too long?

---

### Post by lagagnon on 2006-10-02
RocketLinux: hmmm very strange because I actually find Daper significantly faster than Xandros.

Please run the command "top", in a terminal and wathc it as you start opening programs. Are there any processes that start consuming large amounts of CPU, especially after the apps have opened and stablized? Also, post to this thread the output of commands "free" and "df".

---

### Post by WalmartSniperLX on 2006-10-02
Ubuntu uses gnome 2.14 build 3. I think it might have something contributing to the slowness. Not sure. But I know gentoo, which is a lot faster, uses gmone 2.12 pre compiled for simplicity:performance. I dont know about xandros, but this is something I read up a while back when I asked myself the exact question your stating now, except I was comparing ubuntu with gentoo. 

But I know what you mean by slowness. Slow gui, cpu cycles, etc. I had it too. Im using Kubuntu inwhich I find much faster. But, Edgy is being released and I heard the way they compiled Gnome 2.16 in it makes it very fast. I used it too and I noticed the live cd itself was MUCH faster than Dapper's :D

---

### Post by RocketLinux on 2006-10-02
> **lagagnon said:**
> RocketLinux: hmmm very strange because I actually find Daper significantly faster than Xandros.

Please run the command "top", in a terminal and wathc it as you start opening programs. Are there any processes that start consuming large amounts of CPU, especially after the apps have opened and stablized? Also, post to this thread the output of commands "free" and "df".

top.zip is a pdf file as the txt didn't seem to work

---

### Post by RocketLinux on 2006-10-02
> **angustia said:**
> is it a progressive slow down or just right after loading or using those programs too long?

I think it's more slowere the first time I load them.

---

### Post by RocketLinux on 2006-10-02
> **WalmartSniperLX said:**
> Ubuntu uses gnome 2.14 build 3. I think it might have something contributing to the slowness. Not sure. But I know gentoo, which is a lot faster, uses gmone 2.12 pre compiled for simplicity:performance. I dont know about xandros, but this is something I read up a while back when I asked myself the exact question your stating now, except I was comparing ubuntu with gentoo. 

But I know what you mean by slowness. Slow gui, cpu cycles, etc. I had it too. Im using Kubuntu inwhich I find much faster. But, Edgy is being released and I heard the way they compiled Gnome 2.16 in it makes it very fast. I used it too and I noticed the live cd itself was MUCH faster than Dapper's :D

As I said, I don't know much about Linux, but I don't know why it isn't swapping programs out to the swap file (if that is what it's supposed to do).

---

