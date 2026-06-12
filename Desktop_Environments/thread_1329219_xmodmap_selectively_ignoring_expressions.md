---
title: "xmodmap selectively ignoring expressions"
date: 2009-11-17
forum: Desktop Environments
---

### Post by grshorwich on 2009-11-17
Here's a weird one for the gallery.

Take these few lines from a 245-line .xmodmap file in Ubuntu-9.10:

```
keycode 0x18 =  q               Q               q               Q               Greek_omega     Greek_OMEGA
keycode 0x19 =  w               W               w               W               twosuperior     Greek_alpha
keycode 0x1A =  e               E               e               E               eacute          egrave
keycode 0x1B =  r               R               r               R               registered      paragraph

keycode 0x39 =  n               N               n               N               ntilde          Ntilde
```All the expressions in the file are evaluated correctly (my keyboard does what I want it to do, I get the &#969; and &#937; symbols using right-alt and Q, ² and &#945; with the W etc.) with the exception of 2 lines. Only the 'e' and 'n' lines seem to disobey orders.

If I assign the symbols eacute, egrave, ntilde and Ntilde to other keys, it all works fine. That's what I've done pending finding chapter and verse on this.

It's just the combination of the right alt key and either the E or N key that's not working. If, for example, I run:

```
xmodmap -e "keycode 0x1A = e eacute"
```then, pressing shift+E does get me an é with an acute accent.

Why should those two lines be partially ignored? Is there anything in the system hooking intothese keyboard shortcuts so that applications don't receive the event or what?

Any pointers would be much appreciated.

Thanks in advance.

---

