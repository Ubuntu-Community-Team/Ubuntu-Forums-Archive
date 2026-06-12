---
title: "Urgent Xserver / GDM problem"
date: 2006-10-04
forum: Desktop Environments
---

### Post by GadgetsGuy on 2006-10-04
** I am willing to pay anybody $50 by paypal that can offer me the solution to this problem:**

I am having a problem with Dapper Drake 6.06LTS that has prevented me from logging in for 4 days now.

When the boot gets to where GDM should kick in, it hangs with a black screen with the circle icon (system working) spinning ...

I left it over night, and the same circle is spinning around.

I can enter the CLI using recovery mode without any problems. I have reconfigured xorg as well as dpkg --reconfigure -a both with no change whatsoever.

I have vmware server set up running win2000 and a few installed apps that I need (flash, dreamweaver, and Photoshop), so reinstalling ubuntu is not really an option, nor do I think it is neccessary, as I am able to start in recovery mode without any problems.

I also removed and re-installed the ubuntu-desktop yet the login screen still does not appear ... the system hangs right where the login screen should appear with that little spinning circle to say the system is busy

When I try to reconfigure gdm in recovery mode, i get this error with a red star:

[b]* Changes will be made after all current versions of X have ended.

invoke-rc.d: initscript gdm, action "reload" failed[/b]

I have found many people with the same type problem in many forums, but I have not found any solution

---

### Post by GadgetsGuy on 2006-10-04
bumping for somebody who wants to make an easy $50

I know there are many Linux geniuses here ..

---

### Post by GadgetsGuy on 2006-10-04
This is unreal .... some of you guys can do all kinds of crazy things in linux, yet NOBODY can tell me how to restore my system to its previous non-broken state?

Well maybe somebody can tell me how to reinstall linux on top of itself like windows can, so I do not lose the other installed applications (IE: VMWare Server with Photoshop, Dreamweaver, and Flash)

---

### Post by bonzini on 2006-11-07
Hi there;

I don't know if you've solved your problem yet, but in case you haven't, here's something that happened to me.

A few kernel updates ago, in fact right around when 6.06 went stable, I stopped being able to get an X session going.

I finally thought to try a previous kernel release from the boot list, and sure enough, up came X.  You might want to do the same.

You should also look at your log files for errors.  Mine was really difficult to find, turned out to be that just before the Xserver started loading, my IRDA device caused a kernel panic.

Anyway, if this helps solve your problem, great, no need for the paypal thing, or if you really want to spend it donate it to the Ubuntu folks.

---

