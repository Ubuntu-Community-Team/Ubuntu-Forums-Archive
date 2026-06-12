---
title: "Admin problems again."
date: 2011-09-21
forum: Desktop Environments
---

### Post by Aisaka_Tiger on 2011-09-21
I recently bought and replaced my HD 4870 with an HD 6870. A worthy upgrade overall. But it's accosted me some problems.

For starters, despite the fact my main user has been given all privileges, I've come across my first problem similar to the ones I had under Kubuntu. That it wouldn't recognize my authority to make changes or decisions despite the fact I had given them to an account.

In this case, the new graphics card came with new graphics drivers. And a sort of new Catalyst Control Center. One problem though, it won't allow me to modify some things because it says I need administrative privileges. But I do have them. And I can't find any ways to give myself more or create another account with more privileges.

The limits this has caused me is that playing fullscreen games gives me a big "1" telling of the monitor number, even if I only have one plugged in. "Identify display" is permanently ticked. This is a real annoying distraction when playing games. And number two, for multi-monitors, it is stuck in clone mode when I want to have more real estate.

But again, I don't have administrative access. Despite the fact I really do. And have no problem with it in most applications. I've tried clicking "ATI Catalyst Control Center(Administrative)", but absolutely nothing opens. It does nothing.

---

### Post by wildmanne39 on 2011-09-21
Hi, if you use a terminal put the command sudo in front of the command being used.

Open the Catalyst with the terminal by using gksu or gksudo in front of the command when you open a graphical program that prevents root from becoming the owner and give you admin rights.
Thank you

---

### Post by haqking on 2011-09-21
+1 to the above.

please read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") which explains the use of sudo/gksudo etc for gaining access to elevated privelege.

Make sure you read it thoroughly and understand its concepts, especailly that of not unlocking the actual root account or logging in as root.

using sudo (superuser-do) or for graphical apps gksudo you will gain the admin privelege you require.

Cheers

---

