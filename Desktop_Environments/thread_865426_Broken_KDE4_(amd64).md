---
title: "Broken KDE4 (amd64)"
date: 2008-07-20
forum: Desktop Environments
---

### Post by vertago1 on 2008-07-20
Ok I ran into a problem where kde4 decided not to start up, same problem on two computers I was able to fix it by changing the owner and group of .ICEauthority to my user instead of root. I am not sure of the security implications, but this allowed the login screen to continue into KDE4.

The other issue I had was the window decorations didn't appear from startup. I had to write a script in the .kde4/autostart/ folder to call /usr/lib/kde4/bin/kwin --replace at startup and the decorations have worked since.

These are workarounds for my probs and I would like to find the underlying issue. Let me know if yall have any insight as to the real problem.

OLDPOST:
> I rebooted 2 different amd64 computers running Kubuntu 8.04 after updates, and both of them had major issues. On one of them all the window decorations stopped showing up and the keyboard input was broken for everything except the search field on the plasma kde programs menu. I tried removing and reinstalling kde4 kdm-kde4 kubuntu-desktop-kde4. Only managing to break the system to where every time kdm tries to login it gets to the 2nd to last flashing icon and then quits back to the login screen. I have two computers doing this now and I don't even know where to begin as to how to troubleshoot the issue.

---

### Post by vertago1 on 2008-07-20
I got my system in working shape by moving back to kde3. I wish I knew how to report the problem I was having specifically.

---

### Post by vertago1 on 2008-07-31
Ok I ran into a problem where kde4 decided not to start up, same problem on two computers I was able to fix it by changing the owner and group of .ICEauthority to my user instead of root. I am not sure of the security implications, but this allowed the login screen to continue into KDE4.

The other issue I had was the window decorations didn't appear from startup. I had to write a script in the .kde4/autostart/ folder to call /usr/lib/kde4/bin/kwin --replace at startup and the decorations have worked since.

These are workarounds for my probs and I would like to find the underlying issue. Let me know if yall have any insight as to the real problem.

I put this in the top post so it would be more visible

---

