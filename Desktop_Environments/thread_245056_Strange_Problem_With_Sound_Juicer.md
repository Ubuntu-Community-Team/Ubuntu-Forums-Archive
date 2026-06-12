---
title: "Strange Problem With Sound Juicer"
date: 2006-08-27
forum: Desktop Environments
---

### Post by woody1989 on 2006-08-27
I'm having a strange problem with sound juicer in ubuntu 6.06 LTS. At least I think it's sound juicer causing the problem. When I rip CDs using sound juicer the files look like mp3s with a .mp3 extension but nothing will read the metadata so as a result I have no library in rhythmbox or amarok. xmms and banshee however read the info fine.But i think xmms just uses the filenames. I'm not sure. 

I think it might be the way gstreamer0.10 is set up. the command im telling sound juicer to use for encoding is 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

but I have always used this command and never had this problem before 

I also have a load of random wavs in my home folder now. It wouldn;t bug me so much because banshee can find the info ok. I just don't like using banshee that much and I have to enter the data manually when i want to put tracks on my ipod. VERY annoying when i have a 4gig cd collection. 

update: 
Okay so it's not all sound juicer's fault just grabbed grip and i think it's something wrong with lame but im not sure what. same thing happens with tracks taken using grip.
Any suggestions greatly appreciated 
Kind Regards 
Woody.

---

