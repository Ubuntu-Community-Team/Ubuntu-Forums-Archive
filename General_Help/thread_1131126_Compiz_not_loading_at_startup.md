---
title: "Compiz not loading at startup"
date: 2009-04-20
forum: General Help
---

### Post by Nechi on 2009-04-20
I've just installed Jaunty on my Compaq Presario C700. It runs wonderfully, but Compiz won't load at startup and I get the message "Special effects could not be activated" when I try to activate it from the Appearances>Visual effects dialogue. 

I thought Metacicty was in the way, so I uninstalled it. Then I rebooted and my windows had no frame. But then I ran Compiz Fusion Icon and clicked "Reload Window Manager" and I got Compiz running with Emerald decorations. Now I have to do that every time I turn the computer on.

I also get some problems once Compiz is running, such as frequent invisible or empty dialog boxes.

What could be broken?

Thaks for your help.

---

### Post by Therion on 2009-04-20
You kind of borked things when you uninstalled Metacity.  Without Metacity Compiz is using Emerald (as best it can) to manage your Window decorations.  Compiz WAS running from the outset, or should have been from a default install, you just needed to enable the restricted driver for your video solution (assuming one exists for your video card or integrated video chip-set) to take full advantage of it.  That's why you were getting the "error" message that the effects could not be enabled; you needed to install/activate a restricted driver.

---

### Post by Nechi on 2009-04-21
Well, actually, I had the problems with Compiz even before I unistalled Metacity. But I have been reading several forums and Compiz seems to be giving a lot of trouble on Jaunty, so I'm not the only one at all.

I'll just keep using Metacity and wait until some fix is released.

Thanks for your time!

---

### Post by jazzedupj0sh on 2009-05-06
Try this,

1) Navigate to System->Preferences->Startup Applications

2) Add a new command "fusion-icon --force-compiz" or "fusion-icon -f"  . Give any Name and Comment you wish.

3) Log out and then log in again. This should now get compiz working by default.

Notes: 
          1) You don't need "compiz --replace" in the Startup Applications (as it seems to work for me).
          2) Windows manager in Compiz Fusion Icon options should be Compiz.
          3) Use the GTK Windows Decorator in Compiz Fusion Icon options.

---

### Post by daygan on 2009-05-07
Okay, so I had basically the same problem as the original poster (started after updating to 9.04 Ubuntu) - compiz wasn't loading, and therefore my Avant Windows Manager wasn't loading. the Avant Windows Manager error message was what first tipped me off to the problem, noting that I needed to run a windows manager like compiz or metacity. I also found that the compiz fusion icon fixed the issue for me, even after I removed metacity, but would not resolve the problem that compiz just wouldn't load at startup.

I tried jazzedupj0sh's suggestion, and yes, it works fine as a temporary workaround, but.. that's just the problem - it's only a workaround. The problem is still there somewhere in the recesses of the computer, because before compiz is forced to load, I still notice the error message, and then, of course, it all goes away when compiz get's loaded..

The reason I know there must be a better solution is that I have another computer that I have also updated to Ubuntu 9.04, and It has absolutely no compiz issues whatsoever. However, I still have not determined what the difference is between the two computers..

---

### Post by stinger30au on 2009-05-07
this error has been happening in every version since 7.04 when i first started using ubuntu

---

### Post by daygan on 2009-05-08
hmm.. well, it wasn't happening for me with Ubuntu 8.** so it must be a localized issue.

---

