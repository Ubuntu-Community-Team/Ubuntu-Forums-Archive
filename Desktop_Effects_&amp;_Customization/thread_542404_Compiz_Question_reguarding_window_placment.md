---
title: "Compiz Question reguarding window placment"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by russo.mic on 2007-09-03
So,

As an example, i've got KTorrent open on one side of my cube, and firefox open on the other.  When I download a torrent in firefox, and just tell it to "open with" ktorrent, of course ktorrent responds by creating a new window asking me where I want to put the files.  Great, except that although my cube rotates automatically to focus on KTorrent, the dialog box it's called on has been created on the cubeface that I was on, namely the one firefox is on.  So, my question is, is there a way to tell compiz to only create dialog boxes on the same cube faces as the programs that call upon them?  seems like that would be kind of an obvious feature, so I feel like it's possible that I'm missing something, but i've searched in compiz preferences to no avail.  The cloest thing I can find is a feature allowing me to assign programs to only open on fixed cube faces.

Thanks in advance!  

Russo

---

### Post by jsully1 on 2007-09-04
You've hit on the only solution that I'm aware of, which would be to tell Compiz to open specific programs or windows on specific viewports.

There's a rather comprehensive FAQ here:
[http://forum.compiz-fusion.org/showthread.php?t=1768](http://forum.compiz-fusion.org/showthread.php?t=1768)

For example in my place plugin I have 
class=Pidgin 1 
Which always opens Pidgin on workspace 2.

---

### Post by russo.mic on 2007-09-04
I thought you'd say that.  I would just like it if there was a way to tell it to only open child windows on viewports where the parent window exists. 

Maybe a compiz suggestion?  anyone else have an opinion?

---

### Post by jsully1 on 2007-09-05
Well the plugin does take regular expressions - it may be possible to craft one that accomplishes this.

---

