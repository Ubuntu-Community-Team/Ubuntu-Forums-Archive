---
title: "utube video keeps pausing"
date: 2008-10-14
forum: Desktop Environments
---

### Post by keratos on 2008-10-14
running sidux:

xfce4.4.2
kernel siduxbox 2.6.26-6.slh.1-sidux-686

no utube video!!

downloaded libflashplayer.so and placed into .mozilla/plugins

flash video from utube now plays but every so often it pauses , sometimes for a second, sometimes for minutes, then resumes.

the problem does not occur on my fedora 8 installation on the same HDD on the same machine, when i dual boot into fedora. 

ping of utube ...

daz@siduxbox:~$ ping uk.youtube.com
PING youtube.l.google.com (208.117.236.69) 56(84) bytes of data.
64 bytes from youtube.com (208.117.236.69): icmp_seq=1 ttl=237 time=184 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=2 ttl=237 time=181 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=3 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=4 ttl=237 time=180 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=5 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=6 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=7 ttl=237 time=183 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=8 ttl=237 time=182 ms

any ideas?

any more info needed ?

---

### Post by XanTrax on 2008-10-14
> **keratos said:**
> running sidux:

xfce4.4.2
kernel siduxbox 2.6.26-6.slh.1-sidux-686

no utube video!!

downloaded libflashplayer.so and placed into .mozilla/plugins

flash video from utube now plays but every so often it pauses , sometimes for a second, sometimes for minutes, then resumes.

the problem does not occur on my fedora 8 installation on the same HDD on the same machine, when i dual boot into fedora. 

ping of utube ...

daz@siduxbox:~$ ping uk.youtube.com
PING youtube.l.google.com (208.117.236.69) 56(84) bytes of data.
64 bytes from youtube.com (208.117.236.69): icmp_seq=1 ttl=237 time=184 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=2 ttl=237 time=181 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=3 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=4 ttl=237 time=180 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=5 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=6 ttl=237 time=182 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=7 ttl=237 time=183 ms
64 bytes from youtube.com (208.117.236.69): icmp_seq=8 ttl=237 time=182 ms

any ideas?

any more info needed ?

I noticed this would happen to me when I would have something like Audacious running and/or playing a song.  Same thing with having a video open in Totem, gxine, and/or VLC.  Make sure you're exited out of all other media-related programs such as those.  Exit Firefox and reopen it.

---

### Post by keratos on 2008-10-17
I only had one browser window open.
nothing else
???

---

### Post by gholm on 2008-10-27
I get this too.
I'm on AMD Hardy 64, 
Latest flash install courtesy of [Vivek's]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") script. still pausing at the 5%-10% playback mark, sometimes 50% if I'm lucky.
No other processes running in Gnome.

same behaviour vimeo, utube

---

### Post by oRioN84 on 2008-10-28
I also share this problem, Ubuntu 8.04 (Hardy) Kernel: 2.6.24-21-generic

*sometimes* youtube vids play for 2sec then pauses (or freezes i suppose is a better term).

I have installed the same fixes you have libflashplayer, etc. No other programs running. It is interesting to note that I've had this happen in WinXP also, although it was rare.

---

### Post by keratos on 2008-10-28
okay for me in WinXP and indeed other distros I'm using (Fedora8, Arch 5, RHEL 5)

---

