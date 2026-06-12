---
title: "Help a Noob"
date: 2007-03-11
forum: Desktop Environments
---

### Post by qbical on 2007-03-11
So i have been really wanting to try Ubuntu for sometime now and i finally did it. i installed Ubuntu 6.10 for amd64. I have to say that the installation went fairly smooth and i was tinkering in no time. I then decided to install the Beryl Package and that didnt go too too bad either. When my comp restarted it showed the little red diamond in the task bar and i am able to get into the Beryl manager and so forth. My only problem is that when i try any of the keystrokes to get the cube, nothing happens. the mouse works the same way it would w/ windows. 
I have read alot of the stickies and havent found my soultion as of yet. I also tried going into the terminal and typing some code that i read online to look for stuff in Beryl. The window opens and closes so fast, i cant see what the heck it says. 
I went into System>Synaptic Manager>Miscallaneous-Graphical (main) and checked anything i saw w/Beryl on it and in (restricted) i  checked nvidia-settings.
Sorry for such a noob post.

---

### Post by gavintlgold on 2007-03-11
Are the windows wobbly, or do they look like GNOME default?

If they are like GNOME default, then try Beryl toolbar>Select Window Manager>Beryl. Perhaps you were just still using Metacity (the gnome window manager).

---

### Post by isecore on 2007-03-11
Also, remember that Beryl is preproduction software in early alpha-stage! Not everyone can get it to work.

---

### Post by qbical on 2007-03-11
Gavin, 
My windows are all flat, so i did what you recommended and the screen goes to white, then black w/ a cursor and then back to my login. Once i log back in  to my desktop, the Metacity(Gnome) is still selected. So basically it tries to load the Beryl settings, but then craps its pants. I just bought the book Ubuntu Unleashed so hopefully that will help me some. I think im gonna reinstall Ubuntu but it looks like it will be the 6.06LTS version n not the 6.10
any input is still greatly appreciated and thanks so far

---

### Post by gavintlgold on 2007-03-11
Did you follow the instructions [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")?

I guess you have Ubuntu Edgy Eft right now, right?

If you didn't follow the instructions, then get [Envy]("http://albertomilone.com/nvidia_scripts1.html") and follow the instructions to install your nVIDIA driver. Then, follow the instructions [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX").

If you didn't install the nvidia driver, Beryl won't work because by default Edgy doesn't have the right driver. Also, you have to edit your xorg.conf file (in the instructions, don't worry). So if you just went and installed beryl simply through synaptic, it won't work.

---

### Post by LORD_PoLvO on 2007-03-11
beryl is still under dev atm and its not the esiest thing to get working right ive had plenty of trouble with it what gfx card are u using and what instructions did u follow??

---

