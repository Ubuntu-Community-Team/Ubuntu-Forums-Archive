---
title: "RAM usage"
date: 2006-05-05
forum: Desktop Environments
---

### Post by raovq on 2006-05-05
ive noticed amarok running a little sluggishly. it has always been the case, but when i skip a song, it can be up to two seconds for it to stop the current track, and start the next. it's not a drama in itself, just something that bugs me. ive got a gaming rig with 1.5gig of ram, i expect a lil better, thats all.

But anyway, i decided to figure out what the deal was, and i checked the system monitor. It uses a staggering 100meg of ram. i can understand it using that much if it was doing something silly like downloading all the album covers at once or compiling a library or something, but to have a standard memory footprint of over 100meg is a bit much. It also on occasions can spawn multiple instances. Half the time when i check it, there are two identical amarokapp processes running at once. i can kill the inactive one quite safely, but i can't constantly check what it is doing.

other programs too use far more ram than you would expect. the weather widget thing, which downloads the forecast and radar map (although a great little program) takes up 20meg of ram. it has three windows, all of which are static. how can it take up so much?

this seems to be more of a linux thing than specific programs. i recently swapped over from windows, where i had it configured to run with minimal ram, and now a single media app takes up more than my windows box with an chat client, winamp and a browser did.

So, to make this a question, is there anything i can do to lower the ram usage in linux? is this just the way things are? should the programs be operating with these resources?

thanks.

---

### Post by ComplexNumber on 2006-05-05
i think the problem is an amorak problem rather than a linux problem. amorak is quite well know for its huge RAM footprint. its one of the reasons why i've never bothered with amorak.

> 
So, to make this a question, is there anything i can do to lower the ram usage in linux? is this just the way things are? should the programs be operating with these resources?no they shouldn't be operating with those resources. i suggest that you run gnome 2.14 because its memory usage is very good. your memory usage does seem a tad unusually high. if you can give a printout of the gnome-system-monitor readout, people may be able to spot the processes that are taking over the system

---

### Post by az on 2006-05-05
[QUOTE=raovq] should the programs be operating with these resources?

thanks.[/QUOTE]
Yes.  They would run much slower if they didn't use the ram.  Unused ram is wasted ram.  

The thing is the kernel will dump out unused memory cached with a low priority on-demand.  Don't worry, it is very efficient.

---

### Post by bluenova on 2006-05-05
Sounds like a normal amount of ram for amaroK. I think what would speed it up for you is to use a mysql database instead of sqlite:
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

The speed for me increased a lot after changing it to mysql.

---

### Post by RagingOcelot on 2006-05-09
yeah, it seems amarok uses quite a bit of memory for what it does.  My system is reporting 46 megs in use for it compared to XMMS taking up only 15.

---

### Post by RagingOcelot on 2006-05-09
also, from time to time, I notice a stray, dead amarokapp process still hanging around and of course using up another 46 megs of RAM

---

