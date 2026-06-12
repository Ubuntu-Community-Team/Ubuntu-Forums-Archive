---
title: "gnome take loooong time to start and panel crash"
date: 2005-06-15
forum: Desktop Environments
---

### Post by glasscleaner on 2005-06-15
my gnome take looong time to start and it ask me to delete applet each time because it crash. i dont know why

someone ahve the same issue?

can i re-install complete gnome?

---

### Post by sethmahoney on 2005-06-15
Did you get a message about HAL failing?

---

### Post by glasscleaner on 2005-06-15
no!

---

### Post by sethmahoney on 2005-06-15
Weird!  A lot of people have had pretty much the same problem, but they got that message.  I guess the next question is: Has it done this every time since you installed Ubuntu?

---

### Post by glasscleaner on 2005-06-15
i made a fresh new install and since i do that this happend.

---

### Post by sethmahoney on 2005-06-15
Did you install Hoary or Warty?  Which version were you using before the fresh install?

---

### Post by Cordate on 2005-06-18
I'm getting something like this in Hoary- I log in as usual but I don't get much of my desktop- just the top and bottom bars with nothing in them but the "show desktop" button. After a while I get the HAL message. 

I've reinstalled GDM and Gnome but it's still not working. I'm off to try looking at xorg.conf to see if there's anything to do done there, but that seems unlikely as things were working fine for a week. Maybe I should reinstall my xserver?

Edit: I just rebooted (I tried this before and it didn't work then) and now things are fine. Odd.

---

### Post by xbaez on 2005-06-27
I have Gnome working fine, but after a while, BUM, gnome-panel just stops working

Hey folks do you think it's because I'm running Gnome as root?

before somebody ask why I do so, because I sync my machine with my server and I need root access in order to edit all the files I want in my hard drive with my CrossOffice Macromedia Dreamweaver MX

;)

I am having the same problems at house, I hope that running as a normal user will clean the mess

Or I will delete the 'default' folder as stated here in this forum.

---

### Post by cmfarley19 on 2005-07-05
I have recently installed 5.04 and experience this as well.  There is a difference.  I have installed this on a laptop.  When I boot within my company, I experience this problem, when I am at home, I do not.  My company has a firewall that requires authentication and only opens ports 80 & 443.  I suspect that something, applet or other, is trying to access the internet (maybe NTP?).  At home, outgoing traffic is wide open (more or less).  therefoe I do not see the problem there.

Any thoughts?

---

### Post by xbaez on 2005-08-02
[QUOTE=cmfarley19]I have recently installed 5.04 and experience this as well.  There is a difference.  I have installed this on a laptop.  When I boot within my company, I experience this problem, when I am at home, I do not.  My company has a firewall that requires authentication and only opens ports 80 & 443.  I suspect that something, applet or other, is trying to access the internet (maybe NTP?).  At home, outgoing traffic is wide open (more or less).  therefoe I do not see the problem there.

Any thoughts?[/QUOTE]
 I will just recommend you to do is:
apt-get install kubuntu-desktop

You could
a) follow the guidelines at this URL:
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)
b) download KDE in your office, and then copy the /var/apt/cache/* files (the ones that you downloaded in order to install KDE) into a flash memory and take them home.

I really thing KDE is like owning a top of the line Window Manager (I don't want it to compare with anything, best thing I've seen) vs owning a Window$ 95 (sorry, I did give Gnome a try)

---

