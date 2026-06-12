---
title: "How to customize arc theme"
date: 2015-11-01
forum: Desktop Environments
---

### Post by RadFel on 2015-11-01
Hi guys,
I installed the arc theme recently and I have few questions:
1. Can the left menu bar in nautilus be transparent like on the screenshots advertising this theme? This question was asked in some thread on a forum and the answer is, unfortunately, no.
2. When you open i.e. firefox in maximized mode, the [close, minimize, maximize] buttons appear on the top left on the top panel. When you detach the window from the top panel, these icons show up on the top of the window. This is how it's supposed to work. However, when it comes to nautilus, these icons are visible all the time on the top of the window, so when you maximize nautilus, there are 2 sets of these icons: one on the top bar, one on the top of the window. How can I make nautlius behave the same way firefox does on arc theme?
3. When you open a window in a normal mode (not maximized), you can see that the top panel of the window is few pixels shorter than its bottom on both right and left (narrow_top_panel.png). How to fix it? Is there a setting for this i.e. in gconf editor?
4. Can I change the color of the left menu bar's background in nautilus in this theme? Currently it's dark, whereas the icons there have pale background and all this combined makes the whole thing look ugly.

Regards,
Radek

---

### Post by brian-mccumber on 2015-11-01
1. You can adjust the launcher's transparency if you install Unity Tweak Tool from your software center.

2. You can toggle Firefox's fullscreen mode using the F11 key. 

3. That is because of the scroll bar view which you can also tweak with Unity Tweak Tool.

4. You can also change the launcher's color using the tweak tool.

Edit: I just noticed your distro is outdated, these  instructions are assuming that you can run Unity Tweak Tool and that it's in your repository for your version.

I like customizing my desktop too.
[ATTACH=CONFIG]265316[/ATTACH]


Here is a good link for lot's of themes and icons for some Linux desktop environments if you haven't found it yet.

[http://www.noobslab.com/](http://www.noobslab.com/)

---

### Post by RadFel on 2015-11-01
> **brian-mccumber said:**
> 
1. You can adjust the launcher's transparency if you install Unity Tweak Tool from your software center.


I don't see such option in this tool. Where is it?

> **brian-mccumber said:**
> 
2. You can toggle Firefox's fullscreen mode using the F11 key. 


I didn't ask about that. I want nautilus to stop displaying [close, max, min] icons on the top left of its window in the full screen mode, as these icons are on the top panel of Unity at that time. Also I'd like nautilus to display these 3 icons in a normal window mode (not maximized) just like other applications (terminal, firefox, evolution, etc.) do, which means having a top panel of a window, instead of displaying all icons on the top menu like nautilus does (shown on the screenshot).

> **brian-mccumber said:**
> 
3. That is because of the scroll bar view which you can also tweak with Unity Tweak Tool.


Honestly, I tried using options related to scroll bar and nothing changed the size of it, not to mention that the left side of a window (where there is no scrollbar) won't be affected at all by these changes, I suppose, whereas I need it to be, as it's also few pixels wider than the top panel of a window.

> **brian-mccumber said:**
> 
4. You can also change the launcher's color using the tweak tool.


I asked about a possibility to change the background of a leftside menu in nautlius, not a leftside launcher in Unity. I showed it on the screenshot with nautilus window, where you can see how the dark background looks ugly surrounded by pale elements of the window.

> **brian-mccumber said:**
> 
Edit: I just noticed your distro is outdated, these  instructions are assuming that you can run Unity Tweak Tool and that it's in your repository for your version.

Since I'm using Ubuntu 15.10, I'm pretty surprised by this summary ;) Can you elaborate?

Regards,
Radek

> **brian-mccumber said:**
> I like customizing my desktop too.
[ATTACH=CONFIG]265316[/ATTACH]


Here is a good link for lot's of themes and icons for some Linux desktop environments if you haven't found it yet.

[http://www.noobslab.com/](http://www.noobslab.com/)
I like the website, although I've done most of these stuff already as I've been using Ubuntu for few years now. I just wanted to check out this arc theme, which looks nice on the promo screenshots and I came across few issues, that's all.

By the way: even though I set up in CompizConfig Settings Manager that the launcher icons should blink when I press them and a program is starting, nothing happens. When I press i.e. Firefox icon, nothing happens until it's open, whereas its icon should blink. Any ideas?

---

### Post by Frogs Hair on 2015-11-01
If the Unity Tweak Tool is not visible in the software center you may have to enable the Canonical Partners repository  in software & updates under the other software tab. You may see a request to refresh after doing this.

---

### Post by RadFel on 2015-11-01
> **Frogs Hair said:**
> If the Unity Tweak Tool is not visible in the software center you may have to enable the Canonical Partners repository  in software & updates under the other software tab. You may see a request to refresh after doing this.
I have Unity Tweak Tool & CompizSystem Settings Manager installed and I'm using these programs. The case is that none of them seems to provide fixes/enhancements I need. Can any of you find a way to customize what I described?

---

### Post by Frogs Hair on 2015-11-01
Launcher transparency is in the launcher tab in Unity Tweak. What theme is being used in the screen shot ?

---

### Post by RadFel on 2015-11-02
> **Frogs Hair said:**
> Launcher transparency is in the launcher tab in Unity Tweak. What theme is being used in the screen shot ?
I didn't ask about launcher's transparency. I know, how to do that. I just wrote there is no possibility to add transparency to nautlius in arc theme, that's all.

I'll wait few more days and close the task as unsolved. Not each issue has to have a fix for it, although it would be nice, of course.

---

### Post by Frogs Hair on 2015-11-02
OK got it ! :) I just installed the theme and will get back to you.

Edit: The theme doesn&#8217;t display transparency in 15.10 on my computer. There are two opacity settings in the CCSM you could experiment with though. I don't know if the theme was made for Gnome 3.14(15.04) or 3.16 (15.10)and if it is for 3.14 that might affect how it looks.

---

### Post by RadFel on 2015-11-03
> **Frogs Hair said:**
> 
Edit: The theme doesn’t display transparency in 15.10 on my computer. There are two opacity settings in the CCSM you could experiment with though. I don't know if the theme was made for Gnome 3.14(15.04) or 3.16 (15.10)and if it is for 3.14 that might affect how it looks.
Thanks for trying, man, I appreciate that, but I think I should give up. Either something went wrong during the upgrade process (I used do-release-upgrade to upgrade from 14.04 to 15.04 and then to 15.10), or these flaws are just there in arc on 15.10.

I close the subject.

---

