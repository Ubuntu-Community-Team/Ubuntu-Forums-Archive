---
title: "xterm customization"
date: 2006-02-02
forum: Desktop Environments
---

### Post by Flexxy on 2006-02-02
I suppose this isnt really a gnome specific problem, or a problem at all... but i wasnt sure were else to post, but anyways....

I want to have xterm start without a title bar... i've searched around on the internet, but everything has to change the text in the title. I assume its something that I could add to ~/.Xresources being that were I was able to set the default font colour, background, ect.  So if anyone could help me out, id greatly apprechate it! thanx, in advanced, for you time!

~Flex

P.S. if anyone knows how to do this with another terminal program, gnome terminal for example... that would work as well

---

### Post by Flexxy on 2006-02-03
I was posting in other forums, and someone suggested that my soloution might be in gnome configuration, but they werent sure... i havnt gotten a chance to try anything yet, but i thought maybe someone might know here and save me some guess work... just an update... thanx

---

### Post by centyx on 2006-09-01
You've probably moved away from xterm by now, but if anyone else finds this thread, here's how to do it.

Edit ~/.Xdefaults to contain the following:

```

XTerm*background: Black
XTerm*foreground: Gray
*backarrowKeyIsErase: false 

```

After editing this file, run 'xrdb ~/.Xdefaults' to put changes into effect.

Have fun! :biggrin:

---

### Post by centyx on 2006-09-02
Oops. That's what I get for skimming too fast. Sorry.

No titlebar? A little confused by that one.

Personally, I prefer rxvt with the sabvga font from [http://home.earthlink.net/~us5zahns/enl/ansifont.html](http://home.earthlink.net/~us5zahns/enl/ansifont.html).

This is the config I use for rxvt:

cat ~/.Xdefaults

Rxvt*font: sabvga
Rxvt*scrollBar: false
Rxvt*background: Black
Rxvt*foreground: Gray
Rxvt*backspacekey: ^H

---

### Post by bobbymcsteels on 2007-08-02
[QUOTE=

```

XTerm*background: Black
XTerm*foreground: Gray
*backarrowKeyIsErase: false 

```
n:[/QUOTE]

Helped me out thanx

---

### Post by Nythain on 2007-08-02
im not sure if xterm is alone can do it... im pretty sure gnome-terminal can, and eterm, and aterm, and rxvt

---

