---
title: "frustrated user - random freezes - log shows clocksource tsc unstable"
date: 2009-02-14
forum: General Help
---

### Post by polobreaka on 2009-02-14
i have spent numerous hours reading this forum and there are a lot of great infos i have soaked into. 

ever since i started dual booting vista with ubuntu 8.10, i found myself to be using ubuntu 80% of the time. i really love how responsive it is, the effects, very little resource used, best of all its free. im averaging at 15-25% RAM usage under ubuntu, but when im on vista, it average at 50-60% usage. its the reason why i like ubuntu over vista right now. 

i have been a windows user ever since i started owning a computer and i consider myself an advanced user, definitely not computer illerate. i also find some programs in ubuntu very similar to Windows (terminal = command prompt, synaptic = add/remove program). ive been almost getting the hang of ubuntu and terminal common codes used. i really like it and i want to stick with it. eventually id want to convert over but this problem im encountering has been holding me back and in fact, is getting me pretty frustrating using this system.

i am getting random freezes while using ubuntu, doesnt matter what program is used, doesnt matter what time and i cannot duplicate it again. i usually wait it out for a couple of mins for the freeze to ride out and head over to the system logs to read what it is. it always shows up as "clocksource tsc unstable". i have research this for a really long time taking advice from numerous of members and other forum boards. mostly posted in other forums that the reason to this error is kernel panic. and a sign of kernel panic is when the caps lock led blinks. mine doesnt blink at all, its a pretty hard freeze. caps lock, num lock light doesnt blink when pressed. i cannot use my mouse at all. ctrl+alt+f1 doesnt work. 

i have tried: 
disabled compiz - still freeze
add line to menu.lst 'clocksource=hpet' - still freeze
change cpufreq governor to 'performance - still freeze

these are the 3 main advices across the board/google and i am running out of options. i would always monitor my cpu and ram usage, and it doesnt use up 100% ever.

here is my computer spec, hopefully someone with the same/similar system can help me out. 

**Intel Pentium D dual core 3.0ghz**
**2 gig ram (single channel)**
**1st hd sata 160 gig (NTFS)** - vista ultimate
**2nd hd ide 250 gig (EXT3)**- ubuntu 8.10 (kernel 2.6.27-11-generic, latest nvidia driver 180.29)
**3rd hd ide 400 gig (NFTS)** - shared drive (documents, media, programs)

unfortunately i will have to be running windows until i can find some resolution. i cant do work when it constantly freezes. i dont ever experience this when i run vista and i can leave my comp on for days without a freeze/crash when im on vista.

i have also posted this problem in the upgrade and installation section, not much help there. i have also responded to an already created post, no answer as well. hopefully someone can help me out. it seems as there are a lot of clocksource tsc unstable errors posted almost everywhere and doesnt seem to find a solution that sticks.


thanks all! you guys have been helpful.

---

### Post by Almat on 2009-02-15
Hi, Polabreaka

As i can see from your post you use the latest nvidia driver 180.29 which is not yet stable and gives random freezes. I had the same problem with new nvidia driver, i had freezes all the time and only power button worked so far. Currently one of the possible solutions is to downgrade the driver to more stable release. the problems with the latest nvidia driver are widely reported in various websites now. I have installed the previous version of nvidia driver and now i don't have any random freezes anymore. It is weird according to nvidia they fixed a lot of bugs in the latest driver however it seems to me something went wrong.

---

### Post by polobreaka on 2009-02-15
actually i was using 177 for a day or 2, and still have these random freezes. then i update to 180.22 for a long time, i still have freezes. it was only recently, like 2 days ago i update to 180.29. still thing, nothing has changed, still freezes.

---

### Post by polobreaka on 2009-02-16
anymore suggestions?

---

### Post by polobreaka on 2009-02-17
bumpppp

---

### Post by frecon on 2009-05-22
I'm also experiencing random reboots and freezes. Did you manage to fix it? I've started a thread about it here. [http://ubuntuforums.org/showthread.php?t=1126491](http://ubuntuforums.org/showthread.php?t=1126491)

---

### Post by pveurshout on 2009-09-05
I may be having the same problem, but on Jaunty. I also experience (seemingly) random system freezes, though I'm under the impression these only occur when I'm running a bittorrent client (Vuze, KTorrent, Deluge). Just like you I'm sharing an NTFS-partition with Windows where all my downloads go to, so it could be a problem with ntfs-3g or something. I have no idea how to confirm this, however. Someone have any ideas?

---

