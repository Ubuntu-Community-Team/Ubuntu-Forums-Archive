---
title: "LXDoom will not run"
date: 2006-12-07
forum: Gaming &amp; Leisure
---

### Post by voided3 on 2006-12-07
Hello, I just installed LXDoom from the add/remove programs list on the applications drop down and when I run it it nothing happens. I ran "lxdoom" in the terminal and this the the output: 

LxDoom v1.4.4 ([http://lxdoom.linuxgames.com/](http://lxdoom.linuxgames.com/))
Z_Init : Allocated 6016Kb zone memory
IWAD not found


I am not familiar with what "IWAD" stands for. Does anyone have any ideas as to how I should go about getting this up and running? Thanks!

---

### Post by hikaricore on 2006-12-07
You need either a shareware or purchased copy of the actual doom "wads" (map,data,sound,gfx,ect package) to play.  If you don't have access to these there are several other versions of doom in the repos, like freedoom for example that I believe come with wads of some sort.

---

### Post by ravenus on 2007-04-15
I faced the same issue. When I try to paste the wad into the /usr/share/games/doom folder, I get the msg that I do not have permission to extract/move files into the folder. In fact I see that I do not have permission to modify any of the folders in filesystem despite being the only user and having the password for using synaptic and other administrative tasks. It says that the owner is root and I am not the owner.

---

### Post by noerrorsfound on 2007-04-15
> **ravenus said:**
> I faced the same issue. When I try to paste the wad into the /usr/share/games/doom folder, I get the msg that I do not have permission to extract/move files into the folder. In fact I see that I do not have permission to modify any of the folders in filesystem despite being the only user and having the password for using synaptic and other administrative tasks. It says that the owner is root and I am not the owner.
Try typing this in a terminal:
```
sudo cp /path/to/your/doom.wad /usr/share/games/doom
```
Replace /path/to/your/doom.wad with where your actual wad file is located.

---

### Post by ceil420 on 2007-04-16
What if you have the original Ultimate Doom (®1993-1996) CD? Is there a way to install it in linux? Or to at least use files from the disc for lxdoom?

---

### Post by noerrorsfound on 2007-04-16
> **ceil420 said:**
> What if you have the original Ultimate Doom (®1993-1996) CD? Is there a way to install it in linux? Or to at least use files from the disc for lxdoom?
You just have to copy the wad file from the CD to the path that lxdoom needs it in.

---

### Post by ravenus on 2007-04-16
Thanks I'll try that out, although after downloading a shareware demo, I thought the performance was pretty abysmal. But that may be because I was running it in a Beryl environment, the app didn't support fullscreen and maybe there was some conflict of allocating 3D card resources?

---

### Post by H.E. Pennypacker on 2007-06-09
> **hikaricore said:**
> You need either a shareware or purchased copy of the actual doom "wads" (map,data,sound,gfx,ect package) to play.  If you don't have access to these there are several other versions of doom in the repos, like freedoom for example that I believe come with wads of some sort.

I downloaded freedom from Synaptic and LxDoom played just fine.

---

