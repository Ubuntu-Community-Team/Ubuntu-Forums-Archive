---
title: "Freezing when logged out"
date: 2011-01-21
forum: Desktop Environments
---

### Post by Fracta on 2011-01-21
I just recently made a new user so that other people can use my computer when I'm not around, and I have noticed things aren't working right. For example, I started a few files downloading in Firefox and then clicked 'Switch from Fracta', expecting it to be like windows and the downloads would continue in the background while people log into the other account. But the screen just went black. Completely unresponsive. It wouldn't let me ctrl-alt-f1 to the command line and alt-sysrq-R,S,E,I,U,B didn't shutdown and restart the pc. 
Also, It is not uncommon for the computer to freeze when my screensaver starts after however long of inactivity and the computer doesn't respond at all.
Does anyone know whats going on?

---

### Post by Krytarik on 2011-01-22
It's most likely video driver related. What video card/chip is installed, what driver are you running?

---

### Post by Fracta on 2011-01-22
I have an ATI Radeon that used to be running the drivers off the ati site, but I remembered seeing the "Additional Drivers" menu item so now I'm running the proprietary FGLRX drivers to see if that makes any difference.

---

### Post by Fracta on 2011-01-25
Nope, didn't fix it. This time my screen froze seconds after the screensaver went on. I came back and clicked the mouse or pressed a key to bring up the login window and the screensaver froze. The time for starting the screensaver is quite short so I have been re-logging in frequently and i thought the problem had been fixed. Any idea what causes this?

---

### Post by Krytarik on 2011-01-25
I do indeed experience a similar behaviour at my mum's machine, it has also a ATI Radeon card, but runs NOT the proprietary driver because it isn't supported by those anymore. Instead of freezing completely, it goes to a black screen with blinking cursor, if one tries to switch users. By pressing Alt+Ctrl+F* one is able to get to the login screen.

In your case, you could try 

- to create a new "xorg.conf":
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)

- to install the proprietary driver build by Ubuntu-X-Swat:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA)

---

