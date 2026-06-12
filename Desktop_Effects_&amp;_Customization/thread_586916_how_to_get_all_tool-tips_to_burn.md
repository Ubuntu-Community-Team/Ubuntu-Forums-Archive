---
title: "how to get all tool-tips to burn?"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by nacho32 on 2007-10-22
Ok I got the burn effect on and only cetain tool tips burn how do I get all mouse over burns when mouse goes over a link when that tool tip box opens?

---

### Post by nacho32 on 2007-10-23
anyone?

---

### Post by mohamad on 2007-11-02
Seems like there is no way to remove ALL tooltips in Gnome, however I found a thread somewhere for a work around if u use compiz fusion. I saved it as a text file so I'll just paste it here:


> A workaround for those of you who are using CompizFusion, which I found googling around:
open the advanced compiz settings panel (you might have to
$ apt-get install compizconfig-settings-manager
)

go to General Options > Opacity Settings

click on Add, type Tooltip into the Opacity windows textbox, and set the opacity to zero

volià: the tooltips are still there, but at least they are invisible :-)

and there u have it :)

---

### Post by mohamad on 2007-11-02
Oh never mind my previous reply, I thought you meant to burn the tooltips as in make them go away :D

---

### Post by VictorR on 2007-11-02
For many non-GTK applications their visual parts are different from what you expect. For example, tooltips can be just type=NORMAL windows instead of type=TOOLTIP for Firefox. So it's the common widows matching problem. Try something like this:
(class=Swiftfox-bin | class=Thunderbird-bin | type=normal) & override_redirect=1
in Window Match for Close Effect, change class=<your apps where expected effect does not work>

---

