---
title: "High CPU usage with Firefox"
date: 2005-01-17
forum: General Help
---

### Post by andbert on 2005-01-17
Im running Hoary and Firefox 1.0
Lateley ive experienced that some web pages seem to take a lot of my CPU.
When browsing for example [www.vg.no](www.vg.no) or [www.itavisen.no](www.itavisen.no) , my system is slow and the sytem monitor shows 100 % usage.

The problem also occurs on similar sites with lots of plugins like flash, media-clips and so on.

Ive disabled the IPV6 thing, but nothing happened.
My cpu is a Intel 2,4 ghz, and i have 512 MB RAM, so that shouldnt cause any of the problems.

Dont know if it matters, but the problem first occured right after a 'sudo apt-get update && sudo apt-get upgrade' two days ago.

Any input?

EDIT: Ive also detected the same problem when i open Desktop -> User... -> Themes

---

### Post by andbert on 2005-01-17
Found the solution...
The problem was caused by the packages swf-player or libflash-swfplayer....

---

### Post by Yukonjack on 2005-01-17
[QUOTE=andbert]Found the solution...
The problem was caused by the packages swf-player or libflash-swfplayer....[/QUOTE]

I have the same problem could you explain how you fix this problem please.

---

### Post by andbert on 2005-01-18
of course
dont know if my solution to the problem will help you though

i just uninstalled the packages using synaptic, since i really dont need them.
after a restart of firefox it then worked fine.

maybe others have the reason and a better way fixing it?

---

### Post by Yukonjack on 2005-01-18
Thanks andbert I solved it by installing Epiphany for now :)
Actually pretty good browser this Epiphany mush faster than Firefox on my box.
I will try out you way also and see, meanwhile I'm looking into it.
It's a plugin for macromedia flash, right?

---

### Post by andbert on 2005-01-18
yes as far as im concerned it is.
was just playing around in synaptic, installing some swf-things.

is Epiphany in universe or something?
maybe ill give it a shot  :D

---

### Post by Yukonjack on 2005-01-18
Not to sure I have my sources.list updated with lots of extra since day 1.
=============================================

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe   

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted   
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted   

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse    

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main    
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main   
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by andbert on 2005-01-18
thanks a lot!

---

### Post by Yukonjack on 2005-01-18
[QUOTE=andbert]thanks a lot![/QUOTE]

You are welcome  8)

---

