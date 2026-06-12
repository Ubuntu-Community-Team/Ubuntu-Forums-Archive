---
title: "How do I make the gnome-shell bottom-notification-bar stop autohiding?"
date: 2012-02-17
forum: Desktop Environments
---

### Post by t.rei on 2012-02-17
Hi.

**I would like to make the notification bar at the bottom of gnome-shell stop autohiding. **

I could then make it transparent via theme to save the screen-real-estate, but would still be able to see all those who have sent me an IM and how many new message from each of those I have.

Seems like such an easy little thing to toggle, will definately have to see if I understand the extension system enough to write something like that (if no one here knows of an easier way).

Thanks for your time.

---

### Post by somewhere2go on 2012-02-17
You cane use the [Permanent notifications extension]("https://extensions.gnome.org/extension/41/permanent-notifications/").

---

### Post by t.rei on 2012-02-17
It's not quite what I'm looking for, but it is indeed better than before. Thank you.

---

### Post by t.rei on 2012-02-18
Tried it for a while. Can't use it. Too many notifications if chatting with 5+ persons.

All I'd need is an anti-autohide extension.

Anyone up to the task?

*edit*
I actually found the place to change, now I only need to find a way to make this into an extension properly.

The location is
*/usr/share/gnome-shell/js/ui/messageTray.js*
```
_showSummary...
line 2249: this._summaryBin.opacity = 255;         
line 2250: this._summaryBin.y = 0;

_hideSummary...
line 2280: { opacity: 255,
```I bet that I could somehow overwrite these functions?

---

### Post by t.rei on 2012-02-25
Ah crap - they changed that file massively...

Back to 0. :/

---

### Post by t.rei on 2012-03-06
**gnome-shell 3.3.90**


This is what I got now (I think thats all thats needed):

It basically makes the message tray behave just as if the overview was active.

messageTray.js
```
 
1432:        this._overviewVisible = [COLOR=Red]true[/COLOR];

``````
1465:                 this._overviewVisible = [COLOR=Red]true[/COLOR];

```Anyone got a hint on how to do this in an extension?

---

