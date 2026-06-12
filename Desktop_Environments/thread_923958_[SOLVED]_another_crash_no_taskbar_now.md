---
title: "[SOLVED] another crash: no taskbar now"
date: 2008-09-18
forum: Desktop Environments
---

### Post by AlanInVancouverBC on 2008-09-18
I guess this is the way I will learn about tweaking Ubuntu. This is the third time in three months I've crashed it. But it's a rather silly, simple problem.

In my Newbie mode, I was searching files and programs and came across Konqueror. Opening it, I found it's another browser--one I hadn't heard of. Being a Firefox fan, I chose to delete Konqueror (and, of course, its dependencies). Well, I found out that one of its dependencies is the taskbar! 
(Gee doesn't this sound like the IE issue with Windows, where you can't delete it without crashing the OS....)
So I can't access Administration, Files, Preferences, etc. I can't get to Synaptic or Add/Remove to repair. I can't use ALT+F2. I can't get to Root in Terminal. 
What I can do, luckily, is get online. I have a folder with games in it, with a toolbar that allows accessing the internet, and "getting help online". So I can go to Bookmarks and go to this fourm for help. And I need help!

---

### Post by Joe_archer on 2008-09-19
I suggest that you use a virtual terminal by pressing ctrl-alt-f1 and log in as yourself, then sudo apt-get install konqueror.

ctrl-alt-f7 will get you back to your x session.

I'd strongly advise against removing things that are installed by default, without checking the consequences first.

---

### Post by AlanInVancouverBC on 2008-09-19
Thank you, Joe, for responding. I can't get to root when I hit C/A/F1. I get to...I forget. So how do I get to root?

p.s. It was always this way with me (and I'm sure many/most others: tinker, experiment, deal with the consequences. Since 80-90% of what I do with a computer is online, getting it back up be reinstalling the system, and tweaking settings, takes me about 2 hours. I.E. no big deal if I HAVE to reinstall everything.

But I would still like to try your idea. I just can't get to Root.
I'm still too new to Ubuntu (but 22 years with PCs)

---

### Post by AlanInVancouverBC on 2008-09-21
I fixed it! I found that by right-clicking on the folder that I have, the games folder, I get a menu option to "open with" another program. One of the programs allowed me to access the shortcuts that are on the taskbar, including Synaptic Manager. In Synaptic, I searched for programs or dependencies that contain the word "taskbar". I found what I was missing, installed it and rebooted. It worked!
So after crashing the system 3 times and reinstalling the system 2 times, I'm at a point that, at least this time, I can logically figure out how to rescue myself. That's a rush.

---

### Post by Lizard_King on 2008-10-06
Ubuntu sucks. I finally decided to give it another chance and now when I turn on my pc all I get is a desktop image with no task bar or any controls. I can move my curser around but nothing else.

I know none of you "experts" will answer this, but maybe a noob knows what the problem is.

---

### Post by Lizard_King on 2008-10-10
Anyone who continues to use this crappy OS and this unhelpful forum should seek professional help.

---

### Post by directcharitycontribution on 2008-10-27
u got to ctral-alt-bspace > sessions > x-failsafe

---

