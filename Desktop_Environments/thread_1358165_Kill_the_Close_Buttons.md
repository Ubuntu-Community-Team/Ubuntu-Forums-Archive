---
title: "Kill the Close Buttons"
date: 2009-12-18
forum: Desktop Environments
---

### Post by HyperHacker on 2009-12-18
Is there a global GTK setting to get rid of "close" buttons, e.g. on the tabs of Xfce4-terminal, the tab bar of XChat, etc? All they do is get clicked by accident. If I want to close a tab I'll right-click it and choose Close in the menu. >.>

---

### Post by hariks0 on 2009-12-18
I think there is an entry in gconf-editor that determines the position of the buttons. Is it not possible to use the same entry values to get rid of the Close button?

Please try and post back the result.

---

### Post by HyperHacker on 2009-12-18
Do you have any idea what that setting is called or where to find it?

---

### Post by hariks0 on 2009-12-18
Found it.

Bring up gconf-editor.
Go to Apps/metacity/general
The "button_layout" will be:
menu:minimize,maximize_,close_

Delete the _,Close_ The effect is instantaneous.

[I have not checked it yet. Change of the button order works]

---

### Post by HyperHacker on 2009-12-18
That would be for the window title bars. I'm talking about the big X buttons on tabs:
[img]http://img15.imageshack.us/img15/5822/closebutton.png[/img]
Some programs have them on every tab, others just one on the tab bar, but they get in the way regardless.

---

### Post by hariks0 on 2009-12-18
Try this for firefox

[http://www.howtogeek.com/howto/internet/firefox/quick-tip-remove-close-button-from-firefox-tabs/](http://www.howtogeek.com/howto/internet/firefox/quick-tip-remove-close-button-from-firefox-tabs/)

---

### Post by HyperHacker on 2009-12-18
Is there no way to remove them from all programs?

---

