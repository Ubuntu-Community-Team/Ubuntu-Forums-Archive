---
title: "CPU extremely easy to overload"
date: 2009-03-28
forum: General Help
---

### Post by holdie on 2009-03-28
So this is something I've been noticing for a while, but it's getting really frustrating so I figured I'd post it up here.  

Basically, it seems like almost anything will overload the CPU on my computer (running Intrepid on a Dell Inspiron 6000 with 1.5 gigs of RAM).  For instance, if I've got Amarok/Firefox running I can't really use any other program because the slowdown is so bad, just those two alone cause a lot of jitteriness and freezing.

I'm not running any intense graphics stuff (no compiz) and I don't have much in the way of background processes.  Can anyone think of a possible explanation for why this might be happening?  I know it's not the latest and greatest CPU, but I definitely remember playing Half Life 2 with a bunch of other stuff running back in the day and didn't really have a problem.

---

### Post by hyper_ch on 2009-03-28
open a terminal, install htop and iotop, have them both run in different terminals and when you see performance issues then check what those two tools tell you.

---

### Post by 3Miro on 2009-03-28
Make sure you have the correct graphical driver installed, you don't want to do graphical stuff on the CPU.

Then you can either use top on the terminal or go to system -> Admin -> System Monitor and check to see which process is taking the bulk of the CPU power.

---

### Post by holdie on 2009-03-31
I tried the htop, iotop programs and found a couple of things that generally took up the most memory

one process /usr/X11R6/bin/X etc. etc. consistently took up about 25% of my CPU (would this be graphics I'm guessing?)

Firefox would also shoot up to about 40% whenever I did something in a website

Also, the iotop program itself took up like 3-10% of my CPU

those were the biggest contributors...any ideas?

---

### Post by hyper_ch on 2009-04-01
well, it's normal for short times that a process spikes to 100% or something... so firefox is cool... but X being constantly that high... you have desktop effects enabled? you do have correct video drivers installed?

---

### Post by Mehashi on 2009-04-01
[COLOR=Magenta]Hi[/COLOR]!

I am also having this issue on my second PC.
 Firefox will generally take up 50-80%, system monitor around 25-50%(peak) and generally window decorator will jump up to fill the gap. 
It is a p4 2.8ghz and definately is not dying as (I hate to say this but it is relevant) it handles workload fine in windows, even when I game. The weird thing is even when it says 100% i can still use more programs and only video media and firefox seems to be affected. 
Ati drivers seem to be fine, and desktop effects have never been easier, but the system can get bought to a halt by firefox? seems strange to me! 

Is there a way of streamlining firefox/system monitor for lower cpu usage?

Thanks for any help!
[COLOR=Magenta]^_^[/COLOR]

---

### Post by holdie on 2009-04-02
Not sure on the graphics, but I would definitely say it's a suspect...I've always had problems with the video drivers in linux (seems I can never tell which one's I've got installed and such)

is there a way to default the computer back to the drivers that came with the original Ibex without totally erasing it?

---

