---
title: "???  Why Is Firefox Doing This?  PIC"
date: 2009-01-26
forum: General Help
---

### Post by sjl127 on 2009-01-26
When I open up a new session, firefox screen dominates everything...

How can I possible fix this?  Here's a screen shot.

[IMG][IMG]http://farm4.static.flickr.com/3471/3230792556_90c1d409ca.jpg[/IMG][/IMG]

---

### Post by sjl127 on 2009-01-26
Played around, noticed that visual settings changed (I didn't do it), had set at minimal, set at the middle option, changed back and all's ok, also, lower right hand corner, originally had set 4 workspaces, 2 row, 2 column, was changed to 1 row.  Just changed back =- wonder what happened?

---

### Post by mb_webguy on 2009-01-27
That looks like kiosk or fullscreen mode, which is toggled with F11.

---

### Post by Crafty Kisses on 2009-01-27
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

---

