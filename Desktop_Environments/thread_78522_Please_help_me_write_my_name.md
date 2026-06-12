---
title: "Please help me write my name"
date: 2005-10-18
forum: Desktop Environments
---

### Post by André on 2005-10-18
Hi everybody,

i recently installed Breezy and i love it.

But i have a problem with the keyboard. The acute is not written like it should be.

My name: Andr&#180;e. The acute should be above the e.

How could i fix that?? It just gets printed to the screen and doesn&#180;t wait for me to enter another letter.

Any ideas??

Greetings
Andr&#180;e (hopefully being written right again soon ;-)

P.S.: German keyboard layout

---

### Post by jeremy on 2005-10-18
Couldn't you just change your name? :rolleyes: 

Seriously though, I have a Spanish kb layout and can write André without any problem, are you sure your kb is set up correctly?

---

### Post by André on 2005-10-18
Hi,

no, i am not sure, but i would like to know what the right setting would be ;-)

Thanks for the reply
Andr´e

---

### Post by André on 2005-10-18
Hi,

here comes the part of my xorg.conf:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
EndSection

```

Looks quite standard, doesn&#180; t it??

Greetings
Andr&#180;e (still trying to write his name)

P.S.: The keyboard layout in Gnome is "Germany eliminate dead keys"... Is this right?

---

### Post by gonr on 2005-10-19
Hi,

I had a somewhat similar problem (dead keys didn't work), but not exactly the same. Other people also have problems with dead keys in breezy.

I found that installing this package fixed it:
[http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb](http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb)

It's from [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372)
which is in state 'pending upload' (so I guess it isn't released yet, but is a 
known fix?)

---

### Post by André on 2005-10-20
Hi,

sorry, i am a little stressed right now so i didn't notice that i didn't mark my problem as solved.

I fixed it by forcing my xorg.conf to use Dead keys like:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
#        Option          "XkbVariant"    "nodeadkeys"
EndSection

```

I am a bit embarassed because it took quite some time to notice that i actually wanted dead keys ;-)

Now it works

Greetings
André (Yeah, that's my name :-))

---

### Post by bdash on 2005-10-20
Here is what I use, to input French on my dvorak:

keycode 0x73 = Multi_key

in the ~/.Xmodmap file. So I press Win+' then e and I get a é.

---

