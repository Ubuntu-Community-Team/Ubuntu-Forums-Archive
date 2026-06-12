---
title: "Unity No Longer default GUI at login"
date: 2012-02-14
forum: Desktop Environments
---

### Post by Jgourd on 2012-02-14
I have asked this elsewhere and gotten absolutely nowhere.

Yesterday while at the login screen for 11.10 I stupidly chose "Recovery Console" from the little gear menu. What happened after that is that a small terminal window opened in the top left of my screen. At this point the keyboard would not enter anything.

I hit CTRL-ALT-F1 and got to a login prompt. I login and everything seems OK. I do a sudo shutdown -r now and the machine comes back up in the recovery console and again, I can't type. Maybe it is the USB keyboards I have tried, I don't know but a PS2 style keyboard is next on my list to test. As before I can hit CTRL-ALT-F1 and use the terminal interface just fine. ALT-F7 takes me back to the little XTERM in the upper left corner where I can't type anything.

Can I assume that since a menu item did this to me that a command line can get me out of it? This really doesn't need to be rocket science. X doesn't need to be restarted. startx complains that it is already running. I have re-installed the Ubuntu desktop, and tried all sorts of things suggested in other forums. Nothing has gotten me back to the GUI.

Just tell me how one who invokes the recovery console can switch back to Unity please?

---

### Post by Jesus_Valdez on 2012-02-14
I'm guessing that you have automatic log in enable?

If that's the case I think that the file that needs to be edited is ¨sudo nano /etc/lightdm/lightdm.conf"

At least according to [https://help.ubuntu.com/community/AutoLogin#Enabling_AutoLogin_from_command_line](https://help.ubuntu.com/community/AutoLogin#Enabling_AutoLogin_from_command_line)

---

### Post by Jgourd on 2012-02-14
This turned out to be really simple but frustrating to solve.

It turns out the X Console I was logging into didn't have focus and that is why it did not take my keystrokes. I moved the mouse over the prompt and the keyboard worked. All I had to do was type "exit" and I was back to the GUI login screen. I changed the default interface back to Unity and all is good.

---

