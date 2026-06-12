---
title: "arabic keyboard: missing &quot;L&quot;, others ok?"
date: 2009-03-23
forum: General Help
---

### Post by ironbishop on 2009-03-23
(This is a newbie+notNativeEnglish question, sorry - move to the right forum place if needed - okthxbai)

Well, I have this friend in which computer I installed Ubuntu. Then I installed arabic keyboard layout ([http://en.wikipedia.org/wiki/File:KB_Arabic.svg](http://en.wikipedia.org/wiki/File:KB_Arabic.svg)) and checked that box that says "... support" and applyed stickers to the (italian layout [http://en.wikipedia.org/wiki/File:KB_Italian.svg](http://en.wikipedia.org/wiki/File:KB_Italian.svg)) keyboard. _Now, the problem IS_: I can't write these: [SIZE="5"]&#65273;[/SIZE], [SIZE="5"]&#65271;[/SIZE], [SIZE="5"]&#65269;[/SIZE], [SIZE="5"]&#65275;[/SIZE].
The other letters are OK. The missing are, in italian layout: SHIFT+t, SHIFT+g, b, SHIFT+b.

How to solve?

--edit--
More informations: when I press "b" with italian keyboard layout:
> KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x65, subw 0x0, time 1616590, (509,312), root:(514,369),
    state 0x10, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

when I press "b" with arabian keyboard layout:
> KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x65, subw 0x0, time 1730223, (885,404), root:(890,461),
    state 0x2010, keycode 56 (**[COLOR="Red"]keysym 0xffffff, VoidSymbol[/COLOR]**), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
when I press (for example) "n" with arabian keyboard layout:
> KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x65, subw 0x0, time 1792050, (296,418), root:(301,475),
    state 0x2010, keycode 57 (keysym 0x5e9, Arabic_alefmaksura), same_screen YES,
    XLookupString gives 2 bytes: (d9 89) "&#1609;"
    XFilterEvent returns: False




--edit--
THANK YOU ALL FOR THE AMAZING REPLIES! The bug has already been reported:
[https://bugs.freedesktop.org/show_bug.cgi?id=8195](https://bugs.freedesktop.org/show_bug.cgi?id=8195) (CONFIRMED)
[https://bugs.freedesktop.org/show_bug.cgi?id=9100](https://bugs.freedesktop.org/show_bug.cgi?id=9100) (NEW)
[https://bugs.launchpad.net/xorg-server/+bug/63310](https://bugs.launchpad.net/xorg-server/+bug/63310) (NEW)

---

