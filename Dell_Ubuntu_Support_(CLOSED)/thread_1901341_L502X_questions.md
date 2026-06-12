---
title: "L502X questions"
date: 2011-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by demon68 on 2011-12-28
Hi,
I have a Dell L502X, and I'd like to switch form Win7 to Ubuntu, but I'm not sure what currently works, and what doesn't. There are some device-specific questions I haven't found the answer for.

[LIST=1]
[*]Does Ironhide/Bumblebee work well with it?
[*]Is there driver for the JBL Maxxaudio?
[*]Is battery life better or worse than on windows (with normal use)?
[*]Do the touch buttons and wifi/battery indicators near the power button work?
[*]Do multi-touch gestures work?
[*]On windows there's a power management setup that applies different settings when the laptop's connected to a power source, lid is turned down etc. Is there something like this for Ubuntu? 
[/LIST]

---

### Post by jerrrys on 2011-12-29
Why not just install ubuntu inside windows and play with it for a while.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wubi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wubi&sa=Search&cof=FORID:9)

---

### Post by n_u on 2011-12-29
Hi. I have a l702x, so quite similar to your dell. 

1. Can't really answer. Ironhide didnt work well (could disable the nvidia card, but ubuntu crashed by using vlc..) Bumblebee does work, but i couldn't disable the nvidia card -> what makes is impossible to use ubuntu without power source.
2. Nope, or hasnt found one jet.
3. much worse (2-3 hours vs 8-9 in windows. With ironhide and nvidia disable i could get a max of 4-5hours, still worse than windows)
4. Yes they work, but different. 
5. Nope, or not yet @ my dell.
6. yes powermanagement based on when its connected to a power source is available in ubuntu.

---

### Post by demon68 on 2011-12-29
> **n_u said:**
> Hi. I have a l702x, so quite similar to your dell. 

1. Can't really answer. Ironhide didnt work well (could disable the nvidia card, but ubuntu crashed by using vlc..) Bumblebee does work, but i couldn't disable the nvidia card -> what makes is impossible to use ubuntu without power source.
2. Nope, or hasnt found one jet.
3. much worse (2-3 hours vs 8-9 in windows. With ironhide and nvidia disable i could get a max of 4-5hours, still worse than windows)
4. Yes they work, but different. 
5. Nope, or not yet @ my dell.
6. yes powermanagement based on when its connected to a power source is available in ubuntu.

Thanks for your answer. I've installed Ubuntu, but I'm not sure if I managed to turn the discrete card off with Ironhide. The Ironhide indicator does write that the dedicated card is off, and in System Information 'Graphics' is Intel Sandy Bridge, BUT the fans are on, blowing out hot air, and the battery life seems very poor, I get a 1.5 hour forecast from Ubuntu starting from 100% battery. Is there a way to test if the nVidia card is turned off?
Also 'Ironhide Application Settings' doesn't work, and I had 'Unknown' written in System Information for the graphics before installing Ironhide (I tried with both restricted nVidia drivers).

---

### Post by demon68 on 2011-12-29
I just checked your [thread]("http://ubuntuforums.org/showthread.php?t=1901550"), guess we have the same problem with Optimus running the nVidia card on idle.

---

### Post by 14quartz on 2012-01-03
Have you tried 
 
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
 
but instead of ./test_off.sh use sh test_off.sh

---

