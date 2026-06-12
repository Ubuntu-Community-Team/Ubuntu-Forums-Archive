---
title: "Flash Games - keyboard interaction broke."
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by pcatiprodotnet on 2005-12-14
Flash games on the web rarely work with my Keyboard at first.  I usually have to right-click the screen then normal-click it again to get my Arrow Keys to work.  Also, moving the mouse off the Flash browser app and back over it again works.  Are there any permanent fixes?  Thanks.

---

### Post by Qrk on 2005-12-14
I had the same problem. It seemed that the mouse curser must be in the flash applet to get it to respond.

---

### Post by Bazon on 2006-05-22
[QUOTE=Qrk]I had the same problem. It seemed that the mouse curser must be in the flash applet to get it to respond.[/QUOTE]
Ah, that tip helped for some games :) - but not all!

E.g.[ this game](http://www.gamesquid.com/?/games/-/NEWS/article/13) doesn't respond to my keyboard at all!

Am I the only one for who that game doesn't work?

Solutions? :(

---

### Post by Klaidas on 2006-05-22
[QUOTE=Qrk]I had the same problem. It seemed that the mouse curser must be in the flash applet to get it to respond.[/QUOTE]

Same here. If I move the cursor out, keybord stops responding ](*,)

---

### Post by Bazon on 2006-05-22
[QUOTE=Bazon]Ah, that tip helped for some games :) - but not all!

E.g.[ this game](http://www.gamesquid.com/?/games/-/NEWS/article/13) doesn't respond to my keyboard at all! :([/QUOTE]
It didn't worked in Dapper before.
I tried in Breezy, and there it worked!

So I downloaded the Breezy flashplugin-nonfree.deb, installed it on Dapper (after uninstalling the newer one of course...) and: It worked! :)

But additionally the packages ruby1.8, ruby, libruby1.8 and libruby were installed (as the breezy flash depended on them.)

So was it the aim of them?

To test that, I updated to the new flashplugin-nonfree version again.

Game still worked.

So were it the ruby packages? I uninstalled them and - the game still works!

So regarding the packages, I'm now here where I started, but the game works now. 
Strange....

---

### Post by Perfect Storm on 2006-05-22
I think you should bug report it.

Edit: By the way, have you tried the flash from adobe.com to see if it works?

---

### Post by Bazon on 2006-05-22
@A.I.:
I do as soon as anyone can confirm this.
(Maybe it was only some strange fault with my dapper...)

Edit:
No, I only tried flashplugin-nonfree from the repos (which connects/dl to/from macromedia anyway...)

---

### Post by Tweek84 on 2006-06-06
I can confirm this one, happened to me in breezy and dapper. Firefox with the plugin intalled automatically by the browser.

It seems to be pretty hit and miss for me.

---

