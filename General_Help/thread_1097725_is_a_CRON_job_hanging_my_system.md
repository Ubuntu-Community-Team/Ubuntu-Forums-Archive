---
title: "is a CRON job hanging my system?"
date: 2009-03-16
forum: General Help
---

### Post by theDaveTheRave on 2009-03-16
Hello all.

I keep having my desktop hang, for no apparent reason.

I am including a copy of the var/log/syslog for you to look at, to see if you can see anything where I am missing something?

all I have been able to find is that there are CRON jobs running just before the hangs occur?

What I am doing at the time of the hang is normally the following.

Programing (usually in NetBeans).
I may then either open a new window in an Explorer, to view the javadoc, or alternately I may compile my program (from within netbeans).

I'm not sure if it is a netbeans problem? However I haven't had this issue with my laptop.

The laptop is running much less memory (500mb compared to 2GB), and a much slower CPU (1.6 Ghz compared a dual core athlon) - although the laptop does have a huge part of my disk set over to swap - 5GB, as I don't have disk space issue.

Are there any other interesting log files that I can post to help you guys out??

advice is appreciated.

David

---

### Post by AliTabuger7 on 2009-03-16
I believe I have been having this trouble too. You can check your System > Administration > System Log Viewer

You should be able to see it in auth and a couple other logs (like syslog, i think).

---

### Post by theDaveTheRave on 2009-03-17
Ok....

so I've checked the other various log files, and there is nothing that is occuring at the same sort of time??

I have initiated a "sort of" solution, and that was to turn off compiz fusion (but I did like my spinning desktop cube!), this isn't running on the laptop.

That seems to have "solved" the excessive memory use.

I've also just realised the other difference between the laptop and desktop, the laptop is 32 bit, whereas the desktop is 64.

I will report back if there are any further "hangs" of the system, but I suspect that it will be OK now that Compiz is turned off!

David

---

### Post by theDaveTheRave on 2009-04-16
Hello again all.


I am still having this issue with my system hanging?

I don't really feel that the desktop is particularly "underpowered" but if anyone is still following this thread and can give advice I would be really pleased.

The desktop is running a dual boot of XP and Intrepid. In fact in XP the window rendering is atrocious, and I get "streaming" when ever I move windows around.....

The spec.
It's a Dell Optiplex 740 (as far as I know it is as standard)
AMD Athlon x2 64Bit
On board nvidia graphics
1 Gig memory.
(I believe that it has sound somewhere too, but I never use it!).

This to me seems like a reasonable machine (not amazing, but should be sufficient I feel) especially when I compare it to the old pc's I used to run with Caldera linux and SuSe 7.4.

However I do now do a "lot" more with my pc.

Typical running application when I get a "hang"

in background
VMware Server.
LDAP
MySQL
Various Java stuff - such as derby, glass fish etc which I guess I could turn off, as I'm currently not using them.

running applications

NetBeans - developing various database applications (Open source of course!)

Dia - a really neat little diagram / graphical UML tool (I use it to "visualise" my DB structure and Java program.

I also have a number of monitors, including system load, memory load etc, and all of these go to the max just before I get my problems (in fact the memory is on the max as soon as I start up netbeans, which lead me to start [this thread]("http://ubuntuforums.org/showthread.php?t=1106161") in the hopes of reducing my system load.

I have a virutal desktop (7 screens) but often only have 1 item on each, most likely I will have nautilus running, as well as a 2 terminals (one logged into mysql), possible firefox, and gedit, each on a separate "desktop".

I get the feeling that this is netbeans related (or java related somehow), but I don't know how to prove this?

I also have a strange error message at boot up saying <aperture beyond 4GB> this seems to be an intrepid 64 bit bug related to either the motherboard or chipset, here is the [launchpad page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070").

I'm not sure I understand why I'm getting this above error when I only have 1 Gig of memory in my system.

Will upgrading the graphics card help in this situation? or the memory?


Thanks for any advice guys

David

---

### Post by theDaveTheRave on 2009-04-23
BUMP

please help me...

As I said, I don't have an issue with my laptop, I may "go quiet" for prolonged periods (often due to an infinite loop in my programming code!), but eventually the system will kill the process, and everything is back to normal....

On the desktop however, the processes seem to hand for much much much much much longer, in fact as we speak the system has now been "static" for nearly 15 minutes...... :confused:

Maybee I need to re-install the system, and just get MySQL a browser and java stuff (netbeans etc) running, so see if it makes any sort of difference, and a really "cut down" system... but I'm not sure if I'm going to make any sort of difference to the system?

I really need some advice on how to trouble shoot this issue, please help...

David

---

### Post by AliTabuger7 on 2009-04-29
I was having a similar problem. I think it ended up being a problem with my RAM. 

Wouldn't hurt to do a memtest. (grub boot loader option)

---

### Post by theDaveTheRave on 2009-05-01
AliTabuger7

Thanks for that response. 

I never even thought of that, I was a bit surprised to get a response, as I had none for such a long time!

I'll check this out on monday morning when I am next in the office.

I guess I'm being lazy but.... do you have any links for what the results of such a test will tell me, as I don't even know what I may be looking for, let alone what the results will tell me, as I say I guess I can always google the results afterwards!


thanks in advance.

David

---

