---
title: "Fluxbox right-click problem"
date: 2007-11-03
forum: Desktop Environments
---

### Post by purplenite on 2007-11-03
I installed fluxbox with the Ubuntu package, and when I log in, I can't right click on the desktop to bring up a menu, which pretty much makes fluxbox useless. Any idea what might be wrong?

Edit: Thought I should add that I am using a laptop, so I'm talking about right-clicking with a touchpad button.

---

### Post by jviscosi on 2007-11-03
I think you can run the **fluxbox-generate_menu** command to create Fluxbox menus.  (Obviously you'll have to do it from another environment, if you can't get a terminal to come up in Fluxbox.)

---

### Post by jviscosi on 2007-11-04
RedSquirrel has a great big Fluxbox tutorial [here]("http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox").  It'd probably be helpful as it seems it's been updated to talk about Fluxbox issues in Gutsy.  (I run an SVN version of Fluxbox rather than the Ubuntu package so my experience differs.)

---

### Post by gatewayasteroid on 2007-11-05
> **purplenite said:**
> I installed fluxbox with the Ubuntu package, and when I log in, I can't right click on the desktop to bring up a menu, which pretty much makes fluxbox useless. Any idea what might be wrong?

Edit: Thought I should add that I am using a laptop, so I'm talking about right-clicking with a touchpad button.

[https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/146414](https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/146414)

---

### Post by usererror on 2007-11-05
If you run the 'update-menu' and them move the menu to 'menu' as the filename then it seems to work...at least for me...and i've had to do it twice because i'm experimenting on a new box. :D

---

### Post by viiv on 2008-03-30
Hey
I'm pretty new to all this. I'm having the same problem. I looked at the tutorial link but I couldn't make much sense of it. I could imagine how to edit files, but where do I find the necessary files to edit? Does anyone have beginner-level advice on how to solve this problem?

---

### Post by tad1073 on 2008-03-30
> **viiv said:**
> Hey
I'm pretty new to all this. I'm having the same problem. I looked at the tutorial link but I couldn't make much sense of it. I could imagine how to edit files, but where do I find the necessary files to edit? Does anyone have beginner-level advice on how to solve this problem?

~/.fluxbox/menu or ~/.fluxbox/usermenu

---

### Post by viiv on 2008-03-30
tad1073
Thanks for your ultra-fast response.
I know a *little bit* about basic linux commands, but that's about it. I have to admit that I don't understand your reference to "~/.fluxbox/menu or ~/.fluxbox/usermenu". Is this a file, a folder etc? And how do I get to it? are the "~" and "." shorthand for something?

---

### Post by tad1073 on 2008-03-30
> **viiv said:**
> tad1073
Thanks for your ultra-fast response.
I know a *little bit* about basic linux commands, but that's about it. I have to admit that I don't understand your reference to "~/.fluxbox/menu or ~/.fluxbox/usermenu". Is this a file, a folder etc? And how do I get to it? are the "~" and "." shorthand for something?
~=/home/yourusername and .=hidden file

---

### Post by RedSquirrel on 2008-03-31
> **viiv said:**
> Hey
I'm pretty new to all this. I'm having the same problem. I looked at the tutorial link but I couldn't make much sense of it. I could imagine how to edit files, but where do I find the necessary files to edit? Does anyone have beginner-level advice on how to solve this problem?

You have to generate the menu.

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

Read the sections in that tutorial:

[B]I installed Fluxbox from the repositories, but there is no menu when I right-click on the desktop. How do I fix this??

The Fluxbox Menu on Gutsy Gibbon is missing some items. How can I fix this?

[/B]

---

### Post by viiv on 2008-04-02
It worked. Thanks everyone.

---

