---
title: "Gnome applets quit unexpectedly"
date: 2005-09-26
forum: Desktop Environments
---

### Post by gorkhal on 2005-09-26
Hey all...very frustrating problem here, similar ones have been reported before, however none of those solutions worked for me.

Whenever I log in these days...two dialogs pop up..

a) 'Window List' has quit unexpectedly
b) 'Workspace Switcher' has quit unexpectedly

and I have to reload them again. This happens only at log in and is driving me absolutely nuts....anyone got a clue??

---

### Post by RikoW on 2005-09-27
I had the same problem not too long ago.

see this thread: [http://www.ubuntuforums.org/showthread.php?t=68424]("http://www.ubuntuforums.org/showthread.php?t=68424")

By accident, I removed the panel, which contained those applets. After creating a new panel and adding the applets again, everything works as before.

I also tried in between to uninstall and install the gnome applets, but that didn't help. So I suspect, the problem is  somewhere in the (user) local config files.

Good luck ;-) 

                 Riko

---

### Post by gorkhal on 2005-09-27
thanks rikow...flushed the panels...re-init...hasnt pooped on me yet.

thanks again.

---

### Post by gorkhal on 2005-09-28
ok new problem...the applets dont crash anymore...however the workspace switcher doesnt show the application icons anymore like it used to, say you have Opera maximized on one desktop, on the workspace switcher, it will show the 'O' icon.

gnome's behaving really bad, it hurts our feelings it does...yessss

---

### Post by RikoW on 2005-09-29
hmm, that problem I don't have! Icons are in plain view right now on the workspace switcher.

Do you know, if you had this problem right away after recreating the panel with the applets or did it appear 'some time' later?

In the first case: the difference between our approaches might be that I had re-installed the applets before (which as I wrote already did not fix the crashing applet problem) and only afterwards 'fixed' it by removing and re-creating the panel.

So maybe, you want to remove and install the gnome-applets .... your guess is as good as mine .... almost window'ish behavior, huh? :)

Good luck ... again :)

             Riko

---

### Post by gorkhal on 2005-10-01
found the solution.....

the workspace switcher will not show any preview icons when the panel size is less than 24 pixel...i had it on 23 :D 

go figure.

---

