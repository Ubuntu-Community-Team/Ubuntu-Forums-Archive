---
title: "How to solve this? (Window decorations)"
date: 2010-06-30
forum: Desktop Environments
---

### Post by ©TriMoon® on 2010-06-30
Anyone have any idea how i can solve the problem shown in image?
[IMG]http://ubuntuone.com/p/8ML/[/IMG]

The same problem is also visible in "Radiance" theme, which uses the same buttons.

This started to show when i upgraded from 9.04 i think to 10.4 LTS.
I meant to post about it right away but forgot about it because i changed to "New Wave" to have at least left-to-right window decoration, but i love those buttons better...

---

### Post by _Mark_ on 2010-06-30
If you are talking about the buttons on the left is not a problem, is by design

They can be moved, the simplest way is with Ubuntu Tweak > Desktop > Window Manager Settings

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by ©TriMoon® on 2010-06-30
Well i doubt it is by design, because the preview shows differently.
Plus the left most icon (system menu) is missing from the windows when you select a theme with these buttons.

The problem is not there when you use other themes with different buttons...
So i think there is some bug here, i just saw it in another thread from someone asking another problem who showed a video...

---

### Post by Jakiejake on 2010-06-30
Same Here
[IMG]http://img810.imageshack.us/img810/4710/screenshotappearancepre.png[/IMG]

---

### Post by Jakiejake on 2010-06-30
To fix it run this in terminal to fix them!
> gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

---

### Post by _Mark_ on 2010-06-30
It is by design read this extract from the first post in this thread [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
> Minimize, Maximize and Close button placement.
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
[Update ]http://www.markshuttleworth.com/archives/333

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders. Unfortunately, if the wrong approach spreads, they won't be able to do that.

Not sure about the system menu button, but that can be accessed by right clicking in the title bar

---

### Post by Jakiejake on 2010-06-30
> **_Mark_ said:**
> It is by design read this extract from the first post in this thread [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)


Not sure about the system menu button, but that can be accessed by right clicking in the title bar

I just found what I posted from a blog I found on a Google search!

---

### Post by ©TriMoon® on 2010-06-30
Mark i somehow can't find that quote you posted on that page...
But nevertheless ill try your suggestion to create a custom theme from the default ones.
I still believe there is some bug somewhere...

*edit*
Thanks to the link jakiejake gave, i now found the source of your text mark :D
[Known Lucid Lynx issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1469475")

So it seems i was correct about the bug piece ;0

*edit2*
Duh im BLIND, you posted the link above your quote...hahaha..../me slaps self!

---

