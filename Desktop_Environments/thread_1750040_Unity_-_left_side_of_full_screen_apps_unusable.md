---
title: "Unity - left side of full screen apps unusable"
date: 2011-05-05
forum: Desktop Environments
---

### Post by donlogan on 2011-05-05
When I full screen an app, mostly firefox or thunderbird in unity, toolbar buttons on the left aren't selectable. I can't click back in firefox which is annoying. Window the app & the left buttons are usable, move it over to the left where the osx dock thingy is & the buttons again become unusable. The dock is set on hide from windows & is not activating when I try any of the left side buttons.

I quite like unity, but I would also like to remove the new menu & have the classic menu, having to click a few times rather than just navigate through the menu is something I'd like to get back. 

Any ideas, thanks.

Don

---

### Post by roger_1960 on 2011-05-05
Hi

It should appear when you "push" the cursor against the left screen edge (I sometimes have to do this a couple of times before the launcher appears).  If not, does it appear when you hit the "windows start" button?

You could set it to never hide...

---

### Post by Copper Bezel on 2011-05-05
Yes, try disabling the autohide in CompizConfig Settings Manager and see if this behavior persists. That way, we can find out whether it's related to the Launcher and hopefully solve the problem.

To change this setting, install CompizConfig from the repositories by searching or just running

> sudo apt-get install compizconfig-settings-manager

and run it from the Dash search or by running the command [font="Courier New"]ccsm[/font]. Look for the Unity plugin, where you can change the hide behavior.

If you really find yourself missing the old menus, consider using the Classic desktop (still available by logging out and changing the selected Session in the menu that appears below the login window after you select your username; Ubuntu will remember your choice for future logins.) The developer of the Unity Launcher also wrote a standalone dock called Docky, which is available from the repositories.

---

### Post by blackicepro on 2011-06-06
I'm having the same problem. It's set to auto hide in ccsm. It's really bad if you visit sites that have their navigation panel on the left side.

---

### Post by almalaci on 2011-06-15
Same problem here. Pretty sure it's since I installed compizconfig manager.
Very annoying issue as it occured just as I decided I will try to get used to this clumsy big dumb Unity panel.

---

