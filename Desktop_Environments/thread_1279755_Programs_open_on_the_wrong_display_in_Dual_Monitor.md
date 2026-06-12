---
title: "Programs open on the wrong display in Dual Monitor Mode (ATI)"
date: 2009-10-01
forum: Desktop Environments
---

### Post by jbfloyd on 2009-10-01
I connected a 2nd display to my computer with the idea that I could use it to watch TV using MythTV while using my first display for work.  This works great when the displays are in single display mode where each has it own desktop.

However, sometimes I would like to be able to use the 2nd monitor for other programs to take advantage of the excess visual space to display more information.  The problem is that for most programs, despite being launched in the menu bar of display 2, they launch in display 1.  There is a short list of programs that will open in display 2 when launched from display 2.  They are:

Firefox
OpenOffice.org
Google Earth and Picasa
MythTV
wicd network manager
ATI Catalyst Control Center
Emacs

Everything else launches to display 1, as far as I can tell.

This is Ubuntu 9.04 using ATI proprietary drivers on a Raedon HD 4870 card.  Display 1 is a 22" LCD running 1680 x 1050 while the second display is an old CRT at 1024x768.

Can anyone tell me what's special about the programs that will launch in display 2?  Does anyone know how to make other programs launch in display 2?  I'm aware that 2 instances of the same program can't be on separate desktops displays or moved between the two in single monitor mode - I'm thinking that has something to do with it - but I don't know what.  (I can't used the mode where it treats both monitors as one display because then it causes complications with how myth is displayed).  Even if I could just open a terminal window in display 2, that would be great.

---

### Post by arpheztwig on 2009-10-01
Also looking for a solution to this. although I'm using nvidia...

it took hours just to get the second monitor working and rotated correctly (inverted), just to find out that the support for multiple monitors is awful... not being able to drag windows between them, not being able to have firefox open in both, and not being able to open most programs, including a terminal, at all on the second monitor make it all but useless to even have it.

does kde have any better support than gnome?  been a long time since I played with beryl and stuff, but do any of these have anything better to offer?

thanks for any advice


eVGA 8800GT, one monitor dvi (which, by the way is also not regognized as DVI) second vga (dvi-vga adaptor), inverted

---

### Post by Digital Magi on 2009-10-02
Found the answer in another thread, but can't find the bookmark right now. Here is the answer that worked for me - nVidia drivers using separate X displays.

Since drag&drop doesn't work when set up as separate X displays, you have to use customized launchers on the second display which define which window you want the app to open in.

Mouse over to the secondary display and create a desktop or panel launcher for your app. In the "command" section type in the app name and add " --screen 1 &" to the name.

example:
```
gnome-terminal --screen 1 &
```

Using the example above you can use the terminal you just opened on the second display to open programs on that display.

Also, any new launchers you create in the panel on the second display will default to the new display, so delete whatever launchers were copied from the first display and make new ones. X seems to know which display they are on and treats them separately, but initially just copies the ones from your primary when you first set up the secondary display, hence the odd behavior of clicking in one and opening in the other. Delete and replace them to get them tied to the new monitor.

It's not perfect, but it does work. It still doesn't let you run two instances of certain apps (like dual firefox) without some work but for things like watching video on one while working on the other it's perfect.

Hope that helps!

---

### Post by kireol on 2009-10-02
sudo apt-get install devilspie

then google how to set it up.


devilspie allows you to specify what workspace, screen, etc.

---

### Post by arpheztwig on 2009-10-06
thanks a ton, guys!
the launcher command will do for now, as I only want a couple programs open on the second monitor (rythmbox, pidgeon, maybe a terminal)

although, pidgeon won't launch at all with the --screen command, but opening it from a terminal on the second monitor works.  I'll look into that app and see if I can make it a little more automated.

rock on

**Use Nickels.  Nickels is money too guys.**

---

