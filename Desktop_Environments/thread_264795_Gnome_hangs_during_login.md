---
title: "Gnome hangs during login"
date: 2006-09-25
forum: Desktop Environments
---

### Post by fox_nl on 2006-09-25
After entering my username and password to login in the graphical login-screen, the screen goes blank (normal brownisch background color) and after that everything stops. No splash screen, no desktop, nothing.

Using CTRL, ALT F1 I can enter a command line and log-in. Where can I look to find the cause of this? Or can anyone tell me how to get this fixed?

---

### Post by simpo666 on 2006-09-25
I just install ubuntu and got the same problem when i rebooted, stuck on the reddish background after login, with no actual desktop

---

### Post by fox_nl on 2006-09-25
This happened to me when I turned on my computer after I came back from my holiday... 

My guess is that it has to do something with an update performed in a previous session. However I don't have a clue which packages were updated or what could be causing this.

---

### Post by simpo666 on 2006-09-25
I havent added much, I only tried to get my wireless network card working and connect to the net, which i couldnt, so I'm pretty limited in what i have installed, so hopefully some-one can help fix this problem

---

### Post by simpo666 on 2006-09-26
bump, i really need help

---

### Post by RikoW on 2006-09-26
Did you guys wait some time (I mean minutes) to see if the login then proceeds?

That's what is happening here (ever since some kernel upgrade some time ago, not the most recent one). As far as I could trace it down, the start-up of the ESD damon hangs or takes a long time. After that is done, login proceeds, just takes a long time. The only solution I found so far (which in fact is not a solution for me) is to turn of ESD in System -> Preferences -> Sound.

It's pretty annoying ....

Cheers,

               Riko

---

### Post by asimon on 2006-09-26
Take a look at the logfile ~/.xsession-errors , maybe there are some error messages there which indicate what's wrong.

---

### Post by simpo666 on 2006-09-26
I tried waiting for about half an hour and nothing happened. I tried re-installing ubuntu but no lck, the first time everything worked ok but then when i restarted the same problem occured. Also I'm completely new to linux, so how do i check the error logs?

---

### Post by asimon on 2006-09-26
> **simpo666 said:**
> Also I'm completely new to linux, so how do i check the error logs?
If you are logged in under the command line, just enter
```

$ less ~/.xsession-errors

```.

---

### Post by simpo666 on 2006-09-26
thanks, i'll give it a shot

Edit: It appears the problem was my wireless card, i disabled it and Ubuntu loaded fine

---

### Post by fox_nl on 2006-09-27
Got my problem solved too. After logging into a command line terminal using ctrl-alt-f1 I tried to do an update using apt-get. It complained that something was wrong (don't remember what) and indicated that I should try the following command:

dpkg --configure -a

After doing this and restarting the X seerver by CTRL-Backspace Gnome started up normally...

---

