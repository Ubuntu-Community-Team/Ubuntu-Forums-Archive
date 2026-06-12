---
title: "bottom panel is gone"
date: 2006-09-20
forum: Desktop Environments
---

### Post by ShendZ on 2006-09-20
Hi guys,
Today I started my machine and notice that the bottom panel is gone.
I tried to make a new panel but it can't be sticked at the edge of the bottom screen.

It looks like the panel is there but not visible, but if I maximize a window, the window will cover up all the screen (but still under the top panel).

In simple words, I lose my bottom panel. How to check what is wrong with it?
Where should I to organize my panels.
This panel is pretty significant because it is where the running applications are displayed.

Thank you in advance.

-Shendy

---

### Post by Qrk on 2006-09-20
Hmm, that is interesting. When you right click on the area that was once your panel, do you get the contexual menu of the panel or the desktop?

Also, try the command "killall gnome-panel" to see if the problem persists.

Lastly, try logging into "failsafe gnome" from gdm.

---

### Post by ShendZ on 2006-09-20
Thank you very much,
With "killall gnome-panel" the panels are like shut down and they come back alive. The bottom panel also comes back.
Thank you very much.

Answering your question, I tried to right click on it when it was gone and it didn't give me contextual menu of the desktop.

Now everything is OK. Thank you once again.

-Shendy

---

### Post by bullit on 2006-09-24
Hi all, 

Another Linux newbie here.

I need some help in restoring missing panels in ubuntu 6.06 LTS.

FYI, I've tried killall gnome-panel but the terminal says I've no process to end. 

I'm running the default panels and to be honest, I don't know how it happened. I did something in terminal prior to logging out. When I log back in, the panels are missing. :confused:  

When I click on the place where the panels were once on, I get a contextual menu. Is there a command that I could run in terminal to restore the  working session prior the crash?

Any help is appreciated. Thanks in advance.

---

### Post by simon360 on 2006-09-24
Are both of your panels gone, bullit? Or just one of them? If it's only one of them, right click the one that works and click "New panel", and if both are gone, find a way to open up the terminal inside X (create a shortcut on the desktop that uses the command "gnome-terminal" without the quotes) and run gnome-panel. See if it spits out any errors, or thinks it's already running. Then, make sure you typed killall gnome-panel properly, typos are a really simple mistake to make.

---

### Post by bullit on 2006-09-25
Both panels. I went into terminal by ctrl alt F(something) and tried killing the panel process, out comes the reply when I did killall gnome-panel. I'm pretty sure I typed killall gnome-panel and after that I did gnome-panel --help or something to get some assistance. But to no avail.

I searched the forum and found an old thread for Hoary suggesting that I should pop in the Ubuntu live CD. 

I did that and installed KDE over gnome. After a successful installation, I found that I prefer gnome over KDE. 

The only issue now, I should remove about 80% of KDE software and that takes some time. *sigh* Wish there's a simpler way to call the terminal in such situation rather going into the black screen (which reminds me of windows 3.1 that I use in 92, what a nightmare). 

And as if reinstalling gnome over a slow net connection is not enough, my OSx86 had to die too.

---

### Post by komputes on 2007-12-13
I would like to pass this on, since I had a hard time finding it. This command + a reboot brings back the default panels. You will first need to get a terminal up. Since you don't have a menu bar/panel, that is quite tricky, but there is a keyboard shortcut for this:

Alt+F2 (This is equivalent to a run command)

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Close the terminal, reboot, et voila!

:popcorn:

---

