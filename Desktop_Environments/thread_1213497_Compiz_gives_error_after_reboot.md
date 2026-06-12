---
title: "Compiz gives error after reboot"
date: 2009-07-14
forum: Desktop Environments
---

### Post by KinKiac on 2009-07-14
Im new to ubuntu and Linux so please bear with me a little.  Im running 9.04 with an nvidia 7600gt.  Im running the nvidia 180 drivers for the video and it was working fine when I set it up.  I installed a few themes, got compiz going with the cube setup, and my desktop was starting to take shape the way i want it to.  Then I had to go to bed(it was 6am by that time) so I did a shutdown.  The reason I shut it down is the last time I left it running it ran into an error and froze up the entire PC.  So this time I shut it down at night(well morning for most people, lol).  The next day when I booted up it came up to the desktop fine but I noticed the cube functions weren't working, so I tried to launch CCSM from the preferences menu.  when i selected it it gave an error saying "input/output error in ccsm".  Im assuming Im going to have to reinstall ccsm, but does anyone know what may have caused the error and how I might avoid it in the future, or if i even need to reinstall ccsm?  Any help would be greatly appreciated.  If anyone needs more info on my system just let me know and Ill post it when I get home.

Thanks
Kin'

---

### Post by sharathpaps on 2009-07-15
KinKiac, Buddy I know this is not gonna be of any help. I'm in the same boat as you are and sometimes I don't find answers here (thats rarely). I don't have the faintest idea about whats causing your problem but did you try googling the error message that you get? Like its often said on these forums...Google is your friend :-)

Just trying to help because I don't want you going off Ubuntu because of this..

---

### Post by ~sHyLoCk~ on 2009-07-15
What happens when you try ```
compiz --replace &
```
If that works put it in your Startup applications!

---

### Post by KinKiac on 2009-07-16
Actually, I ended up re-doing my whole installation(third time in about 2 weeks, lol) and now Ive got everything working fine, except for wireless(auto connection keeps reading my WPA network as WEP and wont let me switch to WPA, manually configured connection just wont connect, keeps asking for password after timing out) but that's another issue.  Ive recently moved my PC to where a wired connection is available so Ill tackle the wireless issue another time.  

I dont know what screwed up the first 2 times, or maybe it was just my lack of experience in getting things going that made the difference.  After my last try I knew exactly what order to do things and what I wanted to do.  

Ive been able to get compiz to work, internet is speedy, system is stable and isnt freezing up like it did before, and Ive found the tutorial on restarting using the alt+sysrq to avoid having to hard kill my PC when it freezes up on me and I think that will definitely make a difference in the long run.  I found out the hard way that Ubuntu(and prolly Linux in general)doesnt take as well to killing your system as Windows does.  

All in all Im very impressed with Ubuntu.  My girlfriend, well she's another story(yes I do have a GF, lol).  There isnt a chance of me giving up on ubuntu or linux in general simply out of principal.  Im sick and tired of either having to pay 100-300$ every couple years just to get all the new features for my OS, or getting a pirated version which is the other option.  Its nice to be able to get everything I want without having to pay huge amount just to get sufficient software to protect my system and files.  Although I wouldnt consider myself just a freeloader either, I have no problem helping out others with Ubuntu and Linux and contributing to the community, its just that at my current skill level Im kinda useless ATM.  Im learning though and grateful for the help I get.  Its just going to take time for me to learn.  Im sure Ill even get my GF to come around eventually, she just had a bad experience with linux in the past and doesnt have the patience to wait while I learn how to run Ubuntu in the same capacity as I can run windows.  So, I keep windows around mostly for her.  Also, part of the reason I decided to come back to Ubuntu is that I work an IT help desk as a systems operator and monitor a bunch of servers, a few of which are running Ubuntu server edition, as well we have some other systems running a custom version of Ubuntu, so I wanted to learn more for work purposes as well as personal reasons.

Thanks for the suggestions though, I really appreciate it.

---

