---
title: "Ut 2004 under Linux low fps!!! HELP"
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by Neo4 on 2007-02-13
Well I've ubuntu edgy on my laptop 1,86 centrino x700

and when I'm running UT2004 the fps are about 90 on the first 5minutes of play after that they slow to 20 or 10! I've tried all resolutions, all configs at very low and low, all options disabled! and the fps won't rise!!!

i've ati drivers installed and running (fglrxinfo)
 
any idea to help me?

thanks

---

### Post by Neo4 on 2007-02-13
no one?

---

### Post by Sqwishy on 2007-02-13
are you using wine / cedega or did you use the linux installer?
Try disabling beryl when you play?

---

### Post by Neo4 on 2007-02-13
> **Sqwishy said:**
> are you using wine / cedega or did you use the linux installer?
Try disabling beryl when you play?


linux installer of course ;) 

how do I disable beryl?

the strange think is that the fps only decrease after 5m of play, the fist 5m the game runs excellent!

---

### Post by Rhubarb on 2007-02-13
If you've got Beagle installed (Applications --> Search), then that may slow down your computer after a few minutes to index everything in your home folder.
I'm not sure what else it could be, ... maybe a cron job or something?

---

### Post by Neo4 on 2007-02-13
yes I have Beagle but i don't have much things on my home folder to reduce fps about 80%!!!

what i think is that must be some think that is reducing my gpu power! first I thinked that should be eat because my laptop was really hot but i've put one fan sending fresh air to laptop, and it didn't get so hot and the game play was still horrible!

I'm getting real annoyed with linux!

---

### Post by Rhubarb on 2007-02-13
Maybe try killing the beagled process before running UT2004?
UT2004 runs well on my edgy machine, (I'm running an nvidia gfx chip here).

---

### Post by Neo4 on 2007-02-13
unsuccessful, just tried kill the program an run UT but the problem is still there. i Think that it must be eat problem because the fps decrease when the fan  that refresh my laptop starts running faster!  is there any program to control my fan?

---

### Post by Rhubarb on 2007-02-14
I don't know of any programs that allow you to control GPU fans (there might be something out there, I don't know).

It could be a simple dust problem.  In which case I suggest you turn your laptop off, get your vacuum cleaner out, and give it a good suck around your laptop vents - use a dry paint brush to get any stubborn dust clumps out.
You shouldn't need to disassemble the notebook.

There's a chance that the notebook manufacturers didn't put sufficient heat transfer compound between the GPU and its heatsink (apple had this problem not so long ago with their iBook range).
- In which case you might be able to get it fixed under warranty, ... or if you're feeling confident / adventurous (like I am), pull your notebook apart and put some silicon grease / silver heat transfer compound on the GPU / heatsink contact yourself.

---

### Post by Sqwishy on 2007-02-14
I don't think it's an overheating problem? Run 'top' in a terminal when you play and keep an eye on what is using your processor
are you running banshe music player?
to disable beryl right click on the icon in your notification area and choose metacity insetad of beryl

---

### Post by Yeeha on 2007-02-14
One thing u can try is change in ut2004.ini file under opengl settings VARSIZE to 64 from 32 whats default. That made mothership map playable for me. But generally game was still running slower than in windows for me in servers with custom maps and additional stuff and lag with high end graphics and low end was similar. Thing that helped for me was getting extra 512 ram to 1gb ram. It seems that 1,5gb ram is must for linux when u want to join server with custom stuff.

---

### Post by Neo4 on 2007-02-14
well it's an eat problem, I've posted on the laptop forum the problem.

if I supend my pc it will run always with the fan on the max speed (ubuntu bug) so I've done it and run UT and now it runs always good!

---

