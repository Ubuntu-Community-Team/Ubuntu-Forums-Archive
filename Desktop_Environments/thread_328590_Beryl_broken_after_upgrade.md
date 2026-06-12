---
title: "Beryl broken after upgrade"
date: 2006-12-31
forum: Desktop Environments
---

### Post by rbrugman on 2006-12-31
I had the previous version of beryl running wonderfly on my Thinkpad R51 with Intel i855 GM graphics chipset, but after upgrading to the latest version, it doesn't work.  My beryl session no longer loads beryl and if I force it to start with the terminal, it works but without any window borders.  The themes manager does nothing and its pretty useless.  Is there any way to fix the install or to downgrade?  I tried reinstalling everything but nothing works.

Thanks,
Robert

---

### Post by iamhugeinjapan on 2006-12-31
A few questions:
Latest version being 0.1.4? 
What command are you using to start Beryl?
What version of Ubuntu are you running?
Is your desktop environment GNOME, KDE or other?
Are you using AiGLX or XGL to run Beryl on?

thanks

---

### Post by Satanister on 2006-12-31
Had the same problem after upgrade Beryl was broken, no window borders and none of the plugins worked.

What I did was I started it from terminal just typed "beryl" without the quotes.
I got a message that the plugins were not the same version as beryl.
So what I did then was to go to synaptic package manager pressed "reload" after that "mark all upgrades" it showed a list of beryl packages that was going to be upgraded.
Then I pressed "apply". After synaptic finished I loaded Beryl and all was well.
Tell me how it turns out....

PS make sure that you have the correct repositories in your source list.

---

### Post by rbrugman on 2006-12-31
Right now I'm running Beryl 0.1.4 on Kubuntu 6.10 with KDE.  I use AiGLX since XGL doesn't render very quick on my laptop.  The command for starting Beryl I found on the Beryl wiki is this script:

#!/bin/sh
 export KDEWM="/usr/bin/beryl-manager"
 exec startkde

When I do that though and change the permissions and make it executable nothing happens.  It worked fine before but it doesn't do anything anymore.  So I tried changing beryl-manager to just beryl.  This time beryl loads and the effects such as the rotating cube work, but my windows don't have any borders and I can't type anything into the terminal.  

The guide I followed is here:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)


Hope that provides some info so I can get this problem fixed!

Thanks,
Robert

---

### Post by Jack_The_Ripper on 2007-01-01
I upgraded beryl to 0.1.4 but it was crashing after second logging in ](*,) 

JTR

---

### Post by rbrugman on 2007-01-01
Last night after some tinkering I actually found a solution to my problem. I noticed Beryl was loading but crashing for some reason, so I used Beryl-manager to disable the feature to load an alternative window manager on crash.  I turned that off and forced it to use beryl all the time.  It works!  Probably an imperfect solution, but if it works I don't really care too much.

Robert

---

