---
title: "Dofus &amp; Adobe Air - Sound Not Working"
date: 2013-09-25
forum: Gaming &amp; Leisure
---

### Post by brandondtaylor on 2013-09-25
I have scoured the internet for solutions to my problem but unfortunately they are either unrelated to my specific problem or they are left unanswered.

I am running Ubuntu 12.04 and I just recently installed Dofus from the Ubuntu Software Center. The game itself runs flawlessly (as I have come to expect from Ubuntu) but strangely the sound does not work at all. I am pretty sure the problem has to be with Adobe Air but I'm unable to remedy the issue from there. If anyone has any ideas or solutions to my problem please help me. :(

---

### Post by kostkon on 2013-09-25
If you check again in the usc, it says:
[LIST]
[*]If you installed Wakfu before August 20, please updates your packages before installing Dofus.
[*]You may have to add yourself to the "audio" group in order for Dofus to play sounds. To do so, please run 'sudo usermod -a -G audio {username}' in a terminal. 
[/LIST]

---

### Post by brandondtaylor on 2013-09-25
I don't understand what any of that means. I didn't install Wakfu before August 20, nor would I know how to update packages or whatever that would be.

I also don't know what adding myself to the audio group means, either. I opened the terminal and ran the command but nothing happens. When it says username it means the username of my computer right?

---

### Post by kostkon on 2013-09-25
> **brandondtaylor said:**
> I don't understand what any of that means. I didn't install Wakfu before August 20, nor would I know how to update packages or whatever that would be.

I also don't know what adding myself to the audio group means, either. I opened the terminal and ran the command but nothing happens. When it says username it means the username of my computer right?
Yes, your username in Ubuntu, e.g.
```
sudo usermod -a -G audio myusername
```

---

### Post by brandondtaylor on 2013-09-25
Well, I restarted my computer and typed it in again, this time it asked for my password. I typed it in, nothing happened. I reopened Dofus to see if it worked, still no sound. :( I can hear some sound effects i.e. birds chirping, but it isn't regular like it should be.

---

### Post by kostkon on 2013-09-25
Do you have an option in the game to run the updater or have you searched in the dash for an app called dofus-updater or something similar?

---

### Post by brandondtaylor on 2013-09-25
When I run the Dofus application, it plays through the updater and opens a separate window for the game. Other than that there's no other update application I can run. So as you can see I am very stumped.

---

### Post by brandondtaylor on 2013-09-27
Small update: I purged Dofus, Wakfu, and Adobe Air from my machine and reinstalled brand new. Still no sound. I've contacted Ankama about my problem and hopefully I'll hear back from them soon. If I do find a solution I will share it here. Fingers crossed!

---

