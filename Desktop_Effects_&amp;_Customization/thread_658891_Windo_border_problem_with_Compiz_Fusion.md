---
title: "Windo border problem with Compiz Fusion"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by Vind on 2008-01-05
Hello. I'm having a problem with my window borders while using Compiz Fusion. I've checked other posts but none seem to solve my problem.

I'm using Ubuntu 7.10 with Compiz Fusion 0.6.0 and Emerald installed. My graphics card is an Nvidia 7600 with the latest nvidia drivers installed. I installed Compiz and Emerald using the following guide:

[http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)

Once everything was installed after following this guide everything worked to perfection, including window borders (this i got to work adding 'emerald' to the comand line in the window border option of compiz settings).

My problem started about 2 days after that. Another frequent user of this PC did System->Preferences->Appearance and modified visual effects to maximum. I'm not quite sure if this created a conflict with compiz, but the following time the PC was booted all the compiz effects were disabled including window borders. I activated them all again and then did Ctrl+Alt+Delete and everything was working again except for the window decorations which had disabled itself once again. I tried activating it several times with the same outcome although in the end (not really sure how) I managed to keep the option enabled at all times and the window borders appear but the behaviour is the same as if the window borders were not there (can't move, minimize, etc)

Additional info: if I access CCSM through the terminal (command 'ccsm'), all options under Window Management are disabled. If I enter CCSM using 'sudo ccsm' all the options under this heading appear activated, doesn't mean much to me but it might mean something to anyone reading this.

I have already tried using 'compiz --replace gconf' and 'emerald --replace' (although these comands leave the terminal prompt flashing after executing them without seeming to give me an error or actually finishing running the command)

Thanks for help in advance

Vind

---

### Post by warbread on 2008-01-05
Was this other user using their own account, or are you two sharing one?  Do they have admin privleges?

---

### Post by Vind on 2008-01-05
No, we both use the same account. He did not use any password while using the PC although he did use the PC after i had made some modifications with the sudo command (not quite sure if the system remebers you have privileges once sudo is declared and the password is entered). Anyway the other user is certain he did not enter any password himself ( he doesn't know it ). So i think he did not have privileges (bare with me quite new to all this :) )

Thanks

Vind

---

### Post by warbread on 2008-01-05
Interesting.  And what happens when you re-enable the settings under 'Windows Management'?

---

### Post by Vind on 2008-01-05
OK, this is most confusing. 

I have tried enabling the options again under 'Windows Management' (this must be around the 10th time I've done this) and now some options have remained activated while some have disabled themselves after doing Ctrl+Alt+Delete. A bit like 'Windows Decoration' in the first post.

Well I'm happy to say that my window borders are functioning again (I think its because the move option under window management has remained enabled this time). I now must try getting resize and other options to work again.

For the life of me, I don't know why or how I am solving this other than, change settings and CTRL+Alt+Delete loads of times :d

---

### Post by warbread on 2008-01-05
At this point, not knowing much better myself, I would reinstall compiz, compiz-settings and emerald.

---

### Post by Vind on 2008-01-06
Hi again. Well I'm glad to say that i have finally been able to get things working normally.

What was bugging me was the command the guide uses to start Compiz under Preferences->Sessions->Startup Programs. The guide says to use >  compiz --replace gconf It turns out (seen at another post)  that it isn't a good idea to use CCSM in combination with gconf as it can lead to erratic behavior, which is what was happening to me.

I replaced the command with this one > compiz --replace ccp and everything was back to normal.

Nice to be back on the road again :D

---

