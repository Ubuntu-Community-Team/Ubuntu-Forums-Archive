---
title: "gam_server eating CPU...how to fix permanently?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by reuben on 2005-04-26
I'm getting tired of skill gam_server whenever my system slows down. Using top, if my system is sluggish, gam_server is almost inevitably eating 70% of the cpu. 

I read all the threads about it, and it seems that although this has been fixed in Fedora, it hasn't yet in Ubuntu. Correct? Or is there something I can do to fix this?

Thanks!

---

### Post by Leif on 2005-04-30
I don't think you can fix this right now, just killall it when it pops up. Hadn't realized this was fixed in fedora, but if it is, it should be fixed here too soon I guess.

---

### Post by KrIaXPaTaLa on 2005-04-30
Ran warty for a couple of months, never eard of such daemon. Upgraded to hoary today, and there it was, just a few hours after the last boot, eating 90% processor time. I was wondering if anyone with warty has this problem. Is it a kernel 2.6.10 bug? Is it a gnome problem?

Best regards,

Kriax, Portugal

---

### Post by sarimak on 2005-05-04
/usr/lib/gamin/gam_server doesn't eat cpu cycles for me but it keeps some file open from my download directory which resides on /mnt/data. Since I need to umount this volume before hibnernating I usually have to sudo kill -9 `pidof gam_server`...
aargh, Jirka

---

### Post by jonrkc on 2005-05-19
[QUOTE=sarimak]/usr/lib/gamin/gam_server doesn't eat cpu cycles for me but it keeps some file open from my download directory which resides on /mnt/data. Since I need to umount this volume before hibnernating I usually have to sudo kill -9 `pidof gam_server`...
aargh, Jirka[/QUOTE]
 I found gam_server consuming up to 90% of my cpu cycles and finally killed it with a sudo kill -15 [pid].  I tried resetting its niceness using top but it made no difference if it was given nice -20 or nice 20, it still tied up the cpu.  I hope I am not compromising my files by killing it...   But I can't just let the computer get tied up forever. 

I switched over to Ubuntu from Manddriva (Mandrake) 10.1 the other day and am loving Ubuntu, but I never had this problem one time with Mandrake.

---

### Post by skoal on 2005-05-20
Argh! Trying to remove gam-server pretty much leaves you with a console for your distro.  I get occasional kernel panics on shutdown/reboot because of the gam-server.

---

### Post by jonrkc on 2005-05-20
[QUOTE=skoal]Argh! Trying to remove gam-server pretty much leaves you with a console for your distro.  I get occasional kernel panics on shutdown/reboot because of the gam-server.[/QUOTE]
 Rather than try to remove it (I don't think I'd know how without guidance!) I just killed it when it was hogging the CPU yesterday.  I guess some Gnome application makes it start up, 'cause it hasn't been running today and I haven't run any Gnome apps (I usually run IceWM sessions, sometimes KDE, seldom Gnome).  My trouble yesterday was during an IceWM session but I'd been running Gnome things earlier in it.  I don't use Nautilus, but not sure I didn't invoke it unintentionally once yesterday.  

Anyway, it didn't seem to do any damage at all to kill gam_server.  Now I'm watching CPU usage frequently to see if it's normal.  So far, so good.

I do hope they get this fixed for the next release; it's the only really troublesome thing I've run into in my less-than-a-week with Ubuntu.  (The only other is that you can't easily get a command-line X login, which I prefer.  But it can be done!)

---

### Post by 23meg on 2005-05-20
it's my biggest complaint with Hoary. i hope it gets fixed sooner than the next release!

---

### Post by jonrkc on 2005-05-20
[QUOTE=23meg]it's my biggest complaint with Hoary. i hope it gets fixed sooner than the next release![/QUOTE]
Yeah, it really bothered me not only because things slowed to a crawl (and I was doing a download of Knoppix at the time, which it could have corrupted but didn't)--and especially because it really heats up the CPU, which I always try to avoid.  Can't afford new equipment every few weeks!

---

### Post by 23meg on 2005-05-20
right, it heats up my laptop up as well. no danger while i'm using it since i can intervene, but i'm worried that it's going to happen while i'm away. sometimes it's the little things that cause big trouble.

---

### Post by jonrkc on 2005-05-20
[QUOTE=23meg]right, it heats up my laptop up as well. no danger while i'm using it since i can intervene, but i'm worried that it's going to happen while i'm away. sometimes it's the little things that cause big trouble.[/QUOTE]
In fact, most of the time it's the little things, because the big ones get more notice!

I read a post somewhere by a man who turns his server off at night because his wife considers it a fire hazard.  At the time I thought, "That's pretty excessively silly."  The more I thought about it, the more uneasy I felt about leaving my machine (not a server) on all night--just so Linux can do its housekeeping and in case I get up in the middle of the night (I'm an insomniac) to look something up or something.  Maybe I should reconsider.

It sure doesn't help safety to have an unpredictable process ready to work your CPU to death!

---

### Post by fdoving on 2005-05-21
[QUOTE=jonrkc]In fact, most of the time it's the little things, because the big ones get more notice!

I read a post somewhere by a man who turns his server off at night because his wife considers it a fire hazard.  At the time I thought, "That's pretty excessively silly."  The more I thought about it, the more uneasy I felt about leaving my machine (not a server) on all night--just so Linux can do its housekeeping and in case I get up in the middle of the night (I'm an insomniac) to look something up or something.  Maybe I should reconsider.

It sure doesn't help safety to have an unpredictable process ready to work your CPU to death![/QUOTE]
 Please test my unofficial packages of gamin 0.1.0 at [http://frode.kde.no/ubuntu/gamin-hoary/](http://frode.kde.no/ubuntu/gamin-hoary/) and give feedback, less problems?, more problems? comments etc.

- Frode

---

### Post by jonrkc on 2005-05-21
[QUOTE=fdoving]Please test my unofficial packages of gamin 0.1.0 at [http://frode.kde.no/ubuntu/gamin-hoary/](http://frode.kde.no/ubuntu/gamin-hoary/) and give feedback, less problems?, more problems? comments etc.

- Frode[/QUOTE]I would like to, but don't feel confident or competent enough.  I hope another user here with this problem will test and report.

By the way, I haven't noticed gam_server running any time since that problem happened the other day, when I killed it to stop the fierce CPU activity.  I must have run something that I normally wouldn't have run, and that caused gamin to come into action.  But I have no idea what I ran...  Only noticed the problem, probably, quite a bit later.

---

### Post by jonrkc on 2005-05-25
I finally renamed gam_server to keep it from tying up the system, after it began doing it again recently and I couldn't even kill it (couldn't get its parent process ID anymore, in order to kill it).  

Now gnome complains about gam_server not being available.

So I downloaded the experimental packages but was unable to install them because of tons of dependency problems.

Maybe somebody with more expertise will be willing to give them a try.  Meanwhile I guess I'll just let gnome go on and complain, and hope that an official upgrade will be made available eventually.  I'm not willing to have to abandon everything I'm doing just because a routine doesn't run right--and furthermore could result in overheating my CPU if it decides to run amok while I'm away from my desk....

EDIT: I did a routine check for "broken packages" (first time I've done it) and was told gamin (gam_server) and its libraries were broken.  After some nail-biting I decided I'd let Synaptic go ahead and remove it, even though there was a heap of dependcies going with it.  I figured surely there was an easy way to get those back afterward.

Well, if there is, I didn't discover it.  Gnome wouldn't work; KDE was gone; I could still run good ole IceWM, but barely...  In short, my system was about shot.  

Luckily I hadn't yet destroyed the image I created my "new" hard disk from, and I was able to restore just about everything, though it took an hour of manual work to get things to run right.  

I guess I just don't understand enough about apt-get and its related software.  I thought surely when it got rid of those "broken packages" it would fix everything up again.  If I'd known I would lose my whole system, I'd probably have just left them there broken.  

Anyway, this reinforces my opinion of gam_server in its current state as a real troublemaker.

---

### Post by aronchi on 2005-05-27
gamin 0.1.0 solved my problem.
I suggest you to upgrade, if you can.

---

### Post by jonrkc on 2005-05-27
[QUOTE=aronchi]gamin 0.1.0 solved my problem.
I suggest you to upgrade, if you can.[/QUOTE]
 I'd gladly upgrade (especially after hearing that it solved your problem!) but as I said above, I tried and was presented with messages saying just about everything gnome-related would be removed from the system as a result.  How can I upgrade without destroying my setup and having to go through a three-hour process of restoring for the third time?

---

### Post by fdoving on 2005-05-27
[QUOTE=jonrkc]I'd gladly upgrade (especially after hearing that it solved your problem!) but as I said above, I tried and was presented with messages saying just about everything gnome-related would be removed from the system as a result.  How can I upgrade without destroying my setup and having to go through a three-hour process of restoring for the third time?[/QUOTE]
 Make sure you install both 
gamin_0.1.0-0ubuntu0.1_i386.deb and  libgamin0_0.1.0-0ubuntu0.1_i386.deb

I'd recommend doing this with 'sudo dpkg -i <packages>'
When both are installed the depends shouldn't be broken.

- Frode

---

### Post by jonrkc on 2005-05-27
Thanks, fdoving!  I downloaded them again and installed the way you recommended, and got no error messages or (apparently) any packages removed.  Now I'll see what happens next time gam_server swings into action.

Your post was very helpful.

And thanks to Aronchi for prodding me to try again!  :)

---

### Post by fdoving on 2005-05-27
[QUOTE=jonrkc]Thanks, fdoving!  I downloaded them again and installed the way you recommended, and got no error messages or (apparently) any packages removed.  Now I'll see what happens next time gam_server swings into action.

Your post was very helpful.[/QUOTE]
 Happy to be useful :)

---

### Post by jonrkc on 2005-05-28
Update...  Well, even with the revised version of gam_server, it still ties up CPU cycles, though so far not as severely as before.  However, it is impossible to KILL this process by any means I know: I tried using killall, kill -9, and kill -15 (having discovered a way to find out its parent process, by issuing ps alnx) and it just keeps respawning under different numbers.  

So I have renamed the directory again to prevent it from activating in the first place.

I'm glad this is being worked on, and hope it can be fixed in time for the next Ubuntu release....

(EDIT: It dawned on me a few minutes after posting this that gam_server most likely isn't re-spawning itself, but being invoked by some application or process I have running.  Not that that makes any difference to the inconvenience it causes, but just to clarify....)

---

### Post by RiotRick on 2005-06-17
[QUOTE=fdoving]Please test my unofficial packages of gamin 0.1.0 at [http://frode.kde.no/ubuntu/gamin-hoary/](http://frode.kde.no/ubuntu/gamin-hoary/) and give feedback, less problems?, more problems? comments etc.

- Frode[/QUOTE]

Had the same thing happening here. I installed your experimental packages. These seem to have fixed the problem so far. Hope it stays this way.

---

### Post by 23meg on 2005-08-22
the experimental package solved the cpu peak problem for me, but brought along two problems:

- i can't eject cds unless i run nautilus as root (even then it will display an error message, but will eject anyway)

- gam_server won't update the desktop

---

### Post by 23meg on 2005-08-22
update: both problems have disappeared after installing gamin 0.1.2-1 from debian testing. no cpu peaks so far either.

---

