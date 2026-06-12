---
title: "[SOLVED] High CPU load on Dell m1330 powered by Ubuntu 8.10"
date: 2009-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abscess on 2009-01-08
Hi

I have a Dell XPS M1330 and have successfully replaced MS Vista with Ubuntu 8.10. I love it! Except from this one thing.. Even after restart, with no software running, idling, the CPU load is at an average of 40 % for the dual centrino @2,1 GHz..

My system:
Core 2 Duo @ 2,1 GHz
3 GB ram
nVidia Geforce 8400M GS
Latest nVidia drivers, 177.82
Running Compiz Fusion

Please help me! I have no clue what the problem is.

---

### Post by agim on 2009-01-08
Check your system monitor. If you are using Ubuntu, type F2, and in the box type:
gnome-system-monitor

It will have 4 tabs on the top, click on Processes. Then click on ' % CPU '
It will tell you what is using your cpu.

Or, you could use the terminal and type:

top

This will show you which programs are using your CPU as well.

Good luck!

---

### Post by paris_alex on 2009-01-08
that is really wierd... try running "top" from command line to see what is using your CPU cycles...

---

### Post by abscess on 2009-01-08
Thank you all for answering!

Didnt know about the "top" command. It revealed Xorg as the main problem. Please have a look at he screenshot. I took the screenshot after a clean startup, laptop at idle.

[IMG]http://www.rpad.net/Skjermdump-12.png[/IMG]

Ok, so now we are half way there, we know the sinner. ..And on to the next part, how do we make it go away? :D

---

### Post by paris_alex on 2009-01-08
i'm guessing something is not right with your video card configuration for X. Things i would try:

- look at contents of /etc/X11/xorg.conf for any 'wierd' (ok..maybe everything here is wierd {g})
- install nvidia's configuration tool thru "sudo apt-get install nvidia-settings" and launch the GUI configuration (you may need to run it as root via "gksu nvidia-settings" to be able to edit changes)

Good Luck!

---

### Post by abscess on 2009-01-08
Thank you paris_alex!

I will have a look at the configuration later on today. I really hope I will find a magic "fix my Ubuntu" button in the GUI ;)

---

### Post by abscess on 2009-01-08
Hi

I could not find anything "weird" in the xorg.conf, actually, surprisingly litle text! Have a look at the screenshot.

[IMG]http://www.rpad.net/Skjermdump-14.png[/IMG]

I could not find anything weird in the nVidia GUI either, but I tried any possible combination anyway. All with the same result, CPU still idles at about 40 %!

Please, any more tips and tricks on what to do? Dell has even shipped M1330 with Ubuntu, it should be stable right?

I really dont want to go back to 8.04..... :o

---

### Post by abscess on 2009-01-08
I have also tried downgrading the nVidia driver to v. 173.14.12. The problem seems to be a little bit smaller, at least I can use vmware in unity mode without having a 100 % cpu load.

But still, the idle cpu load is too high..

---

### Post by paris_alex on 2009-01-08
i'm really out of idea here.. hope this helps...

- checkout [http://www.debianhelp.org/node/3146](http://www.debianhelp.org/node/3146) seems related
- fyi, i'm using ubuntu 8.04 with nvidia driver version 169.12
- ...might want to try turning off compiz with "metacity --replace &" and see if its still 100%?

...but if it does not resolve your problem.. then let's hope some ubuntu expert can help you out! ;-) i'm actually quite new @ linux as well...

---

### Post by abscess on 2009-01-08
Actually paris_alex (and of course agim), you helped me ALOT!

It turns out that it is "System Monitor" itself that makes Xorg run at 40 %! You can see the graph at the screenshot above.. The CPU load increases as the graph moves more and more to the left, and once the graph area is full, Xorg flats out at 40 %!

Really weird!

You learned me the "top" command, once running in console I closed the "System Monitor" and Xorg dropped to 5 % even with Firefox running!

Before "top" I always looked at the "System Monitor", therefor assuming the idle CPU load was indeed 40 % witch its not..!

Thank you both very much!

Case closed and I am waiting for an Ubuntu update ;) :D:D:D

---

### Post by sujanne on 2009-09-24
[B][SIZE=2]What software do you recommend I use for unobtrusive, non-CPU intensive audio recording?I need to record audio on my workstation, constantly, while it is in use, via the Mic port. What software do you recommend I use for unobtrusive, non-CPU intensive audio recording? Thanks.
___________________
[/SIZE][/B]   [yahoo   keyword tool]("http://www.keywordspy.com/overview/keyword.aspx?q=yahoo%20keyword%20tool") ~   [overture]("http://www.keywordspy.com/overview/keyword.aspx?q=overture")   ~ [traffic   estimator]("http://www.keywordspy.com/overview/keyword.aspx?q=traffic%20estimator") ~   [adwords   traffic estimator]("http://www.keywordspy.com/overview/keyword.aspx?q=adwords%20traffic%20estimator")

---

### Post by mikewhatever on 2009-09-24
> **sujanne said:**
> [SIZE=2]What software do you recommend I use for unobtrusive, non-CPU intensive audio recording?I need to record audio on my workstation, constantly, while it is in use, via the Mic port. What software do you recommend I use for unobtrusive, non-CPU intensive audio recording? Thanks.[/SIZE]

Welcome to the forums, and please start your own thread.

---

### Post by jwaclawsky on 2009-09-26
I am seeing similar behavior on my Dell Mini 9. The Xorg task shown by "top" command seems to level out around 40+ percent CPU when the System Monitor is running awhile on a mostly idle machine (just Firefox and terminal running). When I shut down the System Monitor Xorg drops to single digits. 

Are you saying that CPU usage is really not that high that this is a bug in how CPU is being reported?   ...or is this a bug in the fact the system monitor is really using 40% CPU? Thanks for your reply!

---

### Post by franjo101 on 2009-10-06
how did you stop Xorg?

---

### Post by Turtle.net on 2009-10-12
> **franjo101 said:**
> how did you stop Xorg?
I don't think that stopping Xorg is what you wnat to do.
If you shut down Xorg you'll be in terminal mode. To see what happens then just press ctrl+alt+F1 to see and ctrl+alt+F7 to comme back to a graphical interface.

---

### Post by renatkh on 2009-12-17
Hi everyone,
I have exactly the same problem on my XPS m1330. I don't understand why is it marked as solved, I couldn't find solution here. The fact that system monitor uses CPU does not explain why everything slows down without it. My symptoms are slow computer after some time of idle standing or hard processing (doesn't matter). Rebooting X doesn't help, terminating it nether. Only complete reboot solves the problem. I have also noticed that "top" doesn't show anything using CPU so hard. In addition system monitor (with xorg) doesn't use CPU that much when the laptop runs normal. I am using Kubuntu Karmic Koala, seen same problem on Jaunty. Tried latest nvidia driver, nothing. I am afraid it is a hardware problem, nvidia in particular, so does anyone tried windows and see if it runs fine?
So I'd like to open the topic for discussions. Please help with any suggestions.
Best regards.

---

### Post by mkrate on 2009-12-19
Same problem here... only the complete reboot solves the problem, and the problem re-appears seemingly randomly. System monitor shows pretty much the same load as the top command for each process, but the resources tab in the system monitor shows CPU usage of about 100% on both CPUs - needles to say, the CPU usage for processes does not sum up to 100%... My guess is that there is a phantom process (maybe something USB-related?) that eats up a lot of CPU w/o hitting either top or system monitor process list.

---

### Post by renatkh on 2009-12-29
There's not much activity going on here. Any help on this issue would be great! I want to add that the CPU usage disappears with time without reboot and reappear again later. I don't know why, seemed random. I thought it is an overheating problem, however sensors show normal temperature (significantly below critical). I have noticed that my wlan card is pretty hot. If I turn wifi off it has no effect on CPU usage.
Is there any way to remove "[SOLVED]" from the title of the topic? It gives wrong impression.
Thanks to everyone.

---

