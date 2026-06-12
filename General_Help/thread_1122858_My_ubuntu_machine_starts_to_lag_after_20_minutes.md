---
title: "My ubuntu machine starts to lag after 20 minutes"
date: 2009-04-11
forum: General Help
---

### Post by abhinav90 on 2009-04-11
I dont know but i have recently developed this problem in my ubuntu machine Intrepid 8.10. Earlier it use to work just fine. Now after 20 to 30 minutes of use it starts to lag and programs open very slowly. The lag becomes so bad that it takes me 5 minutes just to open up my System Monitor to see whats wrong. Is it a virus or something as i have both wine and a windows xp virtual OS loaded on my system.

PLS help any suggestions are welcome

---

### Post by Diabolis on 2009-04-11
Open System Monitor or run **top** in a terminal to see which application is using 100% of your CPU and post back.

To recover from that, just kill the responsible:
```
killall "app name"
```

---

### Post by abhinav90 on 2009-04-13
Ive already done that however, when i open system monitor it comes that system monitor is using up 45% of CPU and 2nd is something like firefox which is about 3%. Even after killing these processes the lag remains. I think it might be graphics card issue, as it usually starts to happen after a game or animation is run, I am currently using nvidia graphics card. Also i have seen that when the lag starts,, compiz which shows 0% CPU usage jumps as high to about 60% on using a feature like shifting workspaces, this usually takes up 2% under normal conditions, any idea why the lag is created.

---

### Post by Keith Hedger on 2009-04-13
Sounds like something is eating your memory,run ```
top -bn1
```
and check what is hogging the memory (bet its compiz!), then kill the offending process

---

### Post by WatchingThePain on 2009-04-13
Might be a memory leak.

---

### Post by 3Miro on 2009-04-13
Do you have any tools installed to monitor temperature. That might be the cause.

Even if you have problem with windows under Virtual Box (that can surely get a virus) or the more unlikely scenario of problem with wine, those would manifest only if VB or wine are working.

---

### Post by kelvin spratt on 2009-04-13
I had the exact same problem last week all I did was remove Xerver the reinstall don't ask
what the problem was. but alls well now.

---

