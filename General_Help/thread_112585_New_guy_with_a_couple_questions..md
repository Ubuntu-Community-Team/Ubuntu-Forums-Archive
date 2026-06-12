---
title: "New guy with a couple questions."
date: 2006-01-04
forum: General Help
---

### Post by R3linquish3r on 2006-01-04
Hey all.

I just installed ubuntu and have a couple issues.....

First of all, I have ubuntu on my IDE drive, and Windows XP on my SATA drive. I am booting to my ubuntu drive. When grub boots it automatically launches ubuntu and doesn't give me a choice between taht and Windows.

Second, I installed the KDE package. As I was told by the person who helped me set this up was that when KDE installed it would give me an option to boot to ubuntu or kubuntu. I never got that option so it boots to ubuntu then I launch KDE.

Third, When I launch Synaptic I get and error saying: Conversation with su failed.

Fourth, When I boot KDE I get an error from Arts saying that it was shut down because of a processor overload.



I hope I can find some answers here. I've heard these forums are a great resource :D

---

### Post by taseal on 2006-01-04
1. if you want XP to launch, boot up from your SATA drive... if you want ubuntu to launch boot up from your IDE drive? grub is not going to give you an option if they are on diffrent hard drives... I'm almost positibe GRUB only works if both OS is on the same drive, but partitioned... 

2.there should be an option under where you enter the password... there are 3 buttons there, the far left one should let you select if you want GNOME or KDE, it will not say ubuntu or kubuntu, but you have to install GNOME for this.... go to terminal and type sudo apt-get install ubuntu-desktop (I think thats what it was)

3. hmm, thats weird, go to console (terminal) and type sudo apt-get update see if that helps, but I dont think if it'll have to do anything with the problem though =/ 

4.not sure on that one

---

### Post by R3linquish3r on 2006-01-04
Alright that'll have to do. Any idea's for the other problems?

---

### Post by R3linquish3r on 2006-01-04
Alright, I did that update, now it doesn't seem to want to start it at all.....

---

### Post by taseal on 2006-01-04
what doesnt it start?

and arent u on KDE? (kubuntu) I didnt know KDE came with synaptic, it should come with adept...

try this...

if you are in KDE (kubuntu)

go to terminal and type sudo adept

then when that comes up, press fetch upgrades and try to upgrade from there?

---

### Post by R3linquish3r on 2006-01-04
my main is unbuntu but i downlaoded the KDE package and run that. i dont have kubuntu though. ill try that though.

---

### Post by R3linquish3r on 2006-01-04
k i got adept thx.

another one for ya :D 

I downloaded Teamspeak

it has a file called setup.sh

it says when i open it that its bash file and when i execute it in the GUI itll run the installer. How do I execute it in GUI?

---

