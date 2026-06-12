---
title: "Keyboard problem (with 'C')"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Jaoqua on 2008-05-24
Problem with a key mapping:

I'm an Ubuntu noob and I've been installing all sorts of stuff to see what's any good. Most of it gets removed again, but in between I have set up key preferences for various things, now forgotten.

The problem is than now my machine doesn't let me type shift-c. All the other capitals work OK (see!) and if I use caps lock then I get C perfectly well. But shift-c gives me nothing.

Well, not quite nothing. When I type shift-c the cursor blinks briefly signifying that the machine knows a key has been pressed, but I get no character.

How can I find and correct the key mapping? It looks to me like it's been redirected to some other purpose, but heaven knows what.

Since I'm a noob please make your answers explicit. I have looked at the forums and there are bits of stuff about key mapping but I can't seem to follow their instructions. Stupidity? Lack of knowlege? Probably both. Please respond accordingly.

Thx.

    - J.

---

### Post by mali2297 on 2008-05-25
Open a terminal and type (or copy/paste)
```

xmodmap -pke | head -n 50

```
Post the output.

---

### Post by Jaoqua on 2008-05-25
Thanks for your interest, Mali. Here's the output:
keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam onesuperior exclamdown onesuperior exclamdown
keycode  11 = 2 quotedbl twosuperior oneeighth twosuperior oneeighth
keycode  12 = 3 sterling threesuperior sterling threesuperior sterling
keycode  13 = 4 dollar EuroSign onequarter EuroSign onequarter
keycode  14 = 5 percent onehalf threeeighths onehalf threeeighths
keycode  15 = 6 asciicircum threequarters fiveeighths threequarters fiveeighths
keycode  16 = 7 ampersand braceleft seveneighths braceleft seveneighths
keycode  17 = 8 asterisk bracketleft trademark bracketleft trademark
keycode  18 = 9 parenleft bracketright plusminus bracketright plusminus
keycode  19 = 0 parenright braceright degree braceright degree
keycode  20 = minus underscore backslash questiondown backslash questiondown
keycode  21 = equal plus dead_cedilla dead_ogonek dead_cedilla dead_ogonek
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q at Greek_OMEGA at Greek_OMEGA
keycode  25 = w W lstroke Lstroke lstroke Lstroke
keycode  26 = e E
keycode  27 = r R paragraph registered paragraph registered
keycode  28 = t T tslash Tslash tslash Tslash
keycode  29 = y Y leftarrow yen leftarrow yen
keycode  30 = u U downarrow uparrow downarrow uparrow
keycode  31 = i I rightarrow idotless rightarrow idotless
keycode  32 = o O oslash Oslash oslash Oslash
keycode  33 = p P thorn THORN thorn THORN
keycode  34 = bracketleft braceleft dead_diaeresis dead_abovering dead_diaeresis dead_abovering
keycode  35 = bracketright braceright dead_tilde dead_macron dead_tilde dead_macron
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A ae AE ae AE
keycode  39 = s S ssharp section ssharp section
keycode  40 = d D eth ETH eth ETH
keycode  41 = f F dstroke ordfeminine dstroke ordfeminine
keycode  42 = g G eng ENG eng ENG
keycode  43 = h H hstroke Hstroke hstroke Hstroke
keycode  44 = j J
keycode  45 = k K kra ampersand kra ampersand
keycode  46 = l L lstroke Lstroke lstroke Lstroke
keycode  47 = semicolon colon dead_acute dead_doubleacute dead_acute dead_doubleacute
keycode  48 = apostrophe at dead_circumflex dead_caron dead_circumflex dead_caron
keycode  49 = grave notsign bar bar bar bar
keycode  50 = Shift_L
keycode  51 = numbersign asciitilde dead_grave dead_breve dead_grave dead_breve
keycode  52 = z Z guillemotleft less guillemotleft less
keycode  53 = x X guillemotright greater guillemotright greater
keycode  54 = c C cent copyright cent copyright
keycode  55 = v V leftdoublequotemark leftsinglequotemark leftdoublequotemark leftsinglequotemark
keycode  56 = b B rightdoublequotemark rightsinglequotemark rightdoublequotemark rightsinglequotemark
keycode  57 = n N

I'm guessing this was the line you were after:
keycode  54 = c C cent copyright cent copyright

Looks OK to me. Still no C though. But interestingly yesterday I set up a guest account for my daughter to use and all works well there. So it's clearly a user-specific problem.

---

### Post by mali2297 on 2008-05-25
> **Jaoqua said:**
> 
Looks OK to me. Still no C though. But interestingly yesterday I set up a guest account for my daughter to use and all works well there. So it's clearly a user-specific problem.

Your user-specific settings are stored in hidden "dot" files in your home directory. Create a backup folder and move the hidden files and directories there. Then either start from scratch or move back the old configuration files one by one while checking that the problem does not reappear.

---

### Post by Jaoqua on 2008-05-27
Pheew!! What a load of hassle that was!

Anyway, it worked, so thanks! The problem was under .gconf. I never really found out what it was, even though I looked through a thousand xml files. In the end I merged my way out of it by accident. Ignorance and luck prevailed. 

Thanks!

---

