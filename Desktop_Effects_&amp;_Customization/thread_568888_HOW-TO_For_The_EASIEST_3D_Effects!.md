---
title: "HOW-TO For The EASIEST 3D Effects!"
date: 2007-10-06
forum: Desktop Effects &amp; Customization
---

### Post by kshane on 2007-10-06
If you're having trouble getting all the fancy 3D stuff working, i.e., Compiz, Beryl, etc., try this: **3ddesktop**.  I have an ATI Radeon x1650 and had nothing but problems after having tried ***EVERY how-to on the forums.  ***

I finally DID get Compiz working after a TON of private help from another forum user.  But, after all the work and literally hours of banging away on the keyboard making modifications and tweaks, my system was slowed to a crawl.  3ddesktop gave me the 3d desktop switcher I was impressed with the screenshots of, with **no degradation of the system**.  See the screen shot at the bottom!

So, if you're running Gnome, here's a short "how-to".  Users of KDE and others should read the docs for keylaunch to find the differences (minimal).

First, download and install through **Synaptic** the following programs:  **3ddesktop** and **keylaunch**.  Just use the search in Synaptic if you have trouble finding either one.  After installing, follow these steps:

Now, set the number of desktops you want by using the default "**Workspace Switcher**" that comes with Gnome (right-click and choose "properties").  If you don't have it on your panel, put it on the panel by right-clicking the panel and choosing "Add To Panel", then, after setting your number of desktops, you can remove it.

Next, open terminal and cut & paste the following ("user" is your home directory):

```

cd /usr/share/doc/keylaunch
cp example_rc /home/"user"/.keylaunchrc

```

Now, open a text editor in the terminal (and enter your password) as follows:
```

cd /home/"user"
gksudo gedit .keylaunchrc

```

paste these lines below and then save and close gedit
```

key=...F2:3ddesk --acquire
key=...F3:/usr/bin/3ddesk

```

Next, go to System>Preferences>Sessions.
Click on NEW.  Add the word "**keylaunch**" under Name and Command, then click OK and CLOSE.

Now, restart your session, either by <CTL>+<ALT>+<BACKSPACE>, or logging off and back on or by rebooting.

When you're back to your desktop press F2 to acquire the desktops you've set up.  **You only need to hit F2 when the desktop first comes up.**  You don't need to do it again, unless you restart your desktop. Wait 5 or 10 seconds, then hit F3.  You should then get a view like the one abo.  By using your right or left mouse buttons, or the right and left arrow keys, you should be able to spin the desktops in either direction until you are at the desired one.  By hitting spacebar or enter or middle mouse button, you should bring the desktop back to the front.  Use F3 to change desktops again.

Hope it works for you as well as it does for me!  

And please let me know (reply here) if ya have any troubles with this, see an error or know of a better way!

Kevin

---

### Post by britishbulldog on 2007-10-06
I couldn't find 3ddesktop in the synaptic package manager, I am running gutsy now. I just got my dual head (laptop and 20.1" widescreen) working properly. I tried the GLdesktop but it blows up and won't run.:(

---

### Post by kshane on 2007-10-06
> **britishbulldog said:**
> I couldn't find 3ddesktop in the synaptic package manager, I am running gutsy now. I just got my dual head (laptop and 20.1" widescreen) working properly. I tried the GLdesktop but it blows up and won't run.:(

Hmmm.  Sorry, I know absolutely nothing about Gutsy.  Maybe you can get it using apt-get?  I had a ton of trouble using the other stuff, too.  I'm waiting for the full release of Gutsy before I try it...

Kevin

---

### Post by kshane on 2007-10-08
> **kshane said:**
> Hmmm.  Sorry, I know absolutely nothing about Gutsy.  Maybe you can get it using apt-get?  I had a ton of trouble using the other stuff, too.  I'm waiting for the full release of Gutsy before I try it...

Kevin

Yep...  No doubt.  I just upgraded to Gutsy and 3dd3sktop is not available to Gutsy users...  Darn!

Kevin

---

### Post by kghosh22 on 2007-10-08
If I want to start an application, say WMPPP, on the third workspace, everytime with effects like "Always on Top" and "Always on Visible Workspace", and I want this to happen whenever I start my desktop, how do I do it ?

---

### Post by kshane on 2007-10-12
> **kghosh22 said:**
> If I want to start an application, say WMPPP, on the third workspace, everytime with effects like "Always on Top" and "Always on Visible Workspace", and I want this to happen whenever I start my desktop, how do I do it ?

I believe by right-clicking on the top of the application window...

Kevin

---

