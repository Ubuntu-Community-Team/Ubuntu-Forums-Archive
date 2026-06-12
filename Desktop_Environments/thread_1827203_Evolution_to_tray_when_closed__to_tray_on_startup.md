---
title: "Evolution to tray when closed / to tray on startup"
date: 2011-08-17
forum: Desktop Environments
---

### Post by vanjadjurdjevic on 2011-08-17
I have a problem :S : I want to manage Evolution mail to start on startup and to be closed and moved to tray. I don't want to see the window it self but i want it to check the mail in background. The concept is similar do Kdocker and alltray purpose but i can't manage those apps to to that on startup. Thanks in forward!

---

### Post by dave01945 on 2011-08-17
you can set evolution to open at start up and to minimise to tray within evolutions preferences but for it to still run in the backround while minimised to the tray you will need to download a patched version of the evolution indicator. you can get the patched version with these commands

```
sudo add-apt-repository ppa:goehle/goehle-ppa
sudo apt-get update
sudo apt-get install evolution-indicator
```

hope this helps

---

### Post by vanjadjurdjevic on 2011-08-17
> **dave01945 said:**
> you can set evolution to open at start up and to minimise to tray within evolutions preferences but for it to still run in the backround while minimised to the tray you will need to download a patched version of the evolution indicator. you can get the patched version with these commands

```
sudo add-apt-repository ppa:goehle/goehle-ppa
sudo apt-get update
sudo apt-get install evolution-indicator
```

hope this helps

Thank you kind sir :)

---

### Post by vanjadjurdjevic on 2011-08-17
> **dave01945 said:**
> you can set evolution to open at start up and to minimise to tray within evolutions preferences but for it to still run in the backround while minimised to the tray you will need to download a patched version of the evolution indicator. you can get the patched version with these commands

```
sudo add-apt-repository ppa:goehle/goehle-ppa
sudo apt-get update
sudo apt-get install evolution-indicator
```

hope this helps

It works but not perfectly... it opens it on startup but so I can see it and i need to click anywhere on the window to minimize it finally. Is there a way to start it in background so I wouldn't see it ?

---

### Post by dave01945 on 2011-08-17
unfortunately thats the best i have managed with it too haven't managed to start it without it being visible first 

if i find a solution i will let you know ;)

---

### Post by vanjadjurdjevic on 2011-08-17
> **dave01945 said:**
> unfortunately thats the best i have managed with it too haven't managed to start it without it being visible first 

if i find a solution i will let you know ;)

I'll get onto it tomorrow when i wake up so keep me posted here in this thread with your progress. P.S. Is there a way to delay terminal command that is meant to start on startup (set up in "startup setting")?

---

### Post by dave01945 on 2011-08-17
it could be done the command **at** will run a command at a specified time ```
sleep 10 && command
``` 

will run the command after 10 seconds

---

### Post by Bobhuber on 2011-08-17
> **vanjadjurdjevic said:**
> I have a problem :S : I want to manage Evolution mail to start on startup and to be closed and moved to tray. I don't want to see the window it self but i want it to check the mail in background. The concept is similar do Kdocker and alltray purpose but i can't manage those apps to to that on startup. Thanks in forward!
My solution in Natty was to use the  mail app in cairo-dock. Works great.

---

### Post by vanjadjurdjevic on 2011-08-18
Ok I think I have a solution but I can't manage to try it out because I messed up my Evolution Indicator plugin so I will please you to try it out. So, the concept is following : 
1. put this in your startup query :
sleep 20 && kdocker evolution
2. make sure that everything in Indicator plugin settings in evolution plugin settings is set up properly :
Keep evolution running in background
hide Evolution on startup is ticked.
Try it out and let me know

---

### Post by dave01945 on 2011-08-18
unfortunately could not get it to work as intended if i let kdocker open evolution then it opens and hides at start up but when i click the mail icon it doesn't show my inbox. also when i open evolution by clicking mail when i close it again it closes fully and does not minimise to tray.

also if i get evolution to start itself kdocker gives the warning could not locate window for evolution.

this may work if i wasn't using unity but i haven't tried that yet

---

### Post by vanjadjurdjevic on 2011-08-18
> **dave01945 said:**
> unfortunately could not get it to work as intended if i let kdocker open evolution then it opens and hides at start up but when i click the mail icon it doesn't show my inbox. also when i open evolution by clicking mail when i close it again it closes fully and does not minimise to tray.

also if i get evolution to start itself kdocker gives the warning could not locate window for evolution.

this may work if i wasn't using unity but i haven't tried that yet

In my attachment there is a screenshot of my evolution settings so set them up like that and set this in startup : 
```
bash -c 'sleep 5; exec kdocker evolution'
```

LOG OUT AND LOG IN AGAIN and it should work except it shows evolution window for a sec and at first it doesn't show inbox status in notifier applet but it checks the server inbox like it is set up in settings and if you have a new mail it will show you a notification and then it will refresh the dropdown menu so it will show the current inbox status :) try it out and let me know does it work :0

---

### Post by vanjadjurdjevic on 2011-08-18
After 2 hours of trying i think there is no best solution to handle this. I think the best would be if evolution-indicator package team would optimize this for unity cuz this plugin works but it has some delay time on startup so it doesn't minimize the window imediately cuz the top bar embedding. :(

---

### Post by dave01945 on 2011-08-18
i was just thinkin the same thing i was just tryin another method added

```
alltray evolution
```

to startup applications but again it show evolution for a second or less when starting and the only way to open it again is by clicking contacts not mail

---

### Post by vanjadjurdjevic on 2011-08-18
> **dave01945 said:**
> i was just thinkin the same thing i was just tryin another method added

```
alltray evolution
```

to startup applications but again it show evolution for a second or less when starting and the only way to open it again is by clicking contacts not mail

A made a bug report on evolution-indicator launchpad so we'll see what they say.

---

