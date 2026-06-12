---
title: "cannot move panel items"
date: 2010-06-11
forum: Desktop Environments
---

### Post by andreworg on 2010-06-11
I just installed xubuntu 10.04 and realized i cannot move xfce4-panel items.
I can add or remove items just fine, but just can't move them out of their original position.

How annoying.

Same problem with two (2) different installations on different hardware.

Fiddled with $HOME/.config/xfce4/panel/* to no avail. Nothing strange seems to be there AFAICS.

Same problem on two X drivers (fglrx and tightvncserver).

I just realized I also can't drag-and-drop contacts in Pidgin, so maybe this is a drag-and-drop issue?
But I don't think so, panel items cannot be moved even when the action is initiated by right-clicking on them and choosing "Move".

Running latest xfce4-panel (4.6.3-1ubuntu2 at this time).

---

### Post by XubuRoxMySox on 2010-06-11
That's a new one I hadn't heard before. Forgive me if this sounds too "dumbed down" then, but it's the only way I know...

Right click on the item in the panel you want to move, select Move (by left-clicking on it), then **place the cursor over the spot where you want the item to appear and left click.**

There may be a "command line" way to do it, but I don't know about it. Perhaps you've already done the steps above, but you didn't say precisely what you did... 

Hoping this helps,
Robin

---

### Post by azertyh on 2010-06-12
hi,
right-click on the icon, select "move", put the icon where i want works for me too.

---

### Post by Anonymous Rain on 2010-06-13
Thanks [dixiedancer]("http://ubuntuforums.org/member.php?u=809532"), I had this problem and your solution really helped!

---

### Post by andreworg on 2010-06-14
> **dixiedancer said:**
> 
Right click on the item in the panel you want to move, select Move (by left-clicking on it), then **place the cursor over the spot where you want the item to appear and left click.**


Robin,
that's what I'm used doing myself (I'm a long time xfce user) and that's exactly what is not working.

Moreover, if I recall correctly, when moving is allowed xfce4-panel very conveniently previews the new placement as you move the cursor over the new location. Obviously this is not happening for me. Actually, after choosing "move", all of the panels become "greyed out" (as in "you  cannot drop anything here"). If you insist on left-clicking the grabbing hand cursor on a spot (and I've tried), an icon flies from the cursor back to the original position (as in "you dropped something where it does not belong").

---

### Post by andreworg on 2010-06-14
UPDATE:

Drag-and-Drop is not working also in Thunar, so this may be a xfce4 issue (not only xfce4-panel).

---

### Post by XubuRoxMySox on 2010-06-14
Yikes!

That's kinda weird. Certain desktop environments are buggy for me and others aren't. I played around with [LXDE]("http://lxde.org") for a couple of months before giving up on it, but I really *wanted* it to work because it's super lightweight and simple and has a "Windowsy" familiarity that made it ideal sharing with other kids. Yet others described the simplest solutions that worked for *them*, but never for me, even on a fresh install of both the OS *and* the DE. So I guess mine was a hardware issue, although I suspect it's more common than folks know because, well, look how long it is taking for Lubuntu to get out of Alpha testing...

I'm curious if you're using Xubuntu or just have Xfce on top of some other distro. I find Xfce quite different from one distro to another. In [Crunchbang]("http://crunchbanglinux.org") it's invisible until you right-click. In Debian it's pale, blue, bland and boring, a plain white canvas for the user to paint any way s/he likes. And it seems to work a bit differently depending on the window manager (are you using Xfwm? Is compositing enabled?), the hardware, and alot of GTK stuff.

Hoping to still help if we can,
Robin

---

### Post by andreworg on 2010-06-14
> **dixiedancer said:**
> 
I'm curious if you're using Xubuntu or just have Xfce on top of some other distro.

Robin,
many thanks for your interest.

It's kind of weird. I've had the same problem on a couple of different installations.
The first one is from xubuntu 10.04 i386 on a notebook computer. The second one is a VM installed from ubuntu server 10.04 64 bit, I can't remember if I installed xubuntu-desktop or just a few selected xfce packages (can't check now, I deleted the VM). On the notebook I am experiencing the issue with both the fglrx driver and xtightvncserver. Compositing is off.

I have put xubuntu 10.04 on a pen drive (via pendrivelinux.com), I will check what happens booting from it as soon as I can.

---

### Post by andreworg on 2010-06-28
Issue still unresolved.
the issue is NOT present on vanilla xubuntu 10.04 booted from USB stick.

---

### Post by searchfgold6789 on 2010-12-12
I have the same issue, somewhat.
[http://ubuntuforums.org/showthread.php?p=10231180](http://ubuntuforums.org/showthread.php?p=10231180)
I am very curious to see how this thread winds up being solved.

---

### Post by andreworg on 2010-12-13
_update:_

my initial analysis was wrong, the issue appears to be there **only when working on vncserver**.
I can confirm that the problem involves drag-and-drop desktop-wide; I cannot drag to relocate Firefox tabs, create Thunar shortcuts, etc.

---

### Post by damnated on 2011-01-14
I had the same problem too, until I removed the Task List applet from the panel. 
Because it had a dynamic width, I couldn't drag other applets to it's sides. Once I re-arranged everything, I added the Task List applet back, and everything stayed at it's new place. 
Hope this helps.

---

### Post by kellemes on 2011-01-15
del

---

### Post by kellemes on 2011-01-15
Arranging items is problematic indeed..
See..
[https://bugzilla.gnome.org/show_bug.cgi?id=634765]("https://bugzilla.gnome.org/show_bug.cgi?id=634765")
and..
[http://bugzilla.xfce.org/show_bug.cgi?id=6818]("http://bugzilla.xfce.org/show_bug.cgi?id=6818")

A workaround that works for me is renaming the panel conf-files in the preferred order.
On my Arch system running Xfce 4.6.2 they can be found in ~/.config/xfce4/panel
Relogin after this.

---

### Post by damnated on 2011-01-17
There has to be a " separator or spacing " item, and you can move the items only relative to this. It's very hard to explain because it is so retarded. 
Just add a "separator /spacing" item to the panel (has to be of type empty space) and play around a little. It's not rocket science, just annoying.

---

### Post by damnated on 2011-01-17
edit: sorry, server timed out.

---

### Post by kellemes on 2011-01-18
Just upgraded to Xfce 4.8.0 and all is fine.

---

### Post by glennr on 2011-03-02
xfce 4.8 did not resolve the drag and drop issue under vncserver for me.

---

### Post by zainka on 2011-07-01
Youst my 2c..

I have had the same problem on 10.10

If you try to solve the problem by editing panels.xml manually be aware that xfce4-panel must be killed before the edit and then started after the edit. Else the change will have no effect because an already running xfce4-panel session will overwrite your edits.

---

### Post by emap on 2011-07-02
this may be somewhat related, but is there a way to reorder the indicators within the indicator applet? I can move the applet around, but I have my weather, battery, sound, and mail all moving together.

---

### Post by ArcherB on 2011-10-17
Here is how I was able to move items withing the XFCE4 Panel.

Right click on panel and click "Panel Preferences"
Uncheck "Lock Panel"
Click the "Items" tab
Click on the item you want to move and then click the up/down arrows on the right side of the window.  Items should move as you want.

Good luck.

---

### Post by wah fun on 2011-10-28
Fro what its worth . . .I am sure most are aware of this command but if not then it might help. Open a terminal as root and type the command xfwm4. This resets the window manager and often clears problems with windows display such as not being able to click and drag a window, or no minimize,maximize,close buttons. It also clears problems with the panel such as right click not working properly, etc.

---

