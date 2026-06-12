---
title: "Very weird problem with mouse not raising focus"
date: 2009-11-06
forum: Desktop Environments
---

### Post by Jethro_uk on 2009-11-06
Right, I upgraded 8.10->9.04 last week. Was pleasantly surprised it went so smoothly, given my 7.10->8.10 upgrade was  nightmare.

Spoke too soon !

I have noticed an irritating, and bizarre problem with the mouse. The machine in question is dual-boot, and the WindowsXP works fine, so we can discount hardware issues.

Basically, I log in, and load an app ... lets say Firefox. From that point on, the mouse doesn't seem to give what is under it focus. So initially I can move around in the browser window, click hyperlinks etc etc.l However, moving the mouse to the menu does nothing. The click is ignored. If I press "Alt+F" then the menu becomes active, and the mouse works fine. However the browser window becomes inactive. I have to use the tab key to cycle through the GUI elements until one in the browser takes focus. Then the menu doesn't work again ...

Initially I thought the mouse click was being lost, but having spent a while yesterday investigating, I have managed to work out exactly what is happening.

Being a Win32 programmer, I know a bit about message maps, and how Windows deals with GUI elements, but I want to use Ubuntu, not work in it.

I tried disabling Desktop effects (which should kill compiz IIUC ?) with no joy. It does it with any of the three options,So it's not that. I know X Windows has the concept of a "window manager" which you can mix'n'match with the Window provider, but beyond that I am stumped.

Can anyone suggest what has happened, and how to fix it? To be honest is makes the system completely unusable for more than a minute.

---

### Post by kellemes on 2009-11-06
You have this with every app? Or it is just Firefox?

---

### Post by Jethro_uk on 2009-11-06
every app, I was using FF as an example. Nautilus windows, the mouse poperties window (That pops up, and I can change the tabs, but clicking "Close" does nothing. Once the window pops up I can't click the desktop or taskbars) ....

---

### Post by Jethro_uk on 2009-11-17
> **Jethro_uk said:**
> Right, I upgraded 8.10->9.04 last week. Was pleasantly surprised it went so smoothly, given my 7.10->8.10 upgrade was  nightmare.

Spoke too soon !

I have noticed an irritating, and bizarre problem with the mouse. The machine in question is dual-boot, and the WindowsXP works fine, so we can discount hardware issues.

Basically, I log in, and load an app ... lets say Firefox. From that point on, the mouse doesn't seem to give what is under it focus. So initially I can move around in the browser window, click hyperlinks etc etc.l However, moving the mouse to the menu does nothing. The click is ignored. If I press "Alt+F" then the menu becomes active, and the mouse works fine. However the browser window becomes inactive. I have to use the tab key to cycle through the GUI elements until one in the browser takes focus. Then the menu doesn't work again ...

Initially I thought the mouse click was being lost, but having spent a while yesterday investigating, I have managed to work out exactly what is happening.

Being a Win32 programmer, I know a bit about message maps, and how Windows deals with GUI elements, but I want to use Ubuntu, not work in it.

I tried disabling Desktop effects (which should kill compiz IIUC ?) with no joy. It does it with any of the three options,So it's not that. I know X Windows has the concept of a "window manager" which you can mix'n'match with the Window provider, but beyond that I am stumped.

Can anyone suggest what has happened, and how to fix it? To be honest is makes the system completely unusable for more than a minute.


Have identified this along with a few others as a definite bug [https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905]("https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905"). Sadly no fix

---

### Post by Jethro_uk on 2009-12-02
After a while playing with this problem, I have got it down to be an annoyance, rather than a showstopper.

Not being a Linux guru, my opinions are of limited value, but I firmly believe this is an X-Server/XOrg problem. I've seen it happen under GNOME and KDE, and with all combinations of window managers, and decorators.

There appears to be a connection with ALT-TAB ... as soon as the mouse focus issue happens, you lose ALT-TAB.

Anyway, I have discovered that if I activate ALT-TAB as soon as I login, it seems to "protect" my system, and I don't seem to lose mouse focus.

I have also discovered, that CTL-ALT-D (show desktop) seems to recover mouse focus ... once all windows are minimised to the taskbar, then ALT-TAB seems to work again, and mouse focus is restored. Hopefully this workaround will prove useful to people, and can remove the need to logout/login again, or to restart the machine with the loss of data that implies.

---

### Post by Jethro_uk on 2009-12-23
Having lived with this problem for a few weeks now, I believe I can have a stab at suggesting what is going on, and the intermittent nature of the bug.

I *think* that when GDM starts (after I login), some process somewhere starts up, and creates a window. I have read various reports that it's possible to create a window which does not appear in the panel area. This window then steals focus. Because it's hidden, you can't switch to it to close it. From that point on, you're stiffed.

I've read a lot about the modified behaviour of the update manager/notifier, and I would like to propose this as the app which is killing mouse focus.

I'm researching ways to kill it so it never starts ...

---

### Post by indycore on 2010-01-16
Alt-F if the window has a menu works 100% every time to return to normal window focus. And Ctrl-Alt-D twice works 100% every time.

But only a few seconds.. then the focus is "stuck" or "lost" again..

Anyone found the defective component? What do i need to downgrade / uninstall

/Jan

---

### Post by lulaz on 2010-01-24
Has anybody found a fix for this problem ?

---

### Post by johansson on 2011-01-04
lulaz and anyone else looking: I had this issue and resolved it by switching my mouse.  Old mouse still works in windows, but not in linxu.  

Longer post here: [http://ubuntuforums.org/showpost.php?p=10313490&postcount=22](http://ubuntuforums.org/showpost.php?p=10313490&postcount=22)

---

### Post by robobart on 2011-02-27
Totally having the same problem. But my issue is with my laptop's trackpad--more difficult to simply swap out. A software fix would be nice.

---

### Post by smogol on 2012-02-25
Hello there,
I bought a new hardware and I get the same behavior. Everything worked 100% on my old AMD K6.
After I change to my new HW (I7), I had the same behavior.
I thought it was because I used another distribution ( I tried Mint 12), but no.
To get the session to work correctly, I need to close the very first session after the boot. Afterward, the system work like a charm.

---

### Post by mateolan on 2012-05-08
I believe that I have the exact same issue. Actually, I lose left mouse (or trackpad) click--the problem I noticed seems to especially happen when I bounce in and out of my M$oft QEMU session...
 
Were anyone's problems related to VMs?
 
Has anyone filed a ticket?
 
And someone please enlighten, what's happening under the hood with ctrl-alt-D? 
--I am so grateful for this tip.

---

