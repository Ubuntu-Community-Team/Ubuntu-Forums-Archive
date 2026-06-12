---
title: "The most efficient mediaplayer for old Linux machines?"
date: 2008-05-12
forum: Debian
---

### Post by khelben1979 on 2008-05-12
Hello.

I want to know which mediaplayer is the most efficient one for old Linux computer systems. I currently use VLC and it works pretty good, but when I watch DVD movies it gets a bit slow. 8-( The Powermac has no DVD player but it plays .VOB files which DVD:s contains.

I know about Mplayer which is an efficient player, but I don't get it to work on the Debian Etch system. I have tried and compiled many, many versions but they refuse to work with graphics and some versions(especially newer ones) only hangs the system. I think it has to do with the fact that Debian chose to leave Xfree86 in favour of Xorg.

Any suggestions? (B.t.w I have tried several players by the years and Mplayer has been the fastest one and most efficent so far.)

Also, if there is a good Mplayer package for a PPC Linux system which also would work on a Debian Etch system I would be interested to hear about this. I will ask this question on more Debian specific forums too b.t.w.

---

### Post by Sef on 2008-05-12
Moved to Debian Forum.   Do not double post, otherwise an infraction can result and the threads merged or one will be locked.

---

### Post by hwertz on 2008-05-12
> **khelben1979 said:**
> Hello.
I know about Mplayer which is an efficient player, but I don't get it to work on the Debian Etch system. I have tried and compiled many, many versions but they refuse to work with graphics and some versions(especially newer ones) only hangs the system. I think it has to do with the fact that Debian chose to leave Xfree86 in favour of Xorg.


     I'd try mplayer again, but try flags such as "mplayer -vo x11".  "vo" sets video output type.. "mplayer -vo help" will list all output types (some will write to .gifs and stuff, but there's several "real" output types.. xv, x11, xover, gl, gl2, dga, and sdl all apply.  I'd try x11, sdl, and xv first... I think xv might be the default though.)    Total command line will be like "mplayer -vo x11 -dvd-device (some VOB) dvd://0" where dvd://0 can be dvd://1, 2, etc. depending on track number.   

   If it works but is still too slow just occasionally, "-mc 0.1" will set it to speed video back up later to catch up with audio, or "-framedrop" will force frame drops.  (Having video fall behind then catch up can be annoying, but it's less annoying than having it get super-jerky during the action scenes :popcorn:). You can put any of this into .mplayer/config one option per line as for instance "mc=0.1" "vo=x11" "framedrop" etc. so you don't have to type them every time.

     I think your system should be able to just manage it... I did some playback on a P2-333, it wasn't great but was acceptable.

---

### Post by khelben1979 on 2008-05-12
Good advice! I will try this.

I also want to know if you have experimented with different versions of Mplayer, because, as I wrote: some versions of mplayer has been working bad while others have been working really good. What is your experience with using different versions of Mplayer?

---

### Post by rholt on 2008-05-27
> **khelben1979 said:**
> I want to know which mediaplayer is the most efficient one for old Linux computer systems. I currently use VLC and it works pretty good, but when I watch DVD movies it gets a bit slow. 8-( The Powermac has no DVD player but it plays .VOB files which DVD:s contains.

I've been using moc, an ncurses player. Works for radio, cds, etc. 
$ sudo apt-get install moc

Then run in a term, $ mocp

One of the least resource demanding.

---

### Post by khelben1979 on 2008-05-27
Can Moc run DVD movies or AVI/mpeg films?

---

### Post by kerry_s on 2008-05-27
are you running a straight install of debian etch?

if so, first i would recommend you go custom, build up from the base, don't use a desktop, use a light window manager instead. it's all a matter of balancing out the resources of your system. you might also want to move to lenny, programs aren't as old.
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta1/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso)

install the base, so when it gets to package selection, uncheck everything.
log in as root
apt-get install xorg

(that's a base install with X, you need to pick a light wm of your coice, i'll do fluxbox since it's the most common)

apt-get install slim fluxbox menu synaptic
update-menus

(that's enough to get you to a gui)

reboot (ctrl+alt+delete)

log in as your user, open synaptic and continue adding what you want.
if you keep it light you should have more resources to run programs like vlc & open office perfectly.

i don't have ppc, but i run a debian custom on 450mhz 256mb ram.
i use vlc by the way.

---

### Post by khelben1979 on 2008-05-27
No. I won't reinstall Debian on it. It works fine. I just wanted to know if Moc can run DVD movies..

Perhaps a newer Linux kernel in the next Debian will make the system faster? What do you think?

---

### Post by kerry_s on 2008-05-27
> Perhaps a newer Linux kernel in the next Debian will make the system faster? What do you think?

you never know, but the newer the kernel the less legacy support it might have, got to get rid of the old to make way for the new.

i use the etch kernel, so i'm running the same 1 you are, the 2.6.2* kernels in lenny have always gave me problems, it's about the only reason i run etch/lenny other wise i would just go straight lenny.
so my kernel is etch and all the programs are lenny.

---

### Post by oswaldkelso on 2008-06-05
> **khelben1979 said:**
> No. I won't reinstall Debian on it. It works fine. I just wanted to know if Moc can run DVD movies..

Perhaps a newer Linux kernel in the next Debian will make the system faster? What do you think?


NO. moc = music on console

My daughter has a similar spec machine imac ppc 333mhz, 256 mb. She has no dvd drive.
The players installed are  mplayer, xine, and vlc. For video playback all work, but we tend to use vlc. 
To watch dvds we play them on her mothers pc and stream them via vlc (or I rip them to mp4). Streaming is a good option if you have  the hardware/network very easy with vlc even for my 10 yr old. In my experiance with several different ppc machines I would try them all. I got different results with the same player on different ppc machines, hence video is probably the only area where I badly fudge my one app for one job rule.

---

### Post by khelben1979 on 2008-06-06
Mplayer actually ran faster than VLC on my former Debian system (Debian Sarge), but since Debian chose x.org instead of Xfree86, my Mplayer won't show any graphics anymore. Because of this I only use VLC on the mac nowadays.

I have tried compiling different versions of Mplayer myself on this machine but they give me the same result: no video playback. I just get working sound from the movie. It might be that I'm not appending the correct parameters when I choose to compile Mplayer and that Mplayer should work as good as it did on Xfree86, but I don't know.. What do you think?

---

### Post by oswaldkelso on 2008-06-06
I noticed an improvement in video play back when I upgraded it to testing. Eveything just worked. (note I've not updated it for 6 weeks or so and the new Xorg has been a pain on my other ppc machines)

I only have the standard debian repo and debian-multimedia. No contrib or non free. I do have realplayer and a iceweasel/firefox multimedia plugin.  You can see what I installed if you follow the link in my signature, its that machine. Other that that I don't really know what to suggest.

On another tack. I also use Windowmaker on one machine, it's great on lower end machines. Very fast! just a pitty it's a little bit of a ugly duckling. If there was a little bit more development I'm sure the swan inside could find a way out. That said it's been stable and coupled with rox-filer and conky very nice to use.

---

### Post by khelben1979 on 2008-06-07
> **oswaldkelso said:**
> I noticed an improvement in video play back when I upgraded it to testing. Eveything just worked. (note I've not updated it for 6 weeks or so and the new Xorg has been a pain on my other ppc machines)

What is the computer configuration for that one?

---

