---
title: "ASCII/ Unicode in a non-English system"
date: 2014-11-28
forum: Desktop Environments
---

### Post by i3yboy on 2014-11-28
Hello beloved Ubunters. 
I am using an Ubuntu Unicorn (**14.10**), and after much effort it seems that I am unable to produce ASCII symbols using the Keyboard. It might have something to do with the keyboard and system being non-English, thogh I have added an English Keyboard - and still didn't overcome this problem.

I defined a **compose key** (Left Ctrl, on which I have preseesd and released before inputing the code, as well as pressed and didn't release), 
also tried the** Ctrl-Shift-U** (both Right and Left side Ctrl and Shift), (with and without releasing the U key), 
both to no avail.

The code I tried using was "266A" (&#9834;) as suggested here:
[http://fsymbols.com/keyboard/linux/unicode/](http://fsymbols.com/keyboard/linux/unicode/)

Funny enough, compose key does seem to work with shorter codes such as "MU" (producing µ).

I wish to be able to produce the charachters &#9792; and &#9794;.

Many thanks in advace for any assistance,
i3y

---

### Post by Impavidus on 2014-11-28
Ctrl+shift+a already means "select all" (in the terminal at least), so that doesn't work. Only ctrl+shift+{266} is detected, leading to &#614;. But you don't have to hold ctrl+shift whilst typing the hex code. It works fine if you
- Press and release ctrl+shift+u
- Type the hexadecimal code
- Hit either space, enter, control or shift to finish

When using the compose key, you don't have to hold the compose key. Just hit it and then type the other characters. If you hold the compose key, you may trigger other hotkeys.

---

### Post by grahammechanical on 2014-11-28
The sequence is Crtl+Shift+U, then release the keys. Next press the 4 character unicode number and then press Enter.

&#9792;&#9793;

Ctrl+Shift+U, then release the keys, then 2640, then Enter = &#9792;

Ctrl+Shift+U, then release the keys, then 2641, then Enter = &#9793;

Ctrl+Shift+U, then release the keys, then 2642, then Enter = &#9794;

And we get this with the Compose key disabled.

The Ubuntu Desktop User Guide says this

> [COLOR=#3C3C3C][FONT=sans-serif]To enter a character by its code point, press [/FONT][/COLOR][COLOR=#6C6C6C][FONT=sans-serif]Ctrl+Shift+U[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif], type the four-character code point, and press [/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]Enter[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]. If you often use characters that you can't easily access with other methods, you might find it useful to memorise the code point for those characters so you can enter them quickly.[/FONT][/COLOR]


The important bit that is left out is to release Ctrl+Shift+U before typing the four-character code point.

Regards

---

### Post by i3yboy on 2014-11-29
Many thanks, works like a charm!

Also, a nice table of unicodes:   [http://unicode-table.com/en/#ipa-extensions](http://unicode-table.com/en/#ipa-extensions)

---

### Post by GrouchyGaijin on 2014-11-29
Pretty cool I was wondering how to do character like this too

---

