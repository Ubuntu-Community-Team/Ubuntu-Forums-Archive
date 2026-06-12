---
title: "No Volume Control in Xfce"
date: 2008-01-19
forum: Desktop Environments
---

### Post by Comhra on 2008-01-19
I'm running the Xfce desktop environment and I want to continue doing so in tandem with Gnome.

I've encountered a few things that puzzle me such as where is Volume control?

It's not in Add items to panal which is where I'd expect it to be.  So how do I manage Vol. Control in Xfce?

There doesn't seem to be a default dictionary nor a screen capture facility.  I suppose these are part of the Gnome desktop package and they're absence is explained by the fact that I'm using a different desktop manager...right?

Are there alternative dictionary and screen capture packages that I can use when working in Xfce and if so how would I install them using terminal?

---

### Post by afoglia on 2008-01-20
> **Comhra said:**
> I'm running the Xfce desktop environment and I want to continue doing so in tandem with Gnome.

I've encountered a few things that puzzle me such as where is Volume control?

It's not in Add items to panal which is where I'd expect it to be.  So how do I manage Vol. Control in Xfce?

Are you sure it's not there?  It is in mine, but maybe it's not the default in Gutsy.  Check if the xfce4-mixer package is installed.

(Note there is a [bug ]("https://bugs.launchpad.net/xfce4-mixer/+bug/90261")that might mean you can't load the mixer plugin.  If you have problems, try dragging it from the "Add Item to Panel" menu to the panel.)

> 
There doesn't seem to be a default dictionary nor a screen capture facility.  I suppose these are part of the Gnome desktop package and they're absence is explained by the fact that I'm using a different desktop manager...right?

Yep.  Exactly.  That doesn't mean you can't use them in Xfce though.  If they're regular apps, they should be in the application menu; if not, keep reading.

> 
Are there alternative dictionary and screen capture packages that I can use when working in Xfce and if so how would I install them using terminal?

I'm not sure what you mean by a dictionary program--I usually just search online for how to spell words and use aspell for spell-checking textfiles--but there is an xfce4-dict-plugin package that might work.  Also, there is an xfce4-screenshooter-plugin which should handle screenshots.

If neither of those work, there's a plugin that will let you run Gnome applets in the Xfce panel.  Install thexfce4-xfapplet-plugin.  (For more info, see [this blog post]("http://bapoumba.wordpress.com/2008/01/04/add-gnome-applets-to-the-xfce-panel/").)

---

### Post by psychicdragon on 2008-01-20
Is it possible that you don't have the xfce4-mixer package installed?

---

### Post by rosegarden78 on 2008-01-20
The author above sounds correct to me.  I am using a setup similar to yours.  First, I installed Ubuntu Gutsy.  Then I added kde from Synaptic.  Then I added xfce from Synaptic.  So I always have all the dependencies.  You will see XFCE Menu - Settings - Sessions and Startup there is designed for GNOME and KDE in tandem.

You may even try Press Alt+F2 then type "nautilus" and you have best of both worlds.  Make sure you have Xfce Menu added to your launcher.  Nautilus replaces the right click with the familiar file creation menu.

And yes I don't have my Fn keys' volume control activated either.  But I bet if you get the code from Keyboard Shortcuts in Ubuntu it will work.  I think the codes start with zero+x and look much different than their counterparts.  But if you'll notice XFCE has a slightly different approach.  You need to train it as you would like it.

In Xubuntu you need to add a folder or group called "Custom Whatever" before you can add items to your Keyboard Shortcuts.  Mine says aumix.. is the volume program that cannot be executed.  Hence the keys are not working for me either.  Now I will try adding kdesu to the commands ... no luck ... but when I entered Synaptic or Add/Remove Programs a search for aumix revealed it is missing.  I checked the box and am awaiting results ...

OK ... aumix is installed but the Fn + PgUp keys are not recognized and not launching aumix ...

Aha!  Just like my previous post!  A command must be executed with a shell script so here's what you do:

# Before you begin type sudo aptitude install aumix
# Or check the repos in Synaptic to make sure
# Or else this aumix experiment will certainly fail

1) Navigate to /home folder and create new folder "startup"
2) Navigate to /home/startup and create a blank file, or use text editor, and name it "aumix-up"
3) Obtain the source code for the "Up Command"
a) In Xfce Menu - Settings - Keyboard Settings
b) You should have a set of commands and key combos.
c) Edit the command for volume up (aumix...?) by double-clicking it
d) Press Ctrl+a and then Ctrl+c to copy this command
4) Paste this command into your text editor or aumix-up file (the blank one you just opened)
5) Add the path to your shell interpretor !#/bin/sh

#!/bin/sh
# aumix-up shell script
aumix -v+10

6) Save the file and name it aumix-up
7)  Repeat process to make aumix-dn script

#!/bin/sh
# aumix-up shell script
aumix -v-10

8)  Repeat the process to make a aumix-mute script
#!/bin/sh
# aumix-up shell script
aumix -v0


9) Right click Properties - Permission to make these three scripts executable
a) Or type chmod +x /home/startup/aumix-up
b) Then type chmod +x /home/startup/aumix-dn
c) Then type chmod +x /home/startup/aumix-mute
d) In a terminal of course

10) Now add shell scripts to keyboard shortcuts
a) Add new item to Custom group
b) When prompted for command type: bash /home/startup/aumix-up
c) When asked for a key combo press CtrlKey + VolumeUp
d) Now repeat the process for volume down use CtrlKey + VolumeDn
e) For the mute button repeat process use CtrlKey + Mute

That'll do it let me test my hypothesis if it fails I'll get back to you.

Well my friend the experiment failed.

I'm going to try the previous suggestion and get back to you.

Well the dragon was correct about the mixer.  But I still would like to activate the keys so I'm purging aumix and replacing with the the aumix-gtk package.  I'll see if the newer package activates aumix keys and get back to you ..

Well ... an exhaustive experiment proved psychicdragon correct.  I needed to install the xfce4-mixer package but also installed aumix-gtk just to be on the safe side.  Then I reverted the keyboard shortcuts back to default - good thing I made custom commands.  Funny thing is - the function key volume controls work regardless of the keyboard shortcuts.  A word from the wise was sufficient after all ...

---

### Post by samwyse on 2008-01-20
Human theme crashes the volume control.

---

### Post by rosegarden78 on 2008-01-20
Human theme!?  Sorry to hear that.  What about Plastik?

---

### Post by Comhra on 2008-01-20
The mixer was not installed.  Thanks folks.

---

### Post by cardinals_fan on 2008-01-20
> **Comhra said:**
> 
Are there alternative dictionary and screen capture packages that I can use when working in Xfce and if so how would I install them using terminal?

I highly recommend scrot (for screen capture).  Just run ```
sudo aptitude install scrot
``` It is a command-line utility - run "scrot --help" after install to see the options.  Have fun with Xfce!

---

### Post by videodrome on 2008-01-22
I would suggest that you always use the installer and not synaptic when installing xfce. Using the installers have been the only error-free way that I have found to install and or upgrade xfce.

---

### Post by jis on 2008-03-02
> **afoglia said:**
> 
(Note there is a [bug ]("https://bugs.launchpad.net/xfce4-mixer/+bug/90261")that might mean you can't load the mixer plugin.  If you have problems, try dragging it from the "Add Item to Panel" menu to the panel.)


Even if I drag the volume control to panel it won't be present after reboot. I am usein GNOME applets now.

---

### Post by jis on 2008-03-02
> **Comhra said:**
> 
Are there alternative dictionary and screen capture packages that I can use when working in Xfce and if so how would I install them using terminal?

Xfce4 has Screenshot panel item, but it takes 4.3 MB RAM when added.

---

