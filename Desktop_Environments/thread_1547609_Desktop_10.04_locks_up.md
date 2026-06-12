---
title: "Desktop 10.04 locks up"
date: 2010-08-07
forum: Desktop Environments
---

### Post by n8nt on 2010-08-07
I have been running Ubuntu 8.04 or maybe it was 8.06 for over a year with no problems. However, I installed the Desktop 10.04 on two virtual machines and they seemed to run flawlessly. So finally I decided to load it as a replacement to my long running never failing 8.04. (It was so good I never even looked at the version.) 
 
First I decided to install the server version; so I loaded the 64-bit server version. It seemed to run fine but then I remembered that I wanted to continue doing mono and .net development so thought - no, I want the desktop version. So I installed the 32-bit desktop version (I told it to erase the disk and use the entire disk.) Well after it was up and running, I wanted to get the remote desktop running, but before I could get through the steps it took to get there, the screen and whole thing locked up. 
 
I tried re-booting, but again it locked up after a few minutes.
 
I thne tried re-installing; I noticed that at the end of the install where the dialog says to restart now, I clicked it and it went back to the terminal mode, spat out some commands, then spat out a whole series of I/O errors. I then hit the return key and it restarted.
 
Even after re-installing it still locked up after a couple of minutes. 
 
Next, I tried the 640bit desktop version. Same thing. Even the same thing when it was done with the install and waiting for me to hit the restart button.
 
I then decided to put the 32-bit version back in and run just the demo - the one that runs off the CD. It started as the others had, but then also locked up.
 
I'm hoping someone else has seen this and maybe has a clue as to what to do.
Since the server version seemed to run much longer and it has no GUI involved, I'm thinking that maybe it has something to do with the video. It has been over a year since I built that computer and I don't recall what it has in it, other than I know it has an INtel e2200 dual core 64-buit processor and a built in video card on the mother board. I will have to tear into it to find out what exactly those components are.
 
I'm trying one more idea - I've wiped my drive clean and am currently running kill disk on it. I'll try the install one more time.
 
I'm also looking to see if I can find somewhere the disk I used to install the previous version because I need it back.
 
Could it be due to my using a 64-bit system? Certainly, in 2010 that should not be a problem.
 
Thanks,
I'll be checking back.
 
Bob
 
-------------- 
I am back.
Cleaning the disc did not help.
 
I tried putting a video card into one of the pci slots instead of using the onboard video.  That let me boot and allowed the computer to stay up without locking up, but now the network would not run. 
 
I am going to go back to ubuntu 8.04 which has been running fine for over a year.
 
Reading the entries on this forum makes me think that 10.04 is not very stable. I'm a windows guy and have had my windows 2003 server running for almost 7 years now without a hitch. I'd like to believe in linux and ubuntu (unix is what I grew up on) but the pain is killing me.
 
Bob

---

### Post by n8nt on 2010-08-07
It is the next day. I re-loaded my Ubuntu 8.04 and had no problems. It does not lock up. But, I cannot download the latest mono-develop project; it seems to be only available on the 10.04 release of UBUNTU.
 
Are there any specifications for what hardware to use on a 64-bit processor?
 
Any favorite motherboards?
 
I have another machine that I will throw another hard drive into and try installing there. In the meantime I'm developing with mono-develop on my VMWare virtual machine with Ubuntu 10.04. I really want to put Ubuntu 10.04 on its own hardware.

---

