---
title: "Wine menu launcher"
date: 2009-05-29
forum: Desktop Environments
---

### Post by ezekiel000 on 2009-05-29
I have been trying to add a launcher to the gnome menu for some of my wine games, but I have found that when I add them to the menu the games complain about missing files. This doesn't happen when I run the same command within the games directory they work fine.
I used to have this problem with Sam & Max Season One but I got round this by using this command:
env WINEPREFIX="/home/ezekiel/.wine" wine "C:\\windows\\profiles\\ezekiel\\My Documents\\Games\\Sam and Max - Season One\\Episode 1 - Culture Shock Data\\SamMax101.exe"
instead of just:
wine "/home/ezekiel/Games/Sam and Max - Season One/Episode 1 - Culture Shock/SamMax101.exe
The first works from the menu but the second only works from within the Culture Shock directory.
But I tried the same thing with real myst but it didn't work, the new command:
env WINEPREFIX="/home/ezekiel/.wine" /home/ezekiel/Games/realMYST/wine/wine "C:\\windows\\profiles\\ezekiel\\My Documents\\Games\\realMYST\\RealMYST.exe"
Old command:
/home/ezekiel/Games/realMYST/wine/wine ./RealMYST.exe
(A small note I am using a local version of wine because real myst doesn't work with the latest version of wine but Sam & Max doesn't work with the stable version)
Both the commands don't work unless I run them from a terminal within the real myst directory.

Can anyone help?

---

### Post by andrea000 on 2009-06-01
if i understand what you are saying when you launch from the menu
it doesn't do anything.Go to system->preferences->main menu on the
left side pick the menu from there and on the right side pick the sub
menu and click properties and under command type the right command
in.

---

### Post by ezekiel000 on 2009-06-01
Thanks for the reply, but it does launch when I click the menu entry but the game that is launched can't seem to find the rest of the game files even though it works fine if I start it from a terminal from within the game directory.

---

### Post by andrea000 on 2009-06-01
> **ezekiel000 said:**
> Thanks for the reply, but it does launch when I click the menu entry but the game that is launched can't seem to find the rest of the game files even though it works fine if I start it from a terminal from within the game directory.

That's odd sounds like the command for the launcher is messed up
i would check the command in system->preferences->main menu just
to make sure it was the right one.You should post this in the ubuntu
wine forums i would say they could help you better and faster.
good luck

---

### Post by ezekiel000 on 2009-06-01
I think the problem is that the game thinks it is beign launched outside of it's folder so that when it looks around for the game files it can't fin them.

Is it possible for this thread to be moved to the correct forum then?

---

