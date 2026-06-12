---
title: "Where did my window borders go?"
date: 2010-06-02
forum: Desktop Environments
---

### Post by olddog955 on 2010-06-02
I installed 10.04 and everything was good. I did an update, that was successful, when my computer restarted no window borders, no access to applications, time, trash, or any of those items which lie in borders. I'm running an old compaq desktop with a Intel 3. 

I read in sticky the following:[B]
Where did my window borders go?[/B] - cc7gir[INDENT]This is a  common mistake caused by disabling some plugins in CompizConfig Settings  Manager. To fix, open the manager (System > Preferences >  CompizConfig Settings Manager) and find the "Window Decorations" plugin.  Check the box and you're all set.
[/INDENT][LEFT]How do I get to system>preference>CompizConfig Settings Manager without access to items in border.

What's the chance the darn machine configured for multiple monitors, with "same information on each monitor", not selected. How do I get to Monitor preferences?

As you can see, I'm an amoebe-new.
[/LEFT]

---

### Post by Frogs Hair on 2010-06-03
Hi
1. go to top of screen and right click mouse and select new panel . if panel doesn't appear restart computer.
2. Once you have a panel right click the panel and select add to panel 
3. select main menu and click add.

This should give you apps, places, and system menus. 

4. system > administration > select hardware & drivers (Ubuntu will search for a driver )
5. Install recommended driver and restart.
6. From software center on apps menu install Compiz config. settings manager.

I deleted my panel after installation and this worked for me. By right clicking the panel from add to panel 
you may add anything from that menu.

---

### Post by varunendra on 2010-06-03
You may wish to follow a similar thread with alternate solutions:
[http://ubuntuforums.org/showthread.php?t=1500711](http://ubuntuforums.org/showthread.php?t=1500711)

---

### Post by olddog955 on 2010-06-03
I've tried both of the ideas. I lost my mouse right click. I tried a live session and I'm suspecting that the button on monitor preference for show same display in all monitors is unchecked. Is this possibly my problem. 

My question is there a way to toggle that option in a terminal window?

Or

any other ideas?

Live session seems OK, re-installing completely has the same problem. Should I try to install 9.04?? It worked well until my last update, inpreparation for 10.04 upgrade, and it had the same problem.

---

### Post by varunendra on 2010-06-04
Does Alt+F2 do nothing? If it opens the "run application" dialogue-box, then does running "metacity --replace" command do nothing?
Is Compiz Settings Manager installed on your system at all?
Is whatever you have posted in this thread all that you have tried so far?

The thread that I gave you link of is solved now. Revisit & see if you can find something new & helpful there. If these don't work, try booting into recovery mode as follows:

[LIST=1]
[*]Reboot computer
[*]While booting, press & hold 'Shift' key. This will bring up the Grub2 menu
[*]Select 'Recovery Mode'
[*]In the recovery menu, try 'dpkg' (repair broken packages)
[*]If 'dpkg' doesn't work, try other options as well.
[/LIST]
Lucid is relatively new & so are the relative problems. But searching & trying different solutions in this forum should help.

Post here whatever you've tried & whatever results you got. It'll help others understand your problem properly & suggest a more accurate solution.

---

### Post by varunendra on 2010-06-04
> **olddog955 said:**
> Live session seems OK, **re-installing completely has the same problem**. Should I try to install 9.04??

Did you perform a clean install? That is- did you entirely format the partition & made a fresh install of Ubuntu 10.04?

For trying 9.04 part, I don't think you need to return that far! You said 10.04 worked fine until you updated it. So if it's the updates that screw up your system, why update at all? Install it without updating & install individual packages you need.

By the way, as you can notice I'm still using 9.10 & am quite happy with it.

---

### Post by olddog955 on 2010-06-05
Yes, my first clean install of lucid worked fine until I updated it, then "no borders".

I tried alt/F2 and got a "run" window, and then a terminal. But stalled there. I'm really a "user" rather than a "hacker". It's been many years since using linux. I tried 9.04/9.1 and really liked it, but, hey 10.04 has to be even better, right?

This last time, I did another "clean", format all, type install, and still no borders. I even got an "over heating" warning. Stopped, let the system cool and tried again. I live at over 7000 ft, and cooling fans are required and most are just barely adequate.

I'll do another clean install, and try the items you suggested again.

Thanks for the help! I appreciate it.

---

### Post by varunendra on 2010-06-05
> **olddog955 said:**
> I tried 9.04/9.1 and really liked it, but, hey 10.04 has to be even better, right?
Actually, Ubuntu (or any Open Source OS- for that matter) doesn't work that way!

As far as I've learned so far, some changes & modifications (sometimes including too daring or too ambitious ones) are introduced, some basic testing is done, then launched for public use & expected to work as expected.

Then comes the stage where people/developers use/test the OS on a vast variety of hardware & environment which would be impossible to achieve under lab conditions (this is where the strength of 'Open Source' concept comes in). **Obviously, in the initial days they face a large number of bugs unless the introduced changes are too little or too safely designed.**

Then starts the cycle of sorting out bugs> debugging > launching bug-fixes/modified packages some of which again lead to new bugs (which is most likely to be your case) > retesting (both in labs & at public ends).......... & so on.

Finally it reaches a relatively stable & optimized state that can make everyone happy.

Since this process of testing>debugging>developing involves, to a great extent, general public & independent developers- **this is why it is called 'Open Source'**.
Initially, this (putting immature product under public use) causes almost every new release look confused & imbalanced at some points. But in the long run, it proves to be its greatest strength being open source.

So bottom line is- if you're not too enthusiastic & wanna play safe, use a new release only when it becomes mature enough. Otherwise stick to the stable one.

---

### Post by olddog955 on 2010-06-05
Yes, my first clean install of lucid worked fine until I updated it, then "no borders".

I tried alt/F2 and got a "run" window, and then a terminal. But stalled there. I'm really a "user" rather than a "hacker". It's been many years since using linux. I tried 9.04/9.1 and really liked it, but, hey 10.04 has to be even better, right?

This last time, I did another "clean", format all, type install, and still no borders. I even got an "over heating" warning. Stopped, let the system cool and tried again. I live at over 7000 ft, and cooling fans are required and most are just barely adequate.

I'll do another clean install, and try the items you suggested again.

Thanks for the help! I appreciate it.

---

