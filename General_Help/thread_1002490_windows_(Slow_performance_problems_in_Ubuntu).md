---
title: "windows (Slow performance problems in Ubuntu)"
date: 2008-12-05
forum: General Help
---

### Post by mhh91 on 2008-12-05
everytime i see something on this forum,i try 2 check it out on my computer,but then i remember that i'm currently running MS windows ](*,)

i'm dualbooting XP and intrepid,but intrepid has been acting weird lately,it's slowing down suddenly,is this happening 2 anyone else here?

---

### Post by inobe on 2008-12-05
what are your normal activities when intrepid is operating the machine, has anything gone wrong in the past that required fixing, what is acting weird ?

---

### Post by mhh91 on 2008-12-05
well,i'm running either transmission or vuze (Azureus) + rhythymbox + firefox

after about 15 mins of use,it starts to slow down,and i have to restart the machine for everything to work smoothly again :(

---

### Post by Giant Speck on 2008-12-05
> **mhh91 said:**
> well,i'm running either transmission or vuze (Azureus) + rhythymbox + firefox

after about 15 mins of use,it starts to slow down,and i have to restart the machine for everything to work smoothly again :(

How much memory do you have?

You could switch to a lighter alternative to Firefox, such as Swiftfox.  Swiftfox will do everything Firefox can, and it uses only about half the memory.

---

### Post by mhh91 on 2008-12-05
i have 512MB of RAM

when i use other distros (e.g. fedora10 or opensuse 11.0) that doesn't happen,also,ubuntu uses much more CPU than those,why?

---

### Post by magmon on 2008-12-05
Wow.. I have 1.6 gig of ram, and I lag with all those apps out. Maybe try without the music player?

---

### Post by mhh91 on 2008-12-05
those are just 3 apps,i'm doing it with windows and it's not lagging at all,fedora and opensuse do it as well,why not ubuntu??

---

### Post by inobe on 2008-12-05
> **mhh91 said:**
> well,i'm running either transmission or vuze (Azureus) + rhythymbox + firefox

after about 15 mins of use,it starts to slow down,and i have to restart the machine for everything to work smoothly again :(

run them and check system performance, see if ubuntu uses swap.

you could also open terminal and type **top** then hit enter, copy and paste each output on your next post.

---

### Post by magmon on 2008-12-05
I dunno man, but Transmission takes a sizeable chunk from my mem. Maybe its cuz Im downloading about 1 GiB of video per download, but hey.

---

### Post by MikeTheC on 2008-12-05
512MB has really kind of become the "minimum" any more. Simply going up to 1GB of RAM will yield quite a nice amount of performance gain.

If your box can handle it, I'd suggest putting 2GB in instead, as both your Windows and Ubuntu installs will tremendously benefit from that.

Myself, I can't imagine having a system with less than 2GB of RAM in it any more. But, hey, what's the expression? "That just how I roll."

---

### Post by mhh91 on 2008-12-05
i'm downloading fedora 10 DVD = 3.41GB :lolflag:

---

### Post by mhh91 on 2008-12-05
> **MikeTheC said:**
> 512MB has really kind of become the "minimum" any more. Simply going up to 1GB of RAM will yield quite a nice amount of performance gain.

If your box can handle it, I'd suggest putting 2GB in instead, as both your Windows and Ubuntu installs will tremendously benefit from that.

Myself, I can't imagine having a system with less than 2GB of RAM in it any more. But, hey, what's the expression? "That just how I roll."

my computer is quite dated (2005) and it wasn't the best there is back then,the spare parts for my computer are no longer sold here

and sadly,i can't afford to buy a new one :(

---

### Post by magmon on 2008-12-05
Theres your lag!! That is a HUGE file!

---

### Post by mhh91 on 2008-12-05
> **magmon said:**
> Theres your lag!! That is a HUGE file!

then i'll stick to utorrent and windows till the download finishes :D


one other thing,though

i've NEVER been able to restart with linux,i always have to push the button on my case,why does that happen?

all i get is "restarting computer" and then nothing happens

---

### Post by magmon on 2008-12-05
Hmm, thats a great question... Maybe bad install resulting in missing files or odd configuration? Restart works perfect for me every time.

---

### Post by mhh91 on 2008-12-05
that happens with ALL the distros i've installed,i don't think that's a problem with the installation,because i've never had installation problems

---

### Post by magmon on 2008-12-05
I have no idea then. Maybe one of the users more experianced with Ubuntu and linux in general can help ya out.

---

### Post by mhh91 on 2008-12-05
thanks anyway :)


waiting for anyone to help.........

---

### Post by mhh91 on 2008-12-08
Bump!

---

### Post by Martje_001 on 2008-12-08
I think it's vuze, try another bittorrent client. I'm running on 512MB also, and it's smooth when running rhythmbox, firefox, transmission and gimp at the same time.

---

### Post by dannytatom on 2008-12-08
Deluge is a good torrent client, more lightweight than vuze.  You can get it from synaptic as 'deluge-torrent' I believe.

---

### Post by speedwell68 on 2008-12-08
> **mhh91 said:**
> my computer is quite dated (2005) and it wasn't the best there is back then,the spare parts for my computer are no longer sold here

and sadly,i can't afford to buy a new one :(

You still should be able to get spares like memory for a 3 year old PC.  My laptop is just over 2 years old and I put another gigabyte of memory in it a short time ago.

---

### Post by waapwoop1 on 2008-12-08
I bet the problem is that Klogd and DD are running in the background

type top and see what is running.

these programs slow down intrepid unless you kill them. 

I haven't had the problem recently, not sure if it is fixed or not.   But my PC would slow to a crawl after 15 mins of use. even with 2gb ram and a dual core processor. There was a launchpad bug thing on it somewhere too.

---

### Post by K.Mandla on 2008-12-08
This is starting to turn into a support thread, so let's move it into General Help.

---

### Post by NocheBoy on 2008-12-08
yeah Firefox has some memory leaks. Try googling firefox memory leak fix or try not using firefox and see if it's still slow

---

