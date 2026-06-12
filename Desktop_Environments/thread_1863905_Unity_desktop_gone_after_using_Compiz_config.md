---
title: "Unity desktop gone after using Compiz config"
date: 2011-10-18
forum: Desktop Environments
---

### Post by jockmullin on 2011-10-18
Greetings.

Just updated to 11.10 from 10.04 and was going quite well until I decided to look at Compiz conifg manager.

Big mistake.

Now all my workspaces have only destop background, no launcher and top line is only File Edit ... Help and nothing else. No time, or other top line icons. Cannot get to system, cannot shut down and none of the keyboard shortcuts work - alt F2 nothing. Super key plus letter opens a little box lower right but typing there and hitting enter does nothing.

This seemed to start when I hit the > to the right of Advanced Search on the Compiz manager, thinking it was just going to do something benign like give advanced search options.

I would like to remove CCSM, but can't even open a terminal window.

Have I fracked my system? 

Any advice how to revert to pre-CCSM status would be appreciated.

Jock

---

### Post by Copper Bezel on 2011-10-18
The arrow should, quite benignly, create a search index and then allow you to search for words and phrases within plugins. Most likely, something else got ticked or unticked in the process.

Removing compizconfig-settings-manager won't do you any good. It wouldn't remove the altered Compiz setting. Instead, you'll need to reset the Compiz settings using gconftool - assuming this still works in the same way it did under 11.04 and Gnome 2.

Since you can't get to a terminal, you'll need to jump over to a tty, with Ctrl+Alt+F1, F2, or whatever. (Ctrl+Alt+F7 or F8 or so will bring you back to the display.)

First, nuke Compiz's configuration settings:

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
```

Then reset unity:

```
export "DISPLAY=:0"
unity --reset
```

---

### Post by jockmullin on 2011-10-18
Excellent!

That did the trick. Ctrl-Alt F2 got me to TTY as you suggested and everything else worked.

System back to normal. Thanks very much. 

With that procedure at hand I MAY look at CCSM again, after reading the docs and imaging the drive like I should have done in the first place.

Jock

---

### Post by Copper Bezel on 2011-10-18
Very cool! Just be sure to mark the thread as Solved, in Thread Tools at the upper right. = D

---

### Post by Drezliok on 2011-10-18
I did the same thing and it was so late I decided to sleep on it and ask in the morning. Thankyou for beating me to it.

---

### Post by jockmullin on 2011-10-18
Thanks, I was trying to figure out how to do that. Done.

Now if I could only update my profile, but it won't let me because I haven't done enough postings. So it says I am still running Hardy, but t8ntso. That's what I get for lurking and using search.

Glad Drezliok posted also - I still feel like a dork but at least now I have company :)

---

### Post by Copper Bezel on 2011-10-18
Yeah, this has been a recurring problem since Natty. The commands above are from [_Tux Garage's guide_]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") to what to do when Unity disappears. = )

The profile thing is weird, I know. There are other reasons for it, but it's inconvenient if you've already created an account with (now wrong) system information and are looking for a support answer. In any case, thank you for indicating your version in the post itself - that saves a lot of time, since people forget to update their information even when they can. = )

---

### Post by zurga on 2011-10-20
Thank you very much for the solution which I too used to fix the same problem. However, the problem, at least in my case, is not to do with clicking over '>'. What I did was to click over 'Preferences', which I think is only a part of the switch label 'Preferences   >'. Just the one click resulted in the whole desktop seizing up, with no other response. Now, I am afraid to use the tool at all, as it seems extremely fragile.

---

### Post by neuvlo on 2011-10-20
Thank you good Sir!
:)

---

### Post by BHEJU on 2011-10-20
This is what I was looking for. I will try this out soon as I can.

A BIG THANKS.

---

### Post by zurga on 2011-10-20
> **zurga said:**
> Thank you very much for the solution which I too used to fix the same problem. However, the problem, at least in my case, is not to do with clicking over '>'. What I did was to click over 'Preferences', which I think is only a part of the switch label 'Preferences   >'. Just the one click resulted in the whole desktop seizing up, with no other response. Now, I am afraid to use the tool at all, as it seems extremely fragile.
Having fixed the system with  Copper Bezel's solution, I thought I try to test clicking on 'Preferences >' one more time, and as before the system seized up immediately. Used  Copper Bezel's solution again, and proceeded to use CompizConfig tool to reduce the size of the icons in the launcher. This worked very well. So the main problem seems to be 'Preferences >', and 'Advanced Search >'.

---

### Post by wildwildebeest on 2011-10-22
Thanks I had the exact same problem and this solution has restored my launcher and panel icons!

Now looking forward to a permanent fix for CompizConfig.

---

### Post by somnob on 2011-11-01
verry nice,
thanks, it workt great.

you can get a terminal on the desktop by pressing ctrl+ alt + t

---

### Post by Wolfram Wrenches on 2011-11-23
I got to this thread from a Google search having had the problem of missing Unity desktop  after the most recent update today (11/23/2011). I read the solution but before trying it I looked again in Compiz Configuration Settings Manager. I found a setting called Ubuntu Unity Plugin (located in the Desktop section) that was unchecked. I turned it on and immediately got the Unity desktop back with no restart or logout needed! Hope this helps people continue to use Compiz with Unity.

---

### Post by PayPaul on 2011-11-24
I had or maybe still have the same problem as the above posters. I did uninstall compiz before I got to this thread. The disaster continued when I logged back in to Ubuntu. Will the solution posted still work for me? I've been able to restore Unity but the apt get command to reinstall Unity that I started in Terminal is still running as of this moment with lots of "failed" entries. Am I going to be able to log out and log back in with Unity restored?

Update: Terminal is still at it, finding errors and failures by the score. I had to choke when I saw this one though:

```
(npviewer.bin:3446): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

```

Have Santa's merry elves gone bad on me?

---

