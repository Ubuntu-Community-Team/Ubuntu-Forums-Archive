---
title: "Intrepid freezing"
date: 2009-01-06
forum: General Help
---

### Post by Jameshardy88 on 2009-01-06
Hi ive got a problem with my ubuntu installation about once a day for seemingly no reason my computer will freeze. All key combinations cntrl-alt-backspace etc do nothing and caps and num lock also fail to work. Has anyone got any ideas what could be causing this?

---

### Post by SteveDee on 2009-01-06
Does this happen when you are actually using the machine, when the machine is idle or after the screensaver has kicked in?

You could run System Monitor so it shows mini graphs in a panel of (say) cpu%, memory & network activity. That way you can see:-
 - if the cpu is 100% occupied with some task
 - if all your memory has been consumed by something
 - when it crashes whether the system is still running but just not accepting input

---

### Post by blazemore on 2009-01-06
Have you tried searching the problem on the forums?
I swear I helped someone with an identical problem 2 days ago!

---

### Post by Jameshardy88 on 2009-01-06
i have a system monitor in my top panel during freezes it is normally low and typical of what i am currently doing it doesn't suddenly spike up or anything. and upon freezing the monitor also freezes

---

### Post by Jameshardy88 on 2009-01-06
> **blazemore said:**
> Have you tried searching the problem on the forums?
I swear I helped someone with an identical problem 2 days ago!

I think you were probably helping me lol. I started a new thread to see if i could get any other suggestions as unfortunately i can't spare a day to have internet free atm as i need it for revision purposes. I have been looking for an answer on the forums however people with similar problems seem to be few and far between, also as i ave no real clue as to what is causing the problem it is hard to identify if they are actually having the same problems as me

---

### Post by Jameshardy88 on 2009-01-06
would re-installing ubuntu be a good idea or is it likely that after doing so that i will still have the same problems?

---

### Post by SteveDee on 2009-01-06
I guess at this stage we don't know if its hardware or software.

If you have a Ubuntu CD you could run from that for a while. If it still freezes it could be hardware or some compatibility problem.

I don't suppose your cpu is getting too hot? (you could monitor with X Sensors).

---

### Post by SteveDee on 2009-01-06
Here's another idea. Linux creates log files for all sorts of events and saves them in /var/log directory. These can be viewed using the Gnome System Log Viewer (System > Administration > System Log).

Look for events that occurred at the times you noted the system crash, it may offer some further clues.

---

