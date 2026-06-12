---
title: "Network Montior"
date: 2005-11-13
forum: Desktop Environments
---

### Post by kelsey23 on 2005-11-13
Hi, what is the name of the Gnome Network monitor application? (the one with the little icon in the panel) I want to use it but I am using XFCE, and I forgot the name right now :-/

---

### Post by matthewv on 2005-11-13
Not sure if this is what you mean, but I use network manager,
```
sudo apt-get install network-manager
```

---

### Post by kelsey23 on 2005-11-13
I have it installed, when I used Gnome before I used it. I just need the name of it so I can launch it from the shell.

---

### Post by kelsey23 on 2005-11-13
*bump* anyone? Some has got to know lol..........

---

### Post by dbott67 on 2005-11-13
```
gnome-nettool
```
-Dave

---

### Post by dbott67 on 2005-11-13
Just noticed that I get a 'segmentation fault' when trying to run from a terminal.  Works okay from the command line, though.

-Dave

---

### Post by kelsey23 on 2005-11-13
The one I need is the one that sits in the panel and shows when packets are being sent out or coming in....... and when you click on the icon (of two monitors) it has a window that pops up and says hoe much data has been transfered :-)

---

### Post by Dr. Nick on 2005-11-13
If you mean the 2 little monitors with the status bars display when on wireless, I  dont think it can be used in XFCE since its a gnome panel applet and not a seperate program. "gksudo network-admin" will launch the same configuration program that the applet will though.

---

### Post by bionnaki on 2005-11-13
"network monitor" is what comes with breezy

---

### Post by dbott67 on 2005-11-13
Oops... sorry.  BTW, I'm now getting segmentation faults in both CLI and when running from the menu! D'Oh! :)

---

### Post by kelsey23 on 2005-11-13
Alright, I tihnk you are right about the not working with XFCE part, I though it might because a few applications that put an icon in the panel put an icon in the XFCE panel, but maybe not.

---

### Post by Dr. Nick on 2005-11-13
what you can do if you want is to open up a terminal and type gnome-panel and it will launch the gnome panels in xfce I believe. You could edit all that you dont want off of the panels but that may mess them up if you ever want to use gnome. Also if its a slow computer it may hog too much memory

---

### Post by dbott67 on 2005-11-13
I've got the 'network status lights' blinking on my toolbar and when I type 'top' at the command line, there is a process called 'gnome-netstatus' that's running.

EDIT: actually, ps -aux returns 'gnome-netstatus-applet'

-Dave

---

### Post by dbott67 on 2005-11-13
Here's the complete path to running process:
```
dbott    13315  0.4  4.6  19468 11840 ?        S    17:28   0:06 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID:GNOME_NetstatusApplet_Factory --oaf-ior-fd=44
```

---

### Post by Dr. Nick on 2005-11-13
Hmm I tried to execute the above from within gnome and it still didnt work right, I think the problem may be that you have to have a gnome-panel process running for the icon to show up

---

