---
title: "Panel style changed &amp; panel failure (U 10.04.4)"
date: 2013-01-08
forum: Desktop Environments
---

### Post by Metalpen1984 on 2013-01-08
Hi all,

I met a long-time-ago-but-not-yet-solved problem, the panel failure. It's like after restarting from update, I got a lot of "X widget is has quit unexpectedly" and "The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet"."

Another thing I noticed is the style of panel have changed from BLACK to light grey (just like xfce), and I don't have any clue for this situation.

I had tried every tips to fix that, not all in vain. Is re-installing the final solution? I would like to do, but then I have to rebuild those programs (scipy, ncview, etc.) I used for my work (I install Ubuntu for my science work, and it works perfect for me, even good for parallel computation). 

If it is necessary to re-install, please tell me, then I can quickly give up fixing it. Thanks!

My Hardware Spec: AMD64, 3.2GHz, 4GB ram, NVidia GT520.

---

### Post by ibjsb4 on 2013-01-08
Have you tries reinstalling the panel?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reinstall+gnome+panel+10.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reinstall+gnome+panel+10.04&as_qdr=all&sa=Google+Search&lang=en)

10o4 reaches end of life in a few months, maybe time to upgrade.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=upgrade+10.04+to+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=upgrade+10.04+to+12.04&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Metalpen1984 on 2013-01-08
> **ibjsb4 said:**
> Have you tries reinstalling the panel?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reinstall+gnome+panel+10.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reinstall+gnome+panel+10.04&as_qdr=all&sa=Google+Search&lang=en)

Thanks for reminding this, now it shows 
"warning: subprocess old post-removal script returned error exit status 245"

and

"dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 245"

I have checked this on Internet, and after trying the remove, purge, -f install, it does not work. Every action I took by aptitude or apt-get is blocked by 

"Errors were encountered while processing:
 gnome-applets"

Is there any way to by-pass this situation? Doing under tty1 (alt-ctrl-f1)?

> 
10o4 reaches end of life in a few months, maybe time to upgrade.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=upgrade+10.04+to+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=upgrade+10.04+to+12.04&as_qdr=all&sa=Google+Search&lang=en)

I was considering about this, but not this time....thanks anyway. I use 12.04 on another laptop, it does not reach the requirement as 10.04 for working.

---

### Post by ibjsb4 on 2013-01-08
Are you running a custom theme?

---

### Post by Metalpen1984 on 2013-01-08
> **ibjsb4 said:**
> Are you running a custom theme?

Surely, no. The only thing I custom for the Desk Environment, is adding some default applets.

I can say that it's like a totally default environment.

---

### Post by Metalpen1984 on 2013-01-08
I just solved it by my own.
The main problem is the libxml is not upgraded yet, hence the gnome-applets is not working fine and kept showing that "broken package".

The solution for my problem (and for other newbies) is
turn on the Terminal (or go to tty, alt+ctrl+F1), then type in:
```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```

Then my problem is fixed. :)

Thanks ibjsb4 for taking care of my problem.

---

### Post by ibjsb4 on 2013-01-08
Gnome-applets is a separate package.  I think I would try reinstalling it.

[http://packages.ubuntu.com/lucid/gnome-applets](http://packages.ubuntu.com/lucid/gnome-applets)

---

### Post by ibjsb4 on 2013-01-08
Nice job :) and welcome to the forums.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

