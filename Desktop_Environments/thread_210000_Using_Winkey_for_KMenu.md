---
title: "Using Winkey for KMenu"
date: 2006-07-06
forum: Desktop Environments
---

### Post by srunni on 2006-07-06
Is there any way that I can associate the Winkey with the KMenu?
Thanks in advance for the help.

---

### Post by aysiu on 2006-07-06
From the KDE website: > How do I use the Windows® key to open the K menu?
	

Previous versions of KDE provided a trick to allow you to use the Windows® key both as a modifier (so you could have shortcuts like Win+R), and as a regular key (so that pressing Win on its own could open the K menu). This feature was removed for reasons of usability and accessibility, as well as keeping the code clean. For current versions of KDE, you have two options: either use a different shortcut to open the K menu (the default is Alt+F1), or remap the Win key to be a regular key, rather than a modifier.

If you choose to do the second, here's one way:

   1.

      Find the keycode for your Win key using xev: Run the command xev in a Konsole, and press the Win key. Look in the output of xev for keycode n, where n is the keycode of the Win key.
   2.

      Use xmodmap to remap the Win key. An appropriate command is xmodmap -e 'keycode n=Menu'.
   3.

      In the KDE Control Center, go to Regional & Accessibility->Keyboard Shortcuts and set the shortcut for Popup Launch Menu to the Win key. You should now be able to popup the K menu by pressing the Win key.
   4.

      One more step is required to save the changes across settings: Create a file ~/.kde/env/win-key.sh (create the directory if it doesn't exist), and add the xmodmap command you used previously to it. The change should now be applied every time you start KDE.

---

### Post by srunni on 2006-07-06
I think this worked for me; I just have one question - why do you have to do both steps 2 and 3? Shouldn't just step 3 fix the problem?

---

### Post by BatteryCell on 2006-08-18
Step two just tells you what you should substitute in for n in the command.
Oh and thanks aysiu :-)

---

