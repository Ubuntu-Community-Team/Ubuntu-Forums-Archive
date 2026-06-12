---
title: "trick- rotate effect in ubuntu"
date: 2011-06-15
forum: Desktop Environments
---

### Post by shibu_sawyer on 2011-06-15
[COLOR=Red][B]NOTE: compizconfig manager is not suitable for ubuntu 11.04 with unity,works fine with 9.10 and 10.10.
[/B][/COLOR]
 Ubuntu enables "Desktop Wall" by default. By holding Ctrl-Alt keys  and pressing the left-arrow or right-arrow key each time, it slides  through desktop workspaces horizontally for you to choose one to work  on. Alternatively, you can change this to a "rotate cube" effect.
 
[LIST=1]
[*][[IMG]http://www.techsupportalert.com/files/images/Rotate-Cube-200-125.png[/IMG]]("http://www.techsupportalert.com/files/images/Rotate-Cube.png")Go To System > Preferences > [URL="http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#ccsm"]CompizConfig Settings Manager.
[/URL]
[*]Select "Desktop" from the left panel.
[*]Tick "Rotate Cube".
[*]Select "Enable Desktop Cube" as this plugin is required by "Rotate Cube".
[*]Select "Disable Desktop Wall".
[/LIST]
 Immediately  you can rotate your desktop workspaces in this way— holding down  Ctrl-Alt keys, EITHER press the left-arrow or right-arrow key OR  left-click the mouse and drag it to left or right.


if there is no compiz manager in your system,download it.. type :sudo apt-get install compizconfig-settings-manager ..:popcorn:

---

### Post by 3rdalbum on 2011-06-15
[COLOR="Red"]Warning: Do NOT do this on Ubuntu 11.04![/COLOR]

---

### Post by shibu_sawyer on 2011-06-15
why why not,it works fine in 9.10 and 10.10.. i myself checked.. any problem..?

---

### Post by satyanash on 2011-06-15
AFAIK, Ubuntu 11.04 Natty **_with Unity_** doesnt use Compiz as it's default compositing manager, so new users may be confused when they try to do this while using Unity which may screw up the screen, and cause some other undesirable effects.
Satyajeet

---

### Post by shibu_sawyer on 2011-06-15
oh thats a big problem..

---

### Post by satyanash on 2011-06-15
> **shibu_sawyer said:**
> oh thats a big problem..

You might want to edit your earlier post, and make people aware that this will not work in Unity.

---

### Post by apollothethird on 2011-06-15
> **sattu94 said:**
> AFAIK, Ubuntu 11.04 Natty with Unity doesnt use Compiz as it's default compositing manager, so new users may be confused when they try to do this while using Unity which may screw up the screen, and cause some other undesirable effects.
Satyajeet

I never saw this warning and have been using CCSM and the effect described by the OP for weeks.  I notice many changes does appear to break some other functionality, namely the Top and Side menus.  Through trial and error I found that logging out and logging in restores what was broken and the new effect is added in tact.

To logout I either move the mouse around where the Power button is located (but can't be seen) or run gnome-panel in a terminal window.

Other than that, I don't see a problem with CCSM.  I'm happy with the visual enhancements I have configured.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by shibu_sawyer on 2011-06-15
@sattu; okay.thanks, i will re-edit now

---

### Post by 3rdalbum on 2011-06-15
To clarify: CCSM works on 11.04 because Unity uses Compiz, but the Desktop Cube plugin disables stuff that Unity needs to work. I've also heard people saying that Gnome Classic stops working with Desktop Cube in 11.04 too, but I can't confirm that.

---

### Post by overdrank on 2011-06-15
Moved to Desktop Environments

---

### Post by cpmman on 2011-06-15
Natty with Cube (haven't managed Atlantis with motion yet but it will come)
Unity works perfectly.
Haven't sorted how to resize windows for e.g. Skype yet.

[attach]195169[/attach]

---

### Post by stinkeye on 2011-06-15
You can enable the cube on natty but you need to enable the plugins in a 
certain order because of the way the plugin dependencies work.
See this guide. Good idea to make a backup of your current settimgs in
ccsm > preferences

[**_[COLOR="DarkRed"]Enable Desktop Cube in Unity, Ubuntu Natty[/COLOR]_**]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html")

---

