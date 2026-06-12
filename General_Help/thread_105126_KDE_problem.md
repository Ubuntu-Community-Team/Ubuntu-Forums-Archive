---
title: "KDE problem"
date: 2005-12-17
forum: General Help
---

### Post by Internet on 2005-12-17
I have a problem with KDE, I've tried searching about it but it's kind of hard to search for. In Gnome everything is perfect, but when I use KDE, I can still do everything but.. (this is where is gets hard to explain) it's like it somewhat lags/freezes up every few seconds. It's as if my computer started to do something that uses a lot of CPU resources but it's only for half a second and then it's fine again, and then it would be good for another few seconds and do it again. 

It's not a big problem, but I find it is worse in some programs than others. For example, XMMS is fine, and so is xine, but if I try to watch a video in Mplayer then it's really bad, so bad that I can't watch the video because it is constantly freezing every 2 or so seconds. And if I'm using firefox, or any other browser and i scroll down, it'll stop very 2 seconds then start again. It's like this every time I start KDE. 

Like I said, it's a hard problem to describe. I can't think of any better way to say it. Has anyone heard of or had this problem? It's not a big thing since I'm fine with using gnome, but I'd like to use KDE more. 

Thanks in Advance

---

### Post by kairu0 on 2005-12-17
Have you tried opening up top or ktop to see of something actually IS using a lot of CPU processes?

---

### Post by Internet on 2005-12-17
As far as I can tell, there isn't anything using up any CPU resources anymore than it would be in gnome.

---

### Post by Brando569 on 2005-12-18
KDE uses ALOT of memory compared to Gnome afaik, also your computer could be swapping things in and out, for right now thats all i can think of..

---

### Post by jjmckay on 2005-12-18
Here is a possible temporary workaround:

Open KDE System Guard and select the Process Table.  Is gam_server eating more than %1 of your cpu cycles?  This is what causes the same symptom as you describe.  Even just moving the mouse pointer around the screen shows this lag or jerkiness in KDE.

I've noticed this issue is very similar to Ubuntu bugzilla entries 18712 and 15420.  Here is what I sent to the person in charge of these bugs, see if it is similar to what you are experiencing:

I've installed kubuntu (5.10) 3 times and it symptom is still
exhibited each reload.  It happens when I access any NTFS partition in
/media.  The gam_server process goes from 0% to between 10% and 40%.  The more files there are in the folder that I'm using (either from command line
or konqueror), the more cpu is lost to gam_server.  A small folder
with say only 20 or 30 files, especially at first, will not cause a
problem.  A folder with a hundred or many more files will cause a much
larger impact from gam_server on cpu utilization.

Even at ten or twenty percentage of cpu lost to it, it slows the
desktop experience down very noticeably.

I've also noticed that if I unmount one of the partitions I was using,
gam_server drops to about %0 cpu utilization again.  Otherwise,
without a umount, gam_server will continue to eat cpu cycles.

I've compiled the newest version of gamin from the gamin page
(0.1.17), which did not fix this issue.  I presume I installed it
correctly, replacing the executable in /usr/lib/gamin

Also.. I use xmms to play mp3 files on the ntfs volumes.  Just playing
them does not seem to cause this issue with gam_server.

---

### Post by Ckytep on 2006-01-05
Registred this forum just to reply to this thread! Great forum by the way!

Finally I got some mor information about thiss issue, I have the exact sam problem as described here before.
The whole system lags and the cursor lag one time per second.

At first I only noticed it in "amaroK", but later also in "Kaffeine" in KDE. Soon I discovered that if I didn't try to browse my mounted NTFS-partition the lag would not appear.

And as you say here before, the lag becomes even worse if I browse many files in a single directory at the NTFS-partition.

Is there anything to do?

(By the way, I'm pretty new to Linux and (K)Ubuntu. Alot of things is great, really great with Linux, but I don't have cursor-lags in Windows...)

---

### Post by hvbakel on 2006-01-06
I had a similar type of problem, though the freezes didn't occur as often as you describe here (maybe once every 5-8 sec). Disabling the gam_server didn't solve the problem for me, but turning off both the battery monitor (I'm on a laptop) and superkaramba did the trick. I never figured out what the real underlying problem was though.

---

### Post by sharke on 2006-01-06
[QUOTE=hvbakel]I had a similar type of problem, though the freezes didn't occur as often as you describe here (maybe once every 5-8 sec). Disabling the gam_server didn't solve the problem for me, but turning off both the battery monitor (I'm on a laptop) and superkaramba did the trick. I never figured out what the real underlying problem was though.[/QUOTE]
I had the same problem when i was using Super Cybertron Kubuntu theme in karamba cpu usage would jump from 14% to 47% could not watch dvd or play games without stutter.

---

