---
title: "and Xfce, etc... HELP! strange behaviour GUI ok at 50% only ??? !!! :-("
date: 2013-03-14
forum: Desktop Environments
---

### Post by hmag on 2013-03-14
Hello,

A couple of months ago, I installed a Ubuntu 12.04LTS on my 321bit desktop with ATI graphics card.
I had to struggle a time with the "PC frozen" issue, not finding any solution, then moving to Xubuntu on advise I got from this forum (my desktop is 5 years old).
Xubunbtu worked fine until today, but surprisingly starting today, below are the main (blocking) issues I am facing, (Xubuntu and Xfce show same issues) :
- no "X" any more to close windows - need to use the menu
- text edit fields in some dialog boxes (e.g. password dialog to login in Pidgin) are frozen (no text cursor when moving inside - not possible to inpout any text in there)
- Firefox can be launched, but once open, its main menu is inactive, thus it is impossible to close it except by kill in a term ;  also menus to logout/restart/stop are inaccessible
- etc...

Surprisingly, when I login using the full Gnome, all this is still working fine.
Nevertheless I want to find a solution to this Xubuntu issue, because it has ben working fine during these last 3 months and I dont want to use Gnome because freezing on my "old" desktop with ATI graphics.

Any idea ? Did you see this already ? Could it be related to any update ? Anything else ?

Early thanks
hmag

---

### Post by Frogs Hair on 2013-03-14
Open the terminal and restart the window manager. I am logged into xfce and today's updates have had no ill effects
```
xfwm4 --replace
```

---

### Post by Rodney9 on 2013-03-14
I too have been having this problem with Xubuntu 12.10
I can not open a terminal and alt f2 also does work.
I can't type anywhere.

I  ended up using Lubuntu from a live dvd and found many others having similar with bug reports made.
Using the live cd I mounted my hard drive and deleted the sessions folder in .cache
this fixed the problem, if it keeps happening, I may well end up using Lubuntu.

Rodney

---

### Post by hmag on 2013-03-16
Hi Rodney,

Thanks for the information about this issue not being so rare, and for the workaround. Fortunately in my case I yet can open terminals and enter commands (for how long time ;-) thus removing this sessions cache should be possible.

I am new to Ubuntu, Xubuntu, etc... but not new to Linux, I started my first install on a slackware on a Intel 486 20 years ago, went through Mandrake, Suze, then stayed a couple of years on Gentoo. Gentoo is the most flexible and really robust as far as you are ok to spend hours at compilation and configuration for every single piece of hardware which is connected to your motherboard... Also when you are unlucky with Gentoo, a simple update may require DAYS (not hours) of recompile interleaved with fights with dependencies and redesigned configuration files... a distrib for geeks only, not for users.

So I finally ended on Ubuntu recently, seduced by the comprehensive and effective installation process. By the way, giving up tons of potential open source software offered in Gentoo, for a system offering a somewhat more limited number of applications, that I supposed to be more reliable for everyday use and keep up to date... I see that finally, there is no magic in the Linux world, and Ubuntu too has its flaws, apparently not minor ones...!

At this time I yet don't which flavour of ?Ubuntu will provide the level of reliability, stability and simplicity I am looking for. On my recent laptop (i am using it to write this text), the 12.04 LTS with Gnome seems to be doing OK. On my desktop, the same does definitively not ("PC freezing" issue), and XUbuntu pushed me to this "sick GUI" issue... and this seems not to be a matter of mismatch betxween hardware and software, because Xubuntu worked well for many months on my desktop. So a software-only issue, mismanaged cache, memory leaks, overwritten files, ... wow

I simply hope that some people are taking these bugs into consideration with the appropriate level of care... Else, the future of these distribs may not be so shiny. About the "PC frozen" issue I have simply seen no real interest and action from the Ubuntu world, ... seems strange ... But for sure every "Linux distrib"'s world is not the same as the planet of the next distrib... ;-)

Regards
HMag

---

### Post by Rodney9 on 2013-03-17
I found this -

 [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu)

Some very good tips, especially the swap one.

I also found that when XFCE locks up again all I have to do is use ctrl/alt/f2 make sure mc is installed, if not use - sudo apt-get install , then use sudo mc root and I can delete the sessions folder in .cache.

then I sudo reboot

I believe the problem will fixed in 13.04, it's something to do with a bad shut down I believe.

Rodney

---

### Post by Peripheral Visionary on 2013-03-17
It's not an issue in 12.04 at all, even with all the updates.  And it sounds like something that might be fixed by an update soon, too.

---

### Post by hmag on 2013-03-18
From my opinion, it definitively seems to have to do with 12.04 because this is what I installed on my PC 2 months ago and I get the issue!

About fix in a next update, are you sure that a bug has been logged for this ? If yes would someone  be kind enough to provide the bug ID ? I will have a look to make sure, and if not really matching my issue, I will consider logging a bug.

I agree that it should have something to do with the shutdown. Because since a long time at every new start of my PC (next to a regular, software-driven shutdown), Firefox used to claim being lost like next to a sudden interruption (e.g. power outage, press on reset, turn computer off using switch, ...): asking what to do with pages which were open before power off.
Also, in the case of this issue, Firefox is the most problematic app, even after ```
xfwm4 --replace
```, it will freeze after a couple of pages were browsed.
Also ```
xfwm4 --replace
``` did not complete correctly and blocked the Term where I issued the command.

NOTE: I removed the content of session under the ".cache" directory for users root and myself, after xfwm4 --replace. This restored "normal" look&feel&functions for just a couple of minutes, in particular until I opened and used Firefox. Then I had to reboot using the reset button because unable to access any command or menu...

Regards
HMAg

---

