---
title: "Wireless problems on an Inspiron 1420"
date: 2007-10-26
forum: Dell  Ubuntu Support
---

### Post by barrrol on 2007-10-26
Hey, I just installed Ubuntu feisty fawn on my Dell Inspiron 1420 (same intel wifi card as every other one) and I have absolutely no wifi. The wifi light doesnt even light up. I need some help on how to fix this, ive searched the forums and havent found anything.

Thanks

---

### Post by RobertGloverJr on 2007-10-27
I have the same problem.  I bought new Inspiron 5 days ago with ubuntu 7.04 installed. There are no directions whatever in the packaging that refer to Linux or Ubuntu at all.  The manuals only have windows commands in them.
   There is a Wifi light on the front of the laptop that is not on.  There is an on/off switch to the left of it, but pushing it toward the on direction does not make the light go on either.  The manual that comes with the inspiron says on page 24 that "When enabled through Dell Quick Set, this switch can scan for a wireless LAN in your vicinity".   Page 86 of the manual says that "Del Quick Set" is accessed by clicking the QuickSet icon in the task bar.  Obviously that refers to Windows, not Linux.
   It almost seems as if Dell is deliberately making it as hard as possible for use Linux with the Inspiron.  How else to account for their being no directions included in the box with the Inspiron.
   Please, please, if anybody out there has any clue how to get the Inspiron 1420 working with a wireless connection using ubuntu 7.04, let us all know.
   The internet connection through an ethernet wire to my router is working correctly.  It's only the wireless that is a total, undocumented  mystery.

---

### Post by sleepykit on 2007-10-27
Did you dell come with Ubuntu?

I have an Inspiron 1420 with Ubuntu preinstalled, so it might be a little different, but for me, NetworkManager refused to do anything useful at all. So, I went out and found WICD [http://wicd.sourceforge.net](http://wicd.sourceforge.net) and installed that instead. It seemed to pick up the wireless card with no problem.

Maybe try
 
```
sudo ifconfig
```

And see if it's even brining up eth1, which for me, is the wireless interface...

---

### Post by RobertGloverJr on 2007-10-27
> **sleepykit said:**
> Did you dell come with Ubuntu?

I have an Inspiron 1420 with Ubuntu preinstalled, so it might be a little different, but for me, NetworkManager refused to do anything useful at all. So, I went out and found WICD [http://wicd.sourceforge.net](http://wicd.sourceforge.net) and installed that instead. It seemed to pick up the wireless card with no problem.

Maybe try
 
```
sudo ifconfig
```

And see if it's even brining up eth1, which for me, is the wireless interface...

   My Inspiron 1420 came with Ubuntu 7.04 preinstalled.  I will try your suggestion (ie. to install WICD) but first I have an important question. On of the google hits I found said to first make sure the "Wifi" light is on.  Well, the "wifi" light is not on.

    Do you have any suggestions how to get the "wifi" light on the front of the inspiron 1420 to go on?

Thanks in advance

---

### Post by sleepykit on 2007-10-27
On my dell, the light is off unless connected to a network. It blinks sometimes when the interface is searching for networks, but is otherwise off. There' a little switch on the front of the laptop that you can switch to turn the wireless on and off, and it has to be in the "right" (vs "left") position in order for the wireless to work. Otherwise, if ubuntu is not currently trying to bring up that card, there's likely not going to be a light (at least in my experience). Hope that helps...

---

### Post by RobertGloverJr on 2007-10-27
I'm making some progress.  The Wifi light on the front left of the 1420 blinks now.  What I did was turn the switch to its left off (to the left) and then on (to the right).
   I installed WICD using the ubuntu instruction at this address: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
  Now the problem I am having is that this command which the instrcution said to execute returned the error "No such file or directory":  sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py

   There is definately an /opt/wicd directory and it contains tray.py  

   So what I need to figure out is where Wicd installed itself;  specifically, where wicd installed "tray.py".

---

### Post by RobertGloverJr on 2007-10-27
I said that wrong.  Of course I know where wicd put tray.py : it put it in /opt/wicd

 What I meant to say is, I don't know where .kde/Autostart/tray.py is

   I tried simply entering as a command:  "/opt/wicd tray.py"  but that returned "command not found".

---

### Post by sleepykit on 2007-10-27
Try this for me, and I's sorry in advance, I'm not as familiar with KDE, but try this:

press ALT+F2 and in the window type in exactly
```
/opt/wicd/tray.py
```

Does that put in the tray at all?

Also, and I'm not sure this will be of much help, but I use version 1.3.4 which is their latest testing version, so mayhaps there are differences. *is a linux newbie too*

---

### Post by RobertGloverJr on 2007-10-27
Horray!  The wireless is working now!  Thanks you so much for telling me about wicd!  I didn't realize the installation instructions at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) gave 3 different ways to do the same thing.  
    I used the 1st of the 3 ways and it worked, taking effect after I restarted the Inspiron. (I.e., :  In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). )
   Not only is the WIFI working perfectly (with the blue WIFI light steadily on), but in the wicd screen when I left clicked on wicd in the tray and then right clicked on "connect.." it showed me all my neighbors WIFI connections and offered to let me connect to any one of them.
    Thanks you so much!
     I think the next thing I'll spend some time worrying about is setting up WIFI security.  Suggestions appreciated for the best approach.

---

### Post by RobertGloverJr on 2007-10-27
Sigh. Another problem has come up. It takes anywhere from 5 to 10 minutes for the wicd screen to appear.  I found more installations instructions at [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)  which directed me to uninstall  network manager via sudo aptitude remove network-manage
but that did not seem to make any difference.
   Just when I've given up hope the wicd screen will appear, it suddenly appears.  Once it appears it works perfectly.  I click on the connection button for my wireless router and am good to go.
  I'm thinking about doing (yet) another factory re-install now that I know a little more about this ubuntu wifi business.  Maybe that "network-manager" would work if I could find some way to start it up.
  Anectdotes/advice appreciated.
Robert

---

