---
title: "GXine: .avi works, but no video from DVD"
date: 2009-05-11
forum: General Help
---

### Post by Dantravels on 2009-05-11
Hi I have two computers running Jaunty and the Desktop (my son's) has a problem playing DVDs in Gxine and VLC.  

[LIST]
[*]disks with AVI movies work well, but only real DVDs are the problem.
[*]The wierd thing is that I can hear sound but cannot see anything.
[/LIST]

The only message is about "permission" that I might not have to play it. 

Is this a region issue? How to change it? (I dont think its a region 1 or 2 issue, but i might have that wrong). 

This desktop box looks to be 3 years old, from some office, with 512 RAM, and which my friend put in a 100gb disk. HP Compaq written on it, with an ASUS DVD burner/player. I 

Other graphics work, like kids games. 

Thanks for any help! 
Dantravels

---

### Post by AndThenWhat on 2009-05-11
You probably need to install DVD encryption support.  Open a terminal (Applications -> Accessories -> Terminal) and try these commands:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

---

### Post by Dantravels on 2009-05-18
Thanks AndThenWhat, I worked on these issues for some time now.  The medibuntu stuff : all installed, ad infinitum. The main issue is about not being able to access the "resource" usually on a permission issue. 
 
And yet, the CDRom is accessible becasue i can run .avi videos with sound and video. 
 
All codecs files are installed, and the region issue should be ok, too. 
 
Now, even the games don't work (edubuntu) : no sound at all, and most games run like a stop start game, and i notice the the processor value on the system monitor is running at 70 to 80%.  Am i right in saying that this much juice should not be sucked out during these simple games?

---

