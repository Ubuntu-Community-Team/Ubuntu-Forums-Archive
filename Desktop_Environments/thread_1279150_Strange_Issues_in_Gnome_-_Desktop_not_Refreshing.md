---
title: "Strange Issues in Gnome - Desktop not Refreshing?"
date: 2009-09-30
forum: Desktop Environments
---

### Post by greyfox1 on 2009-09-30
Recently I have been having a very strange issue.  After I log in (sometimes immediately, sometimes after just a few minutes), menus stop appearing.  This includes the Gnome-panel menus as well as the menus in any program I may be running or the right-click context menu in Nautilus.  When I click a menu, its color changes to indicate that it has been clicked like it normally would, but I don't see the menu.

If I am running any program such as Nautilus or Totem when the problem occurs, I can keep using it normally (as long as I don't need to access a menu or right-click anything), but the only way I have found to resolve the issue is by restarting X (after having installed [dontzap]("https://wiki.ubuntu.com/X/Config/DontZap") and re-enabling the ctrl+alt+backspace shortcut).

Also-- I use Gnome-Do's Docky interface.  I noticed that if I click an icon in Docky while this problem is going on, the icon grows like normal then nothing happens: the program does not launch and the icon doesn't shrink back to its normal size either.

So, this seems to be some weird problem with my desktop not refreshing or something.  I do not recall making any changes recently, other than installing a few updates when prompted (sorry, I don't recall which ones, but this came up about 2-3 weeks ago).

Has anyone seen this before or have any ideas?

---

### Post by greyfox1 on 2009-10-01
*Bump* anyone?

---

### Post by onyxwolf on 2009-10-02
I wonder if you could reinstall the desktop only. I know that if you install Ubuntu without a GUI (i.e. Ubuntu Server), and decide you want it, you can install it afterwards. Try :

sudo apt-get remove gnome-desktop
sudo apt-get install gnome-desktop

I also found the following commands to install it:
sudo apt-get remove x-window-system-core xserver-xorg gnome-desktop-environment
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

**Please do more research** on trying this before you do, I'm just spitting out ideas!

---

### Post by greyfox1 on 2009-10-03
Thanks, I'll look into that. Also if this helps: when I try to run a program that requires gksudo like Update Manager, it will think for a few seconds then hit me with:

"Could not grab keyboard. A malicious client may be eavesdropping on your session"

---

### Post by tolostoi on 2009-10-03
> **onyxwolf said:**
> I wonder if you could reinstall the desktop only. I know that if you install Ubuntu without a GUI (i.e. Ubuntu Server), and decide you want it, you can install it afterwards. Try :

sudo apt-get remove gnome-desktop
sudo apt-get install gnome-desktop

I also found the following commands to install it:
sudo apt-get remove x-window-system-core xserver-xorg gnome-desktop-environment
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

**Please do more research** on trying this before you do, I'm just spitting out ideas!
I think, the proper way to do this is with 
```
sudo tasksel
```then choose the option(s) anh hit enter. 

for the problem, try when it come, hit ctrl+alt+F2, login and exec
```
top
```maybe you will see the problem process  :(

---

### Post by greyfox1 on 2009-10-05
I installed a host of updates two days ago (including some kernel updates) and the issue seems to have been resolved. I'll give it another couple of days before I mark the thread solved, though.

---

### Post by greyfox1 on 2009-10-08
I'm still having the problem, although I have some more information about what seems to be going on. 

It all seems to be related to an episode I had a few months ago after I inadvertently allowed my $HOME partition to fill up. I wrote about it in all its painful glory [here]("http://rickucker.blogspot.com/2009/07/fallout.html").

Since that time everything has seemed fine, except weird issues I've been having in Banshee. I noticed after I addressed the issues caused by the full partition that whenever I launched Banshee, it would never remember my view settings (it did  before the problems I had). For example, one view pane would always be reduced to about 5% of the viewable screen instead of the 60/40 split I would always use. Every time I launch Banshee the first thing I do is resize the view panes to the way I like them, but it never remembers the preference (again, it used to remember).

The display issue I wrote about in my first post seems to have started coming up after Banshee locked up when I paused a movie I was watching. I killed the program with the Force Quit applet. I *think* that this is when the display issues started.

As I mentioned above, the problems seemed to stop when I installed some updates (including a Kernel update). Tonight I re-installed the latest kernel through Synaptic and the issue seemed to stop again.

I'm going to play around with Banshee and see if I can cause this to happen again. Is what I'm describing about Banshee and the other issues ringing any bells? Am I touching on something here? If I am able to cause this to happen by causing a Banshee lockup again, I guess I could try to back up my banshee.db then completely remove/ reinstall the program and see if it performs normally again.

---

### Post by greyfox1 on 2009-10-18
Giving this thread a bump because I'm still having problems.

After logging in (sometimes immediately, sometimes after a few minutes), I lose the following abilities:
-Right-click on anything (menu doesn't appear)
-Open a menu from the Gnome-panel or the currently running app (in the case of the panel, the "button" for Applications/Places/System appears depressed, but the menu doesn't appear)
-Move or resize an open window
-Just about anything involving the keyboard (can't type, can't grab a screenshot, although I can use ctrl+alt+backspace or ctrl+alt+F2)
-If I click on Docky, the whole dock freezes

At first, it appeared that reinstalling the latest kernel through Synaptic would take care of it, but I think that was actually a fluke. It no longer seems to help.

It really appears that the desktop is not being redrawn. If I switch to another console (ctrl+alt+F2) then try to switch back (ctrl+alt+F7) I just get a black screen with a flashing cursor. Nothing happens at that point (I can't even switch back to #2) and I have to restart X or the whole machine.

Turning desktop effects off doesn't help.

With desktop effects disabled, "top" shows that the top two processes are multiload-applet and Xorg. After that it varies. Something called "rt2870Mlmethread" sometimes shows up as #3. I think that process is related to my wireless Dongle. The total CPU usage is only about 10% at any rate.

Does anyone have any idea what I seem to be struggling against here? I'm out of ideas.

---

### Post by greyfox1 on 2009-11-25
This thread is now solved and I wanted to provide some further information. 

Regarding removing/reinstalling the desktop: ```
sudo tasksel
``` is the best way to do this. For others reading this thread, do NOT--   D O   N O T -- try to accomplish this by removing x-window-system-core xserver-xorg gnome-desktop-environment as a few users have recommended above. Due to a [bug]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/424771") in Karmic, this will break your system. Again, use sudo tasksel if you must. I found this out the hard way and ended up reinstalling. 

However, it turns out that none of this would have resolved my issue. While I was running the Live CD and preparing to reinstall everything, I noticed the ORIGINAL ISSUE AGAIN-- menus wouldn't appear, keyboard wouldn't respond, etc. That's when I realized that this was never an Ubuntu issue to begin with. It turns out that my wireless keyboard was dying >< . 

Long story short: replaced the keyboard, issue resolved. Wish I hadn't spent all those hours chasing my tail on this one, but that's the way it goes sometimes.

---

