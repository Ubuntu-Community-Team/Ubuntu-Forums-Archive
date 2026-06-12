---
title: "unity-scope-calculator in 13.04"
date: 2013-05-10
forum: Desktop Environments
---

### Post by VaclavC on 2013-05-10
After upgrade to 13.04 unity-scope-calculator does not work anymore. How can I put it into operation?

---

### Post by kcpr on 2013-05-10
Would really like to know also. It was probably my the most useful non-default Scope.
At now it can be installed from Oneric repositries, but does not really work as I think.

Any help would be appreciated, thanks. :)

---

### Post by javajavachris on 2013-06-14
You can try installing smart scopes (from 13.10). Here's how:

First, you want to add the repository.
Open a terminal window (Ctrl+Alt+T). Copy/Paste, or type:

[B]*     sudo add-apt-repository ppa:ubuntu-unity/experimental-certified*
[/B]
Then update...

[B][I]     sudo apt-get update
[/I][/B]
Last, upgrade the scopes already installed, and install a bunch of new ones.

[B]*     sudo apt-get dist-upgrade*
[/B]
NOTE::"for the last command above, make sure no packages are removed except for the unity-lens-shopping. If the command tries to remove more packages, it means something is broken on your system and you need to fix it so do not proceed with the installation!"

So the system doesn't overwrite the newly installed scopes if 13.04 gets new scopes, type:

[B]*     sudo apt-get install ubuntu-unity-experimental-certified*
[/B]
then

[I]**     sudo apt-get upgrade**
[/I]
... and you're done.

When you search in Dash, you'll have a bunch of new scopes, calculator being one of them. You may have to click "filter results" on the right and activate calculator, as I did.

I know this may be a little too spelled out for some, but I remember coming to these forums the day I first installed Ubuntu, looking for first-day help on a number of topics, so, you you never know how new the person reading this may be :)

cite<[http://www.webupd8.org/2013/04/how-to-install-unity-smart-scopes-in.html](http://www.webupd8.org/2013/04/how-to-install-unity-smart-scopes-in.html)>

---

### Post by VaclavC on 2013-06-20
Already done it. I have package unity-scope-calculator installed but calculator does not work for me. And dash is noticeably slower and does not search in applications from time to time.

---

### Post by mc4man on 2013-06-20
assuming people are using the raring scopes ppa  - 
[https://launchpad.net/~scopes-packagers/+archive/ppa](https://launchpad.net/~scopes-packagers/+archive/ppa)
**And these raring packages** (not the '100 scopes' deal

unity-lens-utilities (0.1-0~10~raring1)
unity-scope-calculator (0.1-0~12~raring1)


When they built the raring package several weeks ago I guess no one bothered to check if gcalctool still  (or ever) installed a symlink in /usr/bin linking to the new calculator or adjusted the scope to use new name
This is why it doesn't work. 
Easy user fix, in terminal - 
```
sudo ln -s /usr/bin/gnome-calculator /usr/bin/gcalctool
```

screen from raring

Edit: turns out it is just 2 lines in /usr/lib/unity-scope-calculator/unity-scope-calculator that need to have gcalctool changed to gnome-calculator
lines 93 & 98
If those are edited then a symlink is not needed - screen 2

---

### Post by VaclavC on 2013-06-21
Still it does not work.

After adding ppa from first post in ithis thread, I had unity-lens-utilities 0.1-0~10~raring1 and unity-scope-calculator 0.1daily13.05.07ubuntu.unity.experimental.certified-0ubuntu1. I added suggested link to gnome-calculator and it did not work. Then I forced unity-scope-calculator package to version 0.1-0~12~raring1 (the second one available with my current apt sources configuration) and it does not work as well. I tried to logout/login after each change.

---

### Post by mc4man on 2013-06-21
> **VaclavC said:**
> Still it does not work.

After adding ppa from first post in ithis thread, I had unity-lens-utilities 0.1-0~10~raring1 and unity-scope-calculator 0.1daily13.05.07ubuntu.unity.experimental.certified-0ubuntu1. I added suggested link to gnome-calculator and it did not work. Then I forced unity-scope-calculator package to version 0.1-0~12~raring1 (the second one available with my current apt sources configuration) and it does not work as well. I tried to logout/login after each change.

You can't mix scopes built  for the default unity in raring with the 100 scopes packages (smart scopes.
 That experimental ppa also installed a different unity so either live with what works at this point or purge the experimental ppa & the calc scope wlll work as I described in a default 13.04 install
(obviously one would need to add the raring ppa I linked

I just dumped the 13.10 install i had so can't say if the calc scope worked there in 'smart scopes'. Maybe ask in the ubuntu+1 subforum

---

### Post by VaclavC on 2013-06-24
Purged experimental PPA and edited unity-scope-calculator file ... and voila, calculator is back. Thank you all for you help!

---

### Post by kcpr on 2013-07-18
> **mc4man said:**
> assuming people are using the raring scopes ppa  - 
[https://launchpad.net/~scopes-packagers/+archive/ppa](https://launchpad.net/~scopes-packagers/+archive/ppa)
**And these raring packages** (not the '100 scopes' deal

unity-lens-utilities (0.1-0~10~raring1)
unity-scope-calculator (0.1-0~12~raring1)


When they built the raring package several weeks ago I guess no one bothered to check if gcalctool still  (or ever) installed a symlink in /usr/bin linking to the new calculator or adjusted the scope to use new name
This is why it doesn't work. 
Easy user fix, in terminal - 
```
sudo ln -s /usr/bin/gnome-calculator /usr/bin/gcalctool
```

screen from raring

Edit: turns out it is just 2 lines in /usr/lib/unity-scope-calculator/unity-scope-calculator that need to have gcalctool changed to gnome-calculator
lines 93 & 98
If those are edited then a symlink is not needed - screen 2

That works! I didn't even need to change these two lines.
Thank You a lot! :)

---

### Post by mc4man on 2013-07-18
> **kcpr said:**
> That works! I didn't even need to change these two lines.
Thank You a lot! :)
I  had contacted the ppa owner about these & he redid the scope to use gnome-calculator so all should be fine now (as you noticed

---

### Post by abateni on 2014-04-24
what shoud i do for 14.04
i've added this:
[https://launchpad.net/~scopes-packagers/+archive/ppa]("https://launchpad.net/%7Escopes-packagers/+archive/ppa")
but couldn't find these:

unity-lens-utilities (0.1-0~10~raring1)
unity-scope-calculator (0.1-0~12~raring1)

---

