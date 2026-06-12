---
title: "Running Wow in Ubuntu"
date: 2007-10-06
forum: Gaming &amp; Leisure
---

### Post by Dopan on 2007-10-06
hey all, am new too this any help would be greatly appreciated :cool::cool::cool:

I've installed Ubuntu 7.04 onto my Toshiba Tecra M3. it is a 2ghz centrino with 2gb ram, it has an nvidia go 6200/6600 te (128mb) which it appeared to detect once things got up and running and sorted the drivers. all good. i installed latest wine and copied across my wow folder and attempted to run it. i managed to log in and select toon but it appears wow froze when trying to enter world (bar went right across but once across just sits there). i downloaded trial of crossover and installed. it has an option for wow but unfortunaly i didnt have cd/dvd handy. i noticed it had steam so i installed. downloaded halflife and attempted to play but graphics where screwed. 

i went looking further thru forums and what not and found someone that had changed settings in xorg.conf so i did and rebooted. retried halflife w/ crossover and seemed to work fine. no sound but graphics where ok.. 

retied wow with crossover and all appeared to work fine. but after a little while it just seems to shutdown?! has done it twice to me now. dosnt turn straight off. goes thru process of shutting down.. 

just wondering if there is a log of some kind that could tell me what its getting upset about and causing it to shutdown? also is there anything obvious that im doing wrong ? could it be graphics card related? if so what ways could i test this to confirm or eliminate. the laptop came with winxp and i had been running that for 12 - 18 months. 

again anyhelp would be appreciated. dont wanna have to go back to winxp im enjoying ubuntu on other levels just be nice to get a couple games working :)

---

### Post by Dopan on 2007-10-06
have been trying some other things and managed to get ubuntu to crash while not running wow...

i found a thread that said to run the following commands....

scooter@scooter-ubuntu:~$ glxinfo |grep direct
direct rendering: Yes


also to test the 3dfx by running glxgears in full screen.
scooter@scooter-ubuntu:~$ glxgears
15824 frames in 5.0 seconds = 3164.176 FPS
3735 frames in 5.0 seconds = 746.924 FPS
3732 frames in 5.0 seconds = 746.306 FPS
3733 frames in 5.0 seconds = 746.451 FPS
3736 frames in 5.0 seconds = 747.185 FPS
3733 frames in 5.0 seconds = 746.411 FPS
3735 frames in 5.0 seconds = 746.954 FPS
3736 frames in 5.0 seconds = 747.173 FPS
3738 frames in 5.0 seconds = 747.570 FPS
3720 frames in 5.0 seconds = 743.997 FPS
3737 frames in 5.0 seconds = 747.250 FPS
3734 frames in 5.0 seconds = 746.663 FPS
3708 frames in 5.0 seconds = 741.552 FPS
3737 frames in 5.0 seconds = 747.366 FPS
3732 frames in 5.0 seconds = 746.266 FPS
3733 frames in 5.0 seconds = 746.509 FPS
3717 frames in 5.0 seconds = 743.330 FPS
2581 frames in 5.0 seconds = 515.981 FPS
1352 frames in 5.0 seconds = 270.230 FPS
1350 frames in 5.0 seconds = 269.991 FPS
1359 frames in 5.0 seconds = 271.717 FPS
1359 frames in 5.0 seconds = 271.777 FPS
1350 frames in 5.0 seconds = 269.873 FPS
1354 frames in 5.0 seconds = 270.755 FPS
1359 frames in 5.0 seconds = 271.714 FPS
1351 frames in 5.0 seconds = 270.160 FPS
1358 frames in 5.0 seconds = 271.537 FPS
1356 frames in 5.0 seconds = 271.038 FPS
1357 frames in 5.0 seconds = 271.219 FPS
1357 frames in 5.0 seconds = 271.367 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
scooter@scooter-ubuntu:~$ 

seems to be a bit of variation ? this was after about 3 - 4 minutes....

when it crashed on me before i had the glxgears running fullscreen on another workspace while i was looking at forums and it just shut itself down...

---

