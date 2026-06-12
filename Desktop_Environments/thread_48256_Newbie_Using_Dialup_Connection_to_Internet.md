---
title: "Newbie Using Dialup Connection to Internet"
date: 2005-07-11
forum: Desktop Environments
---

### Post by Mic on 2005-07-11
Using a US-Robotics 56K modem and it works okay when in SuSE. 
But when connected using Ubuntu, the speed is very very slow, 3-5 minutes for this page to load, if at all.

Any idea what can be done?
- when installing Ubuntu, it tries to detect the DHCP connection which obviously is not there (i am using it at home) and so i bypass it, this shouldn't be causing the problem, right?

How can I see the speed of the connection?

Is Ubuntu setup with a firewall by default?

Many thanks in advance for the advice.

--------
Edit:

Just logged into Ubuntu - the dialer (modem_applet) had crashed.  What luck!
Anyway to bring it back ?

---

### Post by jasmuz on 2005-07-11
[QUOTE=Mic]Using a US-Robotics 56K modem and it works okay when in SuSE. 
But when connected using Ubuntu, the speed is very very slow, 3-5 minutes for this page to load, if at all.

Any idea what can be done?
- when installing Ubuntu, it tries to detect the DHCP connection which obviously is not there (i am using it at home) and so i bypass it, this shouldn't be causing the problem, right?

How can I see the speed of the connection?

Is Ubuntu setup with a firewall by default?

Many thanks in advance for the advice.

--------
Edit:

Just logged into Ubuntu - the dialer (modem_applet) had crashed.  What luck!
Anyway to bring it back ?[/QUOTE]
 I have an External 56k US Robotics modem on ttyS0 wich works fairly well under Ubuntu.

dhcp has nothing to do with the dial up issue.
When you created the connection, what is the maximum speed you placed for your line? 

If you want to restablish the modem applet, just load it again (it crashes sometimes because of a know issue).

---

### Post by Mic on 2005-07-12
What i did was, I reinstalled the entire Ubuntu. I cannot even attached the modem_applet onto the panel. It crashed automatically? when it started.

Anyway, with the network monitor, I am able to access the dialup connection and setup the number to dial, the ID and the password. I use the option to detect the modem automatically (ttys0).

WIth this, I can connect, but I can only reach google. Trying to access this page cause more than 2-3 minutes and still a blank page.

---

### Post by Navin_Johnson on 2005-07-13
I had slow modem problems when I first installed Ubuntu.  I forget exactly why, but the solution for me was to install and use gnome-ppp rather than the modem-applet application.

good luck

---

### Post by krokodil on 2005-07-18
I found the solution to a similar problem following this thread:
[http://www.ubuntuforums.org/showthread.php?t=28514&highlight=robotics+slow](http://www.ubuntuforums.org/showthread.php?t=28514&highlight=robotics+slow)

Which leads you here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8890](https://bugzilla.ubuntu.com/show_bug.cgi?id=8890)

Which has the following to say:
 ------- Additional Comment #3 From Michael Vogt  2005-04-12 22:54 UTC  [reply] -------

Thanks for your problem report.

As for 2)
Could you please open the file /etc/ppp/peers/ppp0:
$ sudo gedit /etc/ppp/peers/ppp0
and add the following line at the end:

115200

(only the number, nothing else)

This will set the speed of the serial interface. Could  you 
than tell me if it helps with the speed/performance problem?

1) is pretty hard to deal with and is a problem with the changes that 
happend in gnome to the modem-applet. 

-------------------------

I wrote it all down here because I had to find the solution on a very slow modem connection too and it took **AGES** page hopping to get this information, thought it would be simpler for future users to have it all in one spot.

-Rudolf

---

