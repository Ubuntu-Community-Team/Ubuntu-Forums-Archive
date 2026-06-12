---
title: "CPU temp monitor applet for panel: Where did it Go?"
date: 2005-03-22
forum: Desktop Environments
---

### Post by wbeck85 on 2005-03-22
Last week I installed Kubuntu preview amd64 on my computer and bumbled about a bit. But I wanted the gnome enviroment so i "apt-getted" ubuntu-desktop and all was well. I like to see my CPU frequency and temp, so i added the CPU frequency Scaling Monitor and the CPU temperature monitor to the top panel and all was good. But last night I downloaded the latest (March 21) ubuntu hoary preview iso for i386 because I am a homstarrunner fan :) (macromedia hasnt come out with 64bit flash yet :( ) So, i setup the desktop nicely, but, unfortunately the CPU Temp monitor applet is gone from the "Add to Panel" menu and I am dissapointed. Where did it go? do I have to install that seperately? is it inthe repositories (must be i guess?) By the way, the repositories are acting up at the moment. It is rather annoying.

---

### Post by smtanner on 2005-03-26
try emifreq

---

### Post by wbeck85 on 2005-03-26
[QUOTE=smtanner]try emifreq[/QUOTE]
 Yes, thank you very much. the emifreq program worked :) I apt-get installed it and there it was in the applet. Just like i had before. The only problem is that I restarted gnome and got some error saying that CPUfreq could not throttle the cpu. However, powernow is doing a fine job of that and emifreq is reporting perfectly well. Can I shut up that useless warning?

---

### Post by garion on 2005-07-23
I have the same problem of displaying this error message... I think it's because somehow the emifreqd is not started.  But emifreq-applet is in the right runlevel rc folders... I tried boot-up manager too which shows it is active at boot, still no luck.  Once you start the daemon, the error message is gone.  Anyone has idea?

---

### Post by müller on 2005-07-25
put the emifreqd in the startup programs
syst->pref->sessions

---

### Post by CameronCalver on 2006-05-20
Can some help me get a basic cpu temp monitor i downoaded emifreq applet from synaptic but how do i open it ?

---

### Post by karnonas on 2006-10-13
if your are using gnome... right click on your app panel and select the menu option: Add to Panel. Then there will be a Utility app that you can select called "CpuFreq Monitor". Click the add button and you will be good to go. Make sure that emifreqd is running before you try running the app or it will give you an error message.  :o)

---

### Post by karnonas on 2006-10-13
I have the problem of getting an error with the applet when ubuntu first loads up. It tells me that emifreqd daemon is not running and cannot adjust cpu frequency until it is running... so I run the cmd sudo emifreqd and the problem is fixed. Now i just need to figure out how to get emifreqd to startup in the sessions when ubuntu first loads up. I added emifreqd to the startup section in the ubuntu sessions but it is still giving me the error. It seems that the only way emifreqd will run is if you use root cmd like sudo. Does anyone have any ideas of what to do here? Let me know if ive just confused you more than you were before.

---

### Post by Craigus on 2006-10-28
I had this issue with Edgy and have resolved it by installing sensors-applet.

---

