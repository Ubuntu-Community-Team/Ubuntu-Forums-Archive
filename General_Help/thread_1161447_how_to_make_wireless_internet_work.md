---
title: "how to make wireless internet work?"
date: 2009-05-16
forum: General Help
---

### Post by gfunkera on 2009-05-16
sorry for newbish question...

i switched over to KDE from Gnome but i cant get online cause i cant find anyplace in Kubuntu to connect to my wireless network.. i found a network connections menu and entered the WEP and stuff but i cant find a place to actually activate the internet! what do i do??

also i also have seem to have lost the little icon in my Gnome panel which showed my wireless connection... how do i get it back?

---

### Post by PhilMize on 2009-05-16
are you running 9.04?

the network manager on 9.04 is **** wont work at all...

if your like me and are pretty proficient in gnome, installing synaptic will help out a lot in kde i really do not like the kde package manager.

After that your going to want to look up wicd which is a different network manager from the one packed with kubuntu. Ull see that one be removed and wicd take its place.

---

### Post by gfunkera on 2009-05-16
please help i screwed up big time! im sure this is not a big deal for someone who knows a thing or two about linux networking but i have no clue what to do because i cant seem to find any easy place in System>Administration or System>Preferences...

okay so i was trying to get my wireless internet connection to work in kubuntu and along the way i typed in this command in the terminal:
-----------------------
sudo aptitude purge network-manager
-----------------------

as a result i cannot surf the net at all!
i noticed that the aptitude installer informed me that some things were removed like "network-manager-gnome{a}".... "network-manager-kde{a}"... those are the only ones that i can remember... there might have been one or two more things that were removed...

i dunno what i did! how can i fix this?
the following is the output in terminal after i run the iwconfig command:
----------------------
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
---------------------

UPDATE: okay i did some fooling around, i dont know exactly what i did but i fixed the internet in gnome.... im scared! im gunna use synaptic to reinstall the stuff i mentioned earlier...

---

### Post by natman on 2009-05-16
Okay i am using 904 and had real internet problems at the start but i did fix them - please be advised my advice is based on my personal experience and dont take anything i say as gospel.

first off when i first installed i picked to partition manually as ext4 installed and them the problems started, wifi would show network name but never connect, anyway i used wired for a while but kpackagekit would never work at all. I got sick of this and did a fresh install under ext3. This time kpackagekit worked under wired finem but still now wireless. Eventually i decided to enable * Kwallet* and then wireless connected perfectly am happy ever since! No idea if Kwallet was the only reason but it semmed to help me out.

So are you using Kwallet? if not try using it.

---

