---
title: "Windows 7 theme"
date: 2012-05-18
forum: Desktop Environments
---

### Post by computeratin on 2012-05-18
Hi all,
 
I'm in the process of building a special project for my wife. I'm testing lots of stuff in a VM before I put it on hardware. I'm trying to get it to look as much like 7 as possible from the desktop. I've found several good themes to try. Only problem is they're all a year or two old and written for gnome 2.
 
I installed the gnome desktop + extras from the repos. But, when I try to install the themes they don't recognize the environment and refuse to run. So it looks like a G2 theme will not work in G3. ( I didn't realize that the desktop package was G3 when I installed it.)
 
I've been researching, and I'm stuck.
 
So I'm wondering:
 
1) Does anybody know if there are any good W7 themes for G3?
2) If I understand correctly MATE is a fork of G2. I'm wondering if I should try that route and see if it works or if that would just be a waste of time?
3) Does anybody know if there are any good GUI tools for recompiling a G2 theme in to G3? Doing so manually or by command line is well beyond my current skill level.

---

### Post by Frogs Hair on 2012-05-18
1. No, there is only one GTK 3 Win 7 style at Gnome look.org.

2. Mate may be the best option for running GTK 2 themes . You would have to make sure the Win 7 transformation packs are compatible. As you may know there is more than one available for GTK 2. 

3. GTK 3 theming is not for the beginner and the themes are made in different way than GTK 2. GTK 3 uses different theme engines also .

Consider Kubuntu or PCLinuxOS  in your testing also because they are closer to Windows in terms of how they look. Linux will not work like Windows no matter what theme you use, but you can make it look more familiar .

---

### Post by computeratin on 2012-05-18
Well, I think with the types of things that she does (send e mail / web surf) that if can can get it to look like 7 that will help a lot. It doesn't really matter to her what the "guts" are so long as the desk top works the way she wants.
 
This is actually a rather complicated project, with a lot of considerations and tweaks, that has had some extended discussion over in the security forum. I know *what* I need to do. Now I just have to figure out* how* to do it.
 
Creating a theme is beyond my skill level. Installing one I can do, if I can match it to an environment where it will run.
 
In the end I want to use VMware to create a limited use win vm to run dragon speak for dictation. Everything will be UB except office / dictation.
 
I want to use VMware's unity feature to intergrate the two OS's in to a single desktop.
 
I'll look in to the other two distros you rec'd.
 
I'm thinking about mint as well?
 
I know it won't be a perfect 7 rep from the DE. But, I want it to be no more dif than switching from XP to Vista to 7. (In other words still look like "Windows land")
 
You said you found a G3 win 7 theme? Could you drop me a link? I haven't found one yet.

---

### Post by Frogs Hair on 2012-05-18
Here is the link and the theme is not highly rated . [http://gnome-look.org/content/show.php/blue+7+theme?content=148167](http://gnome-look.org/content/show.php/blue+7+theme?content=148167)

This may work with mate but I don't know for sure . [http://www.redmondpie.com/windows-7-transformation-pack-for-ubuntu-linux-cid346/](http://www.redmondpie.com/windows-7-transformation-pack-for-ubuntu-linux-cid346/)

---

### Post by computeratin on 2012-05-18
> **Frogs Hair said:**
> Here is the link and the theme is not highly rated . [http://gnome-look.org/content/show.php/blue+7+theme?content=148167](http://gnome-look.org/content/show.php/blue+7+theme?content=148167)
 
This may work with mate but I don't know for sure . [http://www.redmondpie.com/windows-7-transformation-pack-for-ubuntu-linux-cid346/](http://www.redmondpie.com/windows-7-transformation-pack-for-ubuntu-linux-cid346/)
 
I'm at work right now, so I don't have access to my system. (I mailed myself the link to this so I won't loose it.)
 
This project is part practical concerns, part special concerns, a big part security concerns and an even bigger part is to just see if I can pull it off.
 
It will be my most complicated build of any kind to date. (And that's actually saying something. I love to build crazy systems.)
 
I'm going to have to up my skill level to make it work. (I've bought books, lots of books. I've been researching for a couple of months and I had a big conversation going with several people over in the sec forum for like a week.)
 
To make it all work I'm going to have to end up learning enough scripting to create a fairly complicated log on and log off script. I'll cross that bridge when I get everything else working. (But, I've never scripted anything before in my life.)
 
I already tried to install two well rated w7 themes. 
 
One, I followed all the directions in the tutorial but I couldn't run the *.sh after I DL'd it b/c I kept getting errors saying that it didn't belong to me and that I had to be root to run it? And I really don't understand why. From my very limited knowledge of *nix I didn't see any reason for it.
 
The second IIRC is the one that you linked to. It kept telling me that I had to be in a gnome session before the installer would run. (But, I'll try your link when I get home; just to be sure.)
 
Just for informational purposes: How hard would it be to get G2 installed and running on 12.04x64?

---

### Post by Frogs Hair on 2012-05-18
Here is a start as to what is involved. [http://developer.gnome.org/gtk3/3.0/migrating.html](http://developer.gnome.org/gtk3/3.0/migrating.html)

---

### Post by computeratin on 2012-05-18
Well quick research says that I can't put G2 on 12.04 b/c lots of stuff would break. I'm sure some guru could probabley fix it if they wanted to. But that would basically be making your own distro. And that's so far over my head it's not even funny.
 
And I looked through the link you gave me. Migrating a theme from G2 to G3 is also currently over my head. As is making one from scratch. Part of this is to challenge myself and learn new stuff. But, I can only take that so far. If it takes me a year to build this my wife *will not* be a happy camper.
 
So as I see it my options are:
 
1) MATE (in 12.04 or Mint 13) and just see what happens.
2) PClinuxOS and see what hapens.
3) Scrap a big part of the project that I really wanted to pull off.
 
Can you think of anything else that I could look in to trying?

---

### Post by rai4shu2 on 2012-05-18
Lucky for you, Mint 13 is in RC. So it probably will be out in another week or so.

---

### Post by tumutanzi.com on 2012-05-18
No, I just want to use the classic Gnome desktop, I.e. Gnome2.
But I think your project is interesting.

---

### Post by computeratin on 2012-05-18
New approach to bounce off the wall for input:
 
[Zorin OS]("http://zorin-os.com/") 5
 
It's built on 11.04 / G2.
 
It has a W7 theme built in. (It looks kind of basic from the screen shots.)
 
If I don't like it I *should* be able to install the better theme from Redmond Pie w/ Areo Glass for G2.
 
Then, update the core to 12.04.
 
I've tried something similar once before. I put Peppermint 2 OS on a VM. Then upgraded the core from 10.10 to 12.04. When the upgrade asked me if I wanted to over write any custom files I said no. I was *guessing* that the custom files were what made it "Peppermint".
 
When I was done it still looked like Pepperment and everything seemed to work fine. But, I didn't play with it very much.
 
Yes, no, stupid, worth a try, let the upgrade over write some or none of the custom files?

---

### Post by rai4shu2 on 2012-05-18
Zorin seems like a good way to go, but I don't know about its long-term viability. Zorin 6 Lite is based on Ubuntu 11.10, but Zorin 6 is going to be based on 12.04 and will use its own custom WM in Gnome 3. Just something to think about.

---

