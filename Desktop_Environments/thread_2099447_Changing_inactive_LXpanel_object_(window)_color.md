---
title: "Changing inactive LXpanel object (window) color"
date: 2012-12-29
forum: Desktop Environments
---

### Post by Dencrypt on 2012-12-29
Running Lubuntu 12.10. LXpanel 0.5.11 and LXAppearance 0.5.2.

My LXpanel looks like this:
[IMG]http://i.imgur.com/QNqX8.png[/IMG]

As you can see the Opera window is selected and the LXterm is deselected. Black font color for LXterm. This is what I want to change as to make it visible when I make the LXpanel transparent and have a black background. 
From what I gathered I should be able to change color in LXappearance -> Color tab. That's a no go. It looks like this:
[IMG]http://i.imgur.com/hatsr.png[/IMG]

I have tried changing all black colors to something else and also the background for selected items but none of these seems to affect the one I want.

Am I missing something here, is it configurable somewhere else or what is going on?

---

### Post by Andy45 on 2012-12-30
A workaround is to change your "tintcolor" in your ~/.config/lxpanel/config to "FFFFFF" for white. More info is at the wiki: [http://wiki.lxde.org/en/LXPanel]("http://wiki.lxde.org/en/LXPanel").

---

### Post by Dencrypt on 2012-12-31
Didn't make any change that I could see. Thanks anyway.

My own workaround now is to check "Flat Buttons" in the Task Bar Settings. Then They all turn white, both inactive and active windows. Better than nothing.

---

