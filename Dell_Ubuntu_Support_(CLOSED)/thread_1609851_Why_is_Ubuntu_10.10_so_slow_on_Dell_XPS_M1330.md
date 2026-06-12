---
title: "Why is Ubuntu 10.10 so slow on Dell XPS M1330?"
date: 2010-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drmarkandersen on 2010-10-30
I have a Dell Vostro 420 desktop at my office. I put Ubuntu 10.10 on it recently, and it's working beautifully. (I'm dual-booting with Windows Vista, but using Ubuntu practically all the time.) As a long-time Windows user using Linux for the first time, it's easy to see why people love it. 
Yesterday, encouraged by my experience with the desktop machine, I installed Ubuntu 10.10 from the same CD onto my Dell XPS M1330 laptop, and it's so slow as to be practically unusable. The CPU hardly ever gets below 100% (according to the Sensor Screenlet), and I gave up trying to install LyX after waiting over an hour (it took a couple of minutes on the Vostro). I feel like I'm back to the bad old days of working on a 300-baud terminal. The processor is Intel Core 2 Duo T9300 25. GHz, 4 GB RAM, NVIDIA GeForce 8400M GS graphics. For now, I'm leaving the Linux partition on the laptop, but I've gone back to using the Vista partition to actually get anything done. I'd really appreciate any advice anyone could give me on making Ubuntu usable on my laptop.
Also, I'm about due for a new laptop. I'll probably want to dual-boot it as well, and I'll probably want to stick with Dell ('cause I get a good deal through my university). Any advice or cautionary tales would also be appreciated.

---

### Post by garvinrick4 on 2010-10-30
There is no reason why that machine is using so much of the processor to run Ubuntu.
Find out what is running all the time to use the processor. It is something sucking up 100% of the machine. Try System Monitor to see what problem is. I use maybe 3 to 15% of a dual core Intel machine and run 3 different Operating Systems in Linux, Ubuntu being my home system and never have that problem. Have heard of something running and using all the processor in other Threads, find out what it is so you know or do a clean install in that partition. If you find post in your thread here. By the way I have 4 gigs of RAM and use 600 meg at a full gallop. If anything Linux uses less than Windows by far of processor and RAM in my personal use.

---

### Post by garvinrick4 on 2010-10-30
Dell gives you a version of Microsoft Windows without the drivers and then a seperate disk
with a load of their proprietary drivers that run there machines. They do not use proprietary hardware but Intel and such. I believe they want to be able to smack you on the knuckles if you get to far away from Dell so they do not use the regular drivers in the DOS kernel that are more or less public domain. But in Ubuntu their is a special section for Dell users because of driver problems, Broadcom cards and such for wired and wireless connections and Video drivers are the ones that come to mind. Dell is a huge corporation and I am sure have their advantage for some things but I as an open source user do not like what they do to their customers to keep them dependent upon Dell. Their are a lot of
Dell users on these Forums that run Ubuntu and a lot of help. Enjoy your Ubuntu linux.

---

### Post by hipikll on 2010-10-31
80 % success: Install the appropriate driver for video card. You can see that Xorg is taking too much processor time. If you install right driver for video card, it will decrease CPU usage.  run top command to see, which one process is taking your cpu high.

---

### Post by drmarkandersen on 2010-11-01
Not sure how to tag the thread as SOLVED, but it appears that I have solved the problem by installing the proprietary NVidia drivers. All is well with the world. :)

---

