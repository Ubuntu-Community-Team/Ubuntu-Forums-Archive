---
title: "Eternal Lands install"
date: 2008-05-03
forum: Gaming &amp; Leisure
---

### Post by onana on 2008-05-03
I want to play Eternal Lands and I have found that it is native to linux. I am running Ubuntu 8.04 Hardy. I see the install instructions on the game page but I do not understand how to execute them. I am still pretty new to using the command line and I just dont understand how to install this game. Is there a possibility someone could walk me through the commands? I am really trying to learn how to use the command line effectively.

Thanks so much in advance to anyone who can help me out.

---

### Post by Perfect Storm on 2008-05-04
Here's a guide should work on 32-bit as well: [http://gaming.gwos.org/doku.php/guides:64bit:eternal_lands](http://gaming.gwos.org/doku.php/guides:64bit:eternal_lands)

---

### Post by Mongo5000 on 2008-05-04
Nice guide AI but I can't get it to go.

I followed it step by step, but when I click on the menu icon to launch the game, nothing happens.

I did notice that I couldn't find the sounds package to download and the name if the file is el_160_linux.zip.  I tried to alter the instructions to match this though.

Not sure where to start troubleshooting

---

### Post by Perfect Storm on 2008-05-04
```
sh ~/.Games/EternalLands-launch.sh
```
What does it say?

---

### Post by SimonHalliday on 2008-05-04
Oddly enough I have been trying to do exactly this. Similar problem - use the shortcut and nothing happens. 

When running 
sh ~/.Games/EternalLands-launch.sh

In the shell, I get:
/home/USERNAME/.Games/EternalLands-launch.sh: 4: ./el.x86.linux.bin: Permission denied

Don't really know what to do.  

When I have previously tried to run the ./el.x86.linux.bin (having compiled it from the source file), it crashes and gives me the following reason 
Segmentation fault (core dumped)

So yes, really not sure.

---

### Post by Grishka on 2008-05-04
> **SimonHalliday said:**
> Oddly enough I have been trying to do exactly this. Similar problem - use the shortcut and nothing happens. 

When running 
sh ~/.Games/EternalLands-launch.sh

In the shell, I get:
/home/USERNAME/.Games/EternalLands-launch.sh: 4: ./el.x86.linux.bin: Permission denied

Don't really know what to do.  

When I have previously tried to run the ./el.x86.linux.bin (having compiled it from the source file), it crashes and gives me the following reason 
Segmentation fault (core dumped)

So yes, really not sure.

you have to change permissions of el.x86.linux.bin. right click on the file, enter file properties and make it executable. if that won't do, there's always an option of running windows executable under wine.

---

### Post by SimonHalliday on 2008-05-04
Tried that.  Solved the permission denied problem. That was silly of me.  

However, like the previous one, it got to the same stage and then just dies.  Try to run it in terminal and get the same problem: 
 Segmentation fault (core dumped)

Would this result from me not having some necessary package installed or something? I followed this howto.  [http://gaming.gwos.org/doku.php/guides:64bit:eternal_lands](http://gaming.gwos.org/doku.php/guides:64bit:eternal_lands)

Edited the launch sh so it wasn't for 64 bit (as in the howto) but for others.  Didn't pick up anything else I might have done wrong.  

Anyway, will check this in the morning.

---

### Post by MicahCarrick on 2008-05-06
Hey guys. I installed Feisty on an old computer for my little brother. He's trying to install Eternal Lands and I've been helping him, however, we're stuck with a segmentation fault.

I'm thinking maybe his video card is the problem since it's relatively old. 

01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

Using the nvidia-glx-legacy driver.

Here is how we tried to run Eternal Lands:

```
sudo aptitude search libsdl-net1.2 libsdl-image1.2 libglu1-mesa libcal3d12
wget http://el.beplacid.net/downloads/el_160_linux.zip
unzip el_160_linux.zip
cd el_install
chmod a+x el.x86.linux.bin
./el.x86.linux.bin 

```

This results in "Segmentation fault (core dumped)" on his computer. However, it works fine on both of my computers.

Any thoughts?

---

### Post by Mongo5000 on 2008-05-08
So I was getting 

```
stephen@gutsy:~$ sh ~/.Games/EternalLands-launch.sh
/home/stephen/.Games/EternalLands-launch.sh: 4: ./el.x86-64.linux.bin: Permission denied
```

I made el.x86.linux.bin and el.x86-64.linux.bin both executable, now getting this 

```
stephen@gutsy:~$ sh ~/.Games/EternalLands-launch.sh
./el.x86-64.linux.bin: 1: ELF: not found
./el.x86-64.linux.bin: 2: Syntax error: "(" unexpected
```

Stumped

---

### Post by Perfect Storm on 2008-05-08
Guide updated.

Works fine with me. I'm on Ubuntu 8.04 64-bit - 8800 Nvidia. Which may have an impact is that I use the latest beta nvidia driver.

---

### Post by Cappy on 2008-05-08
> **Mongo5000 said:**
> So I was getting 

```
stephen@gutsy:~$ sh ~/.Games/EternalLands-launch.sh
/home/stephen/.Games/EternalLands-launch.sh: 4: ./el.x86-64.linux.bin: Permission denied
```

I made el.x86.linux.bin and el.x86-64.linux.bin both executable, now getting this 

```
stephen@gutsy:~$ sh ~/.Games/EternalLands-launch.sh
./el.x86-64.linux.bin: 1: ELF: not found
./el.x86-64.linux.bin: 2: Syntax error: "(" unexpected
```

Stumped

Are you running 64-bit Ubuntu?

---

### Post by Mongo5000 on 2008-05-08
nope, 32 bit.

But when I changed ./el.x86.linux.bin to executable, ran the command again that AI gave, it just switched to the ./el.x86-64.linux.bin one saying permission denied.

The only thing I can come up with from reading the guide again was this part.
```
 #!/bin/bash

cd ~/.Games/EternalLands
./el.x86-64.linux.bin
```

I've made the change to 
```
 #!/bin/bash

cd ~/.Games/EternalLands
./el.x86.linux.bin
```

Will retest and post results when I get home

---

### Post by Mongo5000 on 2008-05-09
> **Mongo5000 said:**
> nope, 32 bit.

But when I changed ./el.x86.linux.bin to executable, ran the command again that AI gave, it just switched to the ./el.x86-64.linux.bin one saying permission denied.

The only thing I can come up with from reading the guide again was this part.
```
 #!/bin/bash

cd ~/.Games/EternalLands
./el.x86-64.linux.bin
```

I've made the change to 
```
 #!/bin/bash

cd ~/.Games/EternalLands
./el.x86.linux.bin
```

Will retest and post results when I get home

That seemed to do the trick.

That will teach me for "adapting" instructions LOL

---

### Post by Perfect Storm on 2008-05-09
There's a reason why I call my guides Ubuntu 64-bit guides ;)
(Though I'm looking for someone who wants to write 32-bit guides).

---

### Post by rob2nd9th on 2008-10-25
Ok have followed the install but when I run it
It freezes at the Language selection screen??
any help would be nice this it the 4th install procedure I've tried!!!!!!!!!!!!!!!

---

### Post by Perfect Storm on 2008-10-25
Run it through the terminal and see what comes out.

---

### Post by rob2nd9th on 2008-10-25
> **Artificial Intelligence said:**
> Run it through the terminal and see what comes out.

If I run it from the terminal I get the same Language screen and freezes??

---

### Post by Perfect Storm on 2008-10-25
Properly not. It might show error outputs.

---

### Post by rob2nd9th on 2008-10-25
If I run "sh ~/.Games/EternalLands-launch.sh" from a terminal It tarts to load gets to select language screen and freezes?

When I tried the synaptic install I get to choose the server then it goes to the language screen and freezes?

If there is a mmorpg that easer to install??

---

### Post by Perfect Storm on 2008-10-25
> **rob2nd9th said:**
> 
If there is a mmorpg that easer to install??

Dofus is nice and not difficult to install.

---

