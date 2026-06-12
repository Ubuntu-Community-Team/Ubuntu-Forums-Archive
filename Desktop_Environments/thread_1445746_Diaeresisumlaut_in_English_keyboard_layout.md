---
title: "Diaeresis/umlaut in English keyboard layout"
date: 2010-04-03
forum: Desktop Environments
---

### Post by efAston on 2010-04-03
Hi,

I want to be able to edit my keyboard layout so that I can type vowels with umlauts.

I've just installed kubuntu 9.10 on my new laptop, and I pretty quickly found that I can't type ä or ö, which I use quite frequently as I often type in Finnish. In Windows I made my own keyboard layout where Alt+Gr and any of the vowels produces that vowel with an umlaut. In my desktop running kubuntu, I was able to get some functionality using xmodmap, but in the laptop I got the following;

aston@aston:~$ xmodmap -e "keycode 38 = a A a A adiaeresis Adiaeresis"
aston@aston:~$ xmodmap -e "keycode 38 = adiaresis A a A adiaeresis Adiaeresis"
xmodmap:  commandline:1:  bad keysym name 'adiaresis' in keysym list
xmodmap:  1 error encountered, aborting.
aston@aston:~$ xmodmap -e "keycode 38 = adiaresis A a A ä Adiaeresis"
xmodmap:  commandline:1:  bad keysym name 'adiaresis' in keysym list
xmodmap:  commandline:1:  bad keysym name 'ä' in keysym list
xmodmap:  2 errors encountered, aborting.

In none of the attempts could I type the ä, nor can I get it from character selector! I really want to get my umlauts as part of my keyboard layout, even when I'm not using foreign languages it's handy for stuff like German names. Does anyone have any good hints on editing keyboard layouts in KDE?

Cheers,
Aston

PS I'm using Dvorak-US if anyone is interested in knowing.

---

### Post by lovecats on 2010-04-03
I think you can download some softwares to help you input those vowels.
you can search with google and find one.

> **efAston said:**
> Hi,

I want to be able to edit my keyboard layout so that I can type vowels with umlauts.

I've just installed kubuntu 9.10 on my new laptop, and I pretty quickly found that I can't type ä or ö, which I use quite frequently as I often type in Finnish. In Windows I made my own keyboard layout where Alt+Gr and any of the vowels produces that vowel with an umlaut. In my desktop running kubuntu, I was able to get some functionality using xmodmap, but in the laptop I got the following;

aston@aston:~$ xmodmap -e "keycode 38 = a A a A adiaeresis Adiaeresis"
aston@aston:~$ xmodmap -e "keycode 38 = adiaresis A a A adiaeresis Adiaeresis"
xmodmap:  commandline:1:  bad keysym name 'adiaresis' in keysym list
xmodmap:  1 error encountered, aborting.
aston@aston:~$ xmodmap -e "keycode 38 = adiaresis A a A ä Adiaeresis"
xmodmap:  commandline:1:  bad keysym name 'adiaresis' in keysym list
xmodmap:  commandline:1:  bad keysym name 'ä' in keysym list
xmodmap:  2 errors encountered, aborting.

In none of the attempts could I type the ä, nor can I get it from character selector! I really want to get my umlauts as part of my keyboard layout, even when I'm not using foreign languages it's handy [miu miu sale]("http://miumiusale.net") for stuff like German names. Does anyone have any good hints on editing keyboard layouts in KDE?

Cheers,
Aston

PS I'm using Dvorak-US if anyone is interested in knowing.

---

### Post by Gömböc on 2010-04-03
How about using "compose-key" sequences, as described here?

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

To get the diaeresis/umlaut, you would press AltGr + [ and then type the letter above which you want the diaeresis.

---

### Post by efAston on 2010-04-03
The Swedish Dvorak layout has all the English letters in the same place so I think I can get used to it. I'm still curious, if anyone knows, how to actually edit keyboard layouts for KDE (the compose-key one is GNOME based, but thanks both of you guys).

---

### Post by Chronon on 2010-04-04
I haven't used it, but skim is supposed to be a kde interface for scim.
[https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu)

Does this help?

[http://www.scim-im.org/](http://www.scim-im.org/)

---

