---
title: "Need Help username and Password dont work"
date: 2006-09-09
forum: Desktop Environments
---

### Post by engineering.concepts on 2006-09-09
Please help,
My username and password do not work anymore! I followed the instructions at 
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
but it says that my system is already up to date. 
I forced a reinstall to make sure, but it still does not work,
I know that my username and password are correct because I needed them to try to update my system..... any thoughts?
THANKS!!!!

---

### Post by aysiu on 2006-09-09
When you say they "do not work," can you be more specific? What happens when you try to log in?

Are you unable to log in graphically, via the terminal, using either? What error message do you get when you try to log in?

How were you able to update your system without being able to log in?

---

### Post by engineering.concepts on 2006-09-09
I will try to give as much detail about the problem, feel free to ask as many questions as necessary - I will be more then happy for anyone's assistance

From power on- everything looks normal - goes to GUI login screen
I enter my username - GUI now askes for password
I enter my password - Screen goes black - see a command prompt - 
Screen goes brown - see a "wait" icon (circle with spinniy lines all around)
Goes back to GUI login screen. 
I can try this many times and it will just repeat the cycle
I thought I might have a similar issue as listed in [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
so I hit "ctrl-alt-F1" to get me to a prompt.
I enter my username
prompt asks for password - I enter my password - I am in
I can type ls to see all my files,
so I tried the steps listed on [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
ie.
sudo apt-get update
sudo apt-get install xserver-xorg-core
but it tells me that my xserver-xorg-core is up to date. 
I tried sudo apt-get install --reinstall xserver-xorg-core
and it reinstalled, but when I reboot, I get the same problem.

Hope this helps......

---

### Post by engineering.concepts on 2006-09-10
Any thoughts?......

---

### Post by engineering.concepts on 2006-09-10
](*,) ](*,)

---

### Post by techstop on 2006-09-10
If you can get to the GUI for login, then you don't have the update issue you linked to. The symptoms of that are that X won't start, therefore no GUI. You have some other problem...

---

### Post by engineering.concepts on 2006-09-10
This issues is with my compaq n800c - 
I tried
sudo dpkg-reconfigure xserver-xorg
and set it up, but still the same issue

then I tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
and downgraded my xserver
still no luck!!!!!

This is driving me crazy! I can log in from the prompt, but need a gui!!!
how can a see any gui????
typing - xserver at the prompt gives me an error
typing - xubuntu at the prompt gives me an error
typing - ubuntux at the prompt gives me an error

I thought one of these would start a gui?

---

