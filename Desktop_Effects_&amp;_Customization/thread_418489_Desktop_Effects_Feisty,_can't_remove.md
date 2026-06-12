---
title: "Desktop Effects Feisty, can't remove"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by Neuralgia on 2007-04-22
I upgraded from Edgy. I already had installed Beryl and evrythig was ok.

Now I tried to use the "default" Desktop Effects on Feisty, and at first I couldn't, I got a mssgs that said

> The composite Extension is noy available

then, after some upgradingI got to enter the Desktop Effects. They asked if they were OK, but I didn't realize I didn't have the bar on top of the window.

Now, for some reason I can't undo this, because when I go to the Desktop Effects options, I get the same mssg I got on the beggining.

When I try to use the Shoe Desktop button I get this:

> Your window manager does not support the show desktop button, or you are not running a window manager.

How can I go back?

or how do I fix this.

Thanks

---

### Post by djrobthaman on 2007-04-22
Hi,

Quick question.  I'm having your initial problem where it says composite not available.  To get around that did you manually edit the xorg.conf file or did is there some user friendly thing to do that i just can't find?


Thanks

---

### Post by Flare183 on 2007-04-22
You enabled compiz when you click on enable Desktop Effects. Compiz and Beryl conflict so that is what done it. Even through Beryl is a fork off of Compiz. Press alt and then the window to move the windows. If that helps.

---

### Post by FuturePilot on 2007-04-22
Add this to the very end of your xorg.conf file
First ```
gksudo gedit /etc/X11/xorg.conf
```
Go all the way to the end and add this```
Section "Extensions"
Composite "Enable"
EndSection
```
If you already have that, make sure it says "Enable" and not "Disable"
Then log out and restart X with <Ctrl><Alt><Backspace>

---

### Post by djrobthaman on 2007-04-22
Arrghh... figured I'd have to do it that way, but what's the point of making it this easy to install fglrx (I wonder is it fglrx or the newer driver that ati just released?) with the restricted manager thing and have a button in the menu for desktop effects if you still have to edit the xorg.  That's not cool at all.

Thanks for the info.  And i guess ignore the vented frustration above.

---

### Post by djrobthaman on 2007-04-22
Darn it.  Beryl still won't work.  I downloaded all the beryl files and xserver-xgl using synaptic, but no luck.  I try to log in to an xgl session but there isn't one. 

Do you know how I can get this working w ith xgl?  Had it on edgy.

---

### Post by FuturePilot on 2007-04-22
Here's a good guide to get Beryl and XGL working on Feisty.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by Neuralgia on 2007-04-22
Ok, let me go slow, and explain again.

1. I used to have Edgy, and Upgraded to Feisty.

2. On Edgy I had Beryl working 100%

3. Immediately after upgrading, I decided to test the DEFAULT "Desktop Effects" that I knew Feisty had.

At first, I recieved the "Composite Extension not available messg"

After upgrading everything, I could see the "Desktop Effect" options and applied them .

4. Everything was ok, my windows were wobbling, and I had 3d desktop

5. After I rebooted I lost 4 things
     a) My menu bar, where the maximize, minimize and close button were
     b) I lost the workspace choose
     c) When I press the Show Desktop button i get the "Your window manager does not support the show desktop button, or you are not running a window manager." messg.
     d) I lost the "window list" on my bar.

I know I can install beryl, because I had it in Edgy, so that is not the question.
The question is

**How do I disable the default Desktop Effects on Feisty?**

when I go to System>Preferences>Desktop Effects I get this messg.

"The Composite Extension is not available"

Please, its frustrating not being able to move your windows, close, minimizo or maximize your apps... and worse of all is that once I open any apps, it gets on top of my main bar, so I can't open anything else. :confused:
ees
=-=-=-=-=-=-=-=-=

I was thinking about installing beryl, BUT, first I want to fix this, since sometimes I get tired of all the eye candy and like a "clean desktop". I guess that if I just install beryl, I'll never be able to fix this issue.

(PS> I got tired and tried to install beryl thinking this might help, but I got an "unment dependency: beryl-manager: depends> beryl but it is not going to be installed   E: broken packages)

---

### Post by Neuralgia on 2007-04-22
Update:


when I log into Gnome Failsafe Session, everything is back to normal

Why can I activate the Desktop Effects, but can't remove them?

---

### Post by FuturePilot on 2007-04-22
Ok to get the window manager back for now, in a terminal just do ```
metacity --replace
```
Now did you have XGL installed on Edgy?

---

### Post by Neuralgia on 2007-04-22
THANKS... that was exactly what I needed

And YES, I had XGL on Edgy working with Beryl with no problems at all.

(in fact, the only problem was that I didn't have the Power Off buttons and Restart... which was a bot annoying... but it seems that they fixed that)

(i tried to fix this, but never worked correctly,sometimes i had the buttons, but my icons sucked)

---

