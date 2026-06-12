---
title: "Can't click Keep Settings for Visual Effects change 7.10"
date: 2008-02-07
forum: Desktop Environments
---

### Post by dvord on 2008-02-07
Long story since the background might illuminate a cause.

When I got 7.10 installed finally and my mouse working ok, I installed the restricted Nvidia drivers, compiz-manager and had lots of fun making all kinds of neat desktop transitions.  Since I had the horsepower, I figured  what the heck.  

Well I started having problems getting CounterStrike to work, so I installed Wine-Doors, tweaked some of the Wine settings, but nothing serious.  I decided to turn my Visual Effects to None in order to get CS working right.  Turns out it doesn't like widescreen.  Fine, I got it working.

Now since I know compiz wasn't the problem, I went to enable my Visual Effects again.

I change settings to ANYTHING besides None and things change, yet I cannot click the button that says Keep Settings.  I can't click the other either.  My mouse cursor is there, but when I press the mouse button the cursor turns into a hand like it's going to move the window.

I'm a little confused.  Any suggestions?

---

### Post by dvord on 2008-02-07
/bump

---

### Post by boc-sixtyniner on 2008-02-08
I'm having the same problem-- buttons (and other things of that nature) fail to respond to mouse clicks while Desktop Effects is active.

Also, right when this began, I stopped being able to modify my wireless settings. I get an error box telling me that "The configuration could not be saved. You are not allowed to modify the system configuration." I think the two problems are related, simply because they both started happening at the exact same time. I have no idea if this indicates what the problem may be, however.

I'm running Hardy amd64. Any help would be greatly appreciated...

---

### Post by dvord on 2008-02-08
Interesting, the network settings denial sounds definitely like a permissions issue.

I'm not sure what file is being modified when you are playing with those settings.  Are you prompted with a "enter password to perform administrative tasks" when you try to change the network settings?

---

### Post by boc-sixtyniner on 2008-02-08
It prompts me for a password, and allows me to change interface details and such, but then when I close the window I get the message about not being able to change the system configuration. This is still happening, but I was able to finally able to activate the wireless interface by editing the /etc/network/interfaces file. For whatever reason the "auto wlan0" entry had been removed from the interface details, so I put it in again above "iface wlan0 inet dhcp." After that I ran ```
sudo ifup -a
```which put me back online. Still can't change the settings from the application, which definitely does indicate a permissions error. 

I don't know enough about the gnome configuration files to be able to tell whether or not the desktop effects issue is actually related, but both issues started within a couple minutes of each other. 

I'm still getting the desktop effects error though. It's definitely the most annoying and bizarre linux freak-out that I've seen. I've never found myself wishing for an xorg.conf problem before, I can fix those in my sleep by now.

[update]

I just found that if I shift+left click rather than just clicking on a button, the mouse activity works normally. So I'm guessing that there's some sort of setting in compiz that's been fudged. Had to leave to do laundry, I'll look into it more when I get back.

---

### Post by pizpot on 2008-03-20
I have it too now, and I got it after tinkering with one of the settings. I wish I knew how to reset it by deleting the right hidden file in my home folder. Good tip about the shift-click. Hehe, quite the security setting ;-)

---

### Post by pizpot on 2008-03-20
I fixed mine!

I opened a terminal window, and then listed my hidden files with:

ls -a

and then I renamed two files and rebooted. (probably just needed to log out) So, I don't know which file needed nuking, but oh well. At least that annoying problem is solved. By doing this, I lost all my desktop settings by the way. The files were:
.gconf and .gconfd

The commands to rename them are this:

mv .gconf .gconf-disable
mv .gconf .gconfd-disable

You could also just delete them with 

rm -r .gconf

but that is not the way I operate. Cheers.

---

