---
title: "Help me to find the problem of desktop"
date: 2011-08-16
forum: Desktop Environments
---

### Post by elliteforce on 2011-08-16
Not able to remove one of the time shown in taskbar,it can't be editable and I'm not able to remove it from my panel,when it appeared the shutdown button was removed by itself.
No Idea how it happens, please tell me why it happened and how to change it.
Thanks in advance

---

### Post by Tamlynmac on 2011-08-16
I have a few ideas.

1. Is your panel locked down? For example, are you able to remove anything from your panel by right clicking and selecting "Remove from Panel" in the drop down menu? If not, it's probably locked down, open your gnome configuration editor located in your system tools menu "configuration editor". Go to "apps/panel/global" and uncheck the box for "locked_down" in the right top window.

2. You can add the shutdown applet by simply right clicking on an empty spot in your panel and selecting "Add To Panel" find the shutdown applet in the listing and select it, then hit the add button at the bottom of the window. Then right click on the icon and move it.

3. If your panel isn't locked down, and you can potentially remove other objects or applets. In your configuration editor go to apps/panel/general and a listing of both applets and objects should be available. This should help to define which clocks, etc. are installed in the panel. A description and configuration of each applet and object is available in the "apps/panel" directory. Listed as "apps" and "objects". By left clicking on the arrow just to the left of each of these directories you will find the listings.

I'm wondering if you recently added a docking app, a new desktop theme, icon theme or even a new app? Occasionally, new themes or apps may add/remove stuff from the panel.

Good Luck & hope this helps. If you need more help, just post again and give as much information as possible.

---

### Post by elliteforce on 2011-08-17
Thanks for replying
* I just checked none of the panel is locked and, I can remove or add anything to the panel.
* Don't knew how but whole thing return back as earlier it was after restarting.I think it's because of "Compiz".
Anyway I came to knew some good stuffs such as adding and removing items by manual procedure
Thanks again :P

---

### Post by Tamlynmac on 2011-08-17
> elliteforce
Don't knew how but whole thing return back as earlier it was after restarting.I think it's because of "Compiz".

That's interesting, it's possible you received an update that contributed or required a restart. I've seen Compiz do some strange stuff but never your problem. I've had it lock up a system due to not enough ram when opening a intensive app. But never have I seen (after setup) it add or remove anything from the panel. Thank you for sharing your feedback, I'll add it to my list... ;)

I also don't use any visual effects and turn them off in the preferences/appearance/visual effects. However, many do and if one doesn't have the ram to support it - I've seen systems do odd stuff, such as literally slow to crawl. But never add or remove panel items.  

I am glad your problem got resolved and hope you continue enjoying the experience. Sorry, I wasn't more help. Good Luck

---

