---
title: "Enemy Territory - Azerty, Brightness problems"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by Xantos on 2007-06-12
Hi all,

I have some problems with ET as you can see.

In this stupid country (Belgium) we use azerty keyboards, which gives problems in ET. 

Difference between qwerty and azerty:
Well there are a few differences but I am only talking about the numbers. In qwerty you can just press the buttons and you got your number. At azerty you need to do shift + those buttons to select the numbers.

Well in my etconfig and in the panel options there is no problem.
You can see that number 1 to 7 are assigned to my weaponbank, but when I try those buttons in the game it's not that at all (except if I press shift+number, but shift is already assigned to jump so I get some problems with that :p).

If I want to re-assign my weaponbank, by pressing the numbers, I get some kind of ASCII values like 0x22 for example. Weird if you ask me:D

My second problem is that the brightness of the game sets back to standard every 10 minutes or so (could be that it's beryl, need to test it yet).

I hope some guys can help me out, my clan is dying and I want to put some life back in it :D

I hope my english is a bit correct and understandable.

Thnx

---

### Post by Rafty on 2007-06-12
> **Xantos said:**
> My second problem is that the brightness of the game set's back to standard every 10 minutes or so (could be that it's beryl, need to test it yet).
thats the screensaver bug. disable the screesaver should help till there's a bugfix ;)


> **Xantos said:**
> In this stupid country (Belgium) we use azerty keyboards, which gives problems in ET. 

Difference between qwerty and azerty:
Well there are a few differences but I am only talking about the numbers. In qwerty you can just press the buttons and you got your number. At azerty you need to do shift + those buttons to select the numbers.

Well in may autoconfig and in the panel options there is no problem.
You can see that nulber 1 to 7 are assigned to my weaponbank, but when I try those buttons in the game it's not that at all (except if I press shift+number, but shift is already assigned to jump so I get some problems with that :p).
maybe reconfigure all keys/bindings. for this you can use the ingame-menu or edit the "etconfig.cfg" in "/home/yourname/.etwolf/etmain/profiles/yourname".

---

### Post by Xantos on 2007-06-13
Aha, the screensaver. Thnx alot it works.

But that with the keys don't work :( 
Like I said, I get some ASCII values if I do that in the in-game menu. If I type it in my etconfig.cfg file I still have the problem.

---

### Post by Rafty on 2007-06-13
have you checked the gnome/kde keyboard setting? maybe there are shortkeys or something enabled?

---

### Post by Xantos on 2007-06-13
I'm running Gnome.
You mean that I use the numbers as shortkeys? No I don't :?

---

### Post by Rafty on 2007-06-13
have you localised your ubuntu installation to the french (or what you speak ;)) language ?

---

### Post by Xantos on 2007-06-13
I'm flemish so I speak dutch. The other half of the country speak even worse english then me. :p

But I installed to dutch(Belgium) yes. ;)

And it's only in the game that I have problems with those numbers. In Ubuntu itself is everything alright.
The 'A' is still an 'A' in ET and the 'Q' a 'Q' so it's really only the numbers.

---

### Post by frodon on 2007-06-13
For the brightness when it arrives just move the brightness cursor in the ET options and it will go back to normal (i have the bug from time to time as well), for your azerty keyboard indeed ET knows only the qwerty layout so here is a trick if you can't leave with it (in my case i leave really well with it) :

I assume you use the french keyboard layout.

1- create a a text file called ETlauncher on your desktop for instance (gedit ~/Desktop/ETlauncher) and put this inside :
```
#!/bin/sh

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

xmodmap ~/.etwolf/kbd_et
et "$*"
xmodmap /usr/share/xmodmap/xmodmap.fr
```Basicaly it set your sound config to avoid the common ET sound issue then start a custom keyboard mapping called **kbd_et**, launch ET and restore your french keyboard layout when you exit ET.

2- create your custom keyboard mapping to match the qwerty standard, for this open a text file called **kbd_et** in your .etwolf directory (gedit ~/.etwolf/kbd_et) then put this inside :
```
keycode  10 = 1 ampersand exclamdown
keycode  11 = 2 eacute asciitilde Eacute
keycode  12 = 3 quotedbl numbersign sterling
keycode  13 = 4 apostrophe braceleft U2019
keycode  14 = 5 parenleft bracketleft trademark
keycode  15 = 6 minus bar U2212
keycode  16 = 7 egrave grave Egrave
keycode  17 = 8 underscore backslash emdash
keycode  18 = 9 ccedilla asciicircum Ccedilla
keycode  19 = 0 agrave at Agrave
keycode  20 = parenright
keycode  21 = equal plus 

keycode  87 = KP_1
keycode  88 = KP_2
keycode  89 = KP_3
keycode  83 = 4
keycode  84 = KP_5
keycode  85 = KP_6
keycode  79 = 7
keycode  80 = 8
keycode  81 = KP_9
keycode  90 = KP_0

keycode 63 = KP_Multiply
keycode 112 = KP_Divide
keycode 91 = KP_Decimal

keycode 49 = twosuperior
```

3- give your launcher execute rights :
```
chmod +x ~/Desktop/ETlauncher
```

4- double click your launcher to start ETand enjoy !

---

### Post by Xantos on 2007-06-13
You are my hero [-o<
I gonna test it this evening.

Thank you!

---

### Post by Xantos on 2007-06-13
Hmmm it doesn't work completely.
I used xmodmap.be instead of .fr but it doesn't change the keyboard back to normal after closing ET.

Also in ET my numbers don't work. When I press 2, I get my ET-console, the rest of the numbers does nothing.

EDIT: Ok everything works now. I copy-pasted my xmodmap.be to my kbd_et and changed the position of the numbers.

ETlauncher
```

#!/bin/sh

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

xmodmap ~/.etwolf/kbd_et
et "$*"
xmodmap /usr/share/xmodmap/xmodmap.be

```

kbd_et
```

! Converted keytable file to xmodmap file
! with mk_modmap by root@linux.chanae.stben.be Tue Nov 12 01:39:34 MET 1996
clear Mod1
clear Mod2
! 
keycode   8 =
keycode   9 = Escape
keycode  10 = 1 ampersand bar
keycode  11 = 2 eacute at
keycode  12 = 3 quotedbl numbersign
keycode  13 = 4 apostrophe braceleft
keycode  14 = 5 parenleft 
keycode  15 = 6 asciicircum asciicircum
keycode  16 = 7 egrave
keycode  17 = 8 exclam
keycode  18 = 9 ccedilla braceleft
keycode  19 = 0 agrave braceright
keycode  20 = parenright degree
keycode  21 = minus underscore
keycode  22 = BackSpace
keycode  23 = Tab
keycode  24 = a
keycode  25 = z
keycode  26 = e E currency
keycode  27 = r
keycode  28 = t
keycode  29 = y
keycode  30 = u
keycode  31 = i
keycode  32 = o
keycode  33 = p
keycode  34 = dead_circumflex dead_diaeresis bracketleft
keycode  35 = dollar asterisk bracketright
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = q
keycode  39 = s
keycode  40 = d
keycode  41 = f
keycode  42 = g
keycode  43 = h
keycode  44 = j
keycode  45 = k
keycode  46 = l
keycode  47 = m
keycode  48 = ugrave percent dead_acute
keycode  49 = twosuperior threesuperior
keycode  50 = Shift_L
keycode  51 = mu sterling dead_grave
keycode  52 = w
keycode  53 = x
keycode  54 = c
keycode  55 = v
keycode  56 = b
keycode  57 = n
keycode  58 = comma question dead_cedilla
keycode  59 = semicolon period
keycode  60 = colon slash Multi_key
keycode  61 = equal plus dead_tilde
keycode  62 = Shift_R
keycode  63 = KP_Multiply
keycode  64 = Alt_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 F11
keycode  68 = F2 F12
keycode  69 = F3 F13
keycode  70 = F4 F14
keycode  71 = F5 F15
keycode  72 = F6 F16
keycode  73 = F7 F17
keycode  74 = F8 F18
keycode  75 = F9 F19
keycode  76 = F10 F20
keycode  77 = Num_Lock
keycode  78 = Scroll_Lock
keycode  79 = KP_7
keycode  80 = KP_8
keycode  81 = KP_9
keycode  82 = KP_Subtract
keycode  83 = KP_4
keycode  84 = KP_5
keycode  85 = KP_6
keycode  86 = KP_Add
keycode  87 = KP_1
keycode  88 = KP_2
keycode  89 = KP_3
keycode  90 = KP_0
keycode  91 = KP_Decimal
keycode  92 = 0x1007ff00
keycode  93 =
keycode  94 = less greater backslash
keycode  95 = F11
keycode  96 = F12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 = Begin
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause
keycode 111 = Print
keycode 112 = KP_Divide
keycode 113 = Mode_switch
keycode 114 = Break
! right windows-logo key
! in "windows" keyboards the postion of the key is annoying, is where AltGr
! usually resides, so go definie it as AltGr
keycode 116 = Mode_switch
! right windows-menu key, redefined as Compose key
keycode 117 = Multi_key
add Mod1 = Alt_L
add Mod2 = Mode_switch

```

Thank you Rafty and Frodon, I appreciate your help very much.

---

### Post by zuzuzzzip on 2007-08-03
thx this is exactly what i needed :D 
I'm also from Belgium, Flemish region!

edit: it did not change back to normal
to make it change back to normal i copied the output of "xmodmap -pke" (because xmodmap.be didn't seem to be right)
```
keycode   8 =
keycode   9 = Escape
keycode  10 = ampersand 1 bar exclamdown bar exclamdown
keycode  11 = eacute 2 at oneeighth at oneeighth
keycode  12 = quotedbl 3 numbersign sterling numbersign sterling
keycode  13 = apostrophe 4 onequarter dollar onequarter dollar
keycode  14 = parenleft 5 onehalf threeeighths onehalf threeeighths
keycode  15 = section 6 asciicircum fiveeighths asciicircum fiveeighths
keycode  16 = egrave 7 braceleft seveneighths braceleft seveneighths
keycode  17 = exclam 8 bracketleft trademark bracketleft trademark
keycode  18 = ccedilla 9 braceleft plusminus braceleft plusminus
keycode  19 = agrave 0 braceright degree braceright degree
keycode  20 = parenright degree backslash questiondown backslash questiondown
keycode  21 = minus underscore dead_cedilla dead_ogonek dead_cedilla dead_ogonek
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = a A at Greek_OMEGA at Greek_OMEGA
keycode  25 = z Z lstroke Lstroke lstroke Lstroke
keycode  26 = e E EuroSign cent EuroSign cent
keycode  27 = r R paragraph registered paragraph registered
keycode  28 = t T tslash Tslash tslash Tslash
keycode  29 = y Y leftarrow yen leftarrow yen
keycode  30 = u U downarrow uparrow downarrow uparrow
keycode  31 = i I rightarrow idotless rightarrow idotless
keycode  32 = o O oslash Oslash oslash Oslash
keycode  33 = p P thorn THORN thorn THORN
keycode  34 = dead_circumflex dead_diaeresis bracketleft dead_abovering bracketleft dead_abovering
keycode  35 = dollar asterisk bracketright dead_macron bracketright dead_macron
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = q Q ae AE ae AE
keycode  39 = s S ssharp section ssharp section
keycode  40 = d D eth ETH eth ETH
keycode  41 = f F dstroke ordfeminine dstroke ordfeminine
keycode  42 = g G eng ENG eng ENG
keycode  43 = h H hstroke Hstroke hstroke Hstroke
keycode  44 = j J
keycode  45 = k K kra ampersand kra ampersand
keycode  46 = l L lstroke Lstroke lstroke Lstroke
keycode  47 = m M dead_acute dead_doubleacute dead_acute dead_doubleacute
keycode  48 = ugrave percent dead_acute dead_caron dead_acute dead_caron
keycode  49 = twosuperior threesuperior notsign notsign notsign notsign
keycode  50 = Shift_L
keycode  51 = mu sterling dead_grave dead_breve dead_grave dead_breve
keycode  52 = w W guillemotleft less guillemotleft less
keycode  53 = x X guillemotright greater guillemotright greater
keycode  54 = c C cent copyright cent copyright
keycode  55 = v V leftdoublequotemark leftsinglequotemark leftdoublequotemark leftsinglequotemark
keycode  56 = b B rightdoublequotemark rightsinglequotemark rightdoublequotemark rightsinglequotemark
keycode  57 = n N
keycode  58 = comma question dead_cedilla masculine dead_cedilla masculine
keycode  59 = semicolon period horizconnector multiply horizconnector multiply
keycode  60 = colon slash periodcentered division periodcentered division
keycode  61 = equal plus dead_tilde dead_abovedot dead_tilde dead_abovedot
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock Pointer_EnableKeys
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = less greater backslash backslash backslash backslash
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = ISO_Level3_Shift
keycode 114 =
keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 129 =
keycode 130 =
keycode 131 =
keycode 132 =
keycode 133 =
keycode 134 =
keycode 135 =
keycode 136 =
keycode 137 =
keycode 138 =
keycode 139 =
keycode 140 =
keycode 141 =
keycode 142 =
keycode 143 =
keycode 144 =
keycode 145 =
keycode 146 =
keycode 147 =
keycode 148 =
keycode 149 =
keycode 150 =
keycode 151 =
keycode 152 =
keycode 153 =
keycode 154 =
keycode 155 =
keycode 156 = NoSymbol Meta_L
keycode 157 =
keycode 158 =
keycode 159 =
keycode 160 =
keycode 161 =
keycode 162 =
keycode 163 =
keycode 164 =
keycode 165 =
keycode 166 =
keycode 167 =
keycode 168 =
keycode 169 =
keycode 170 =
keycode 171 =
keycode 172 =
keycode 173 =
keycode 174 =
keycode 175 =
keycode 176 =
keycode 177 =
keycode 178 =
keycode 179 =
keycode 180 =
keycode 181 =
keycode 182 =
keycode 183 =
keycode 184 =
keycode 185 =
keycode 186 =
keycode 187 =
keycode 188 =
keycode 189 =
keycode 190 =
keycode 191 =
keycode 192 =
keycode 193 =
keycode 194 =
keycode 195 =
keycode 196 =
keycode 197 =
keycode 198 =
keycode 199 =
keycode 200 =
keycode 201 =
keycode 202 =
keycode 203 =
keycode 204 =
keycode 205 =
keycode 206 =
keycode 207 =
keycode 208 =
keycode 209 =
keycode 210 =
keycode 211 =
keycode 212 =
keycode 213 =
keycode 214 =
keycode 215 =
keycode 216 =
keycode 217 =
keycode 218 =
keycode 219 =
keycode 220 =
keycode 221 =
keycode 222 =
keycode 223 =
keycode 224 =
keycode 225 =
keycode 226 =
keycode 227 =
keycode 228 =
keycode 229 =
keycode 230 =
keycode 231 =
keycode 232 =
keycode 233 =
keycode 234 =
keycode 235 =
keycode 236 =
keycode 237 =
keycode 238 =
keycode 239 =
keycode 240 =
keycode 241 =
keycode 242 =
keycode 243 =
keycode 244 =
keycode 245 =
keycode 246 =
keycode 247 =
keycode 248 =
keycode 249 =
keycode 250 =
keycode 251 =
keycode 252 =
keycode 253 =
keycode 254 =
keycode 255 =

```
and tried to reload it using "xmodmap .etwolf/kbd_normal" at end of my script but that doesnt work...
is there a way to get it back to original settings?

---

### Post by zuzuzzzip on 2007-08-04
hmm xmodmap.be is certainly not the right layout for belgium, I think it's belarus (when you look in /usr/share/xmodmap/base.xml)
```
<description xml:lang="be">&#1047;&#1074;&#1099;&#1095;&#1072;&#1081;&#1085;&#1072;&#1103; &#1082;&#1083;&#1103;&#1074;&#1110;&#1103;&#1090;&#1091;&#1088;&#1072;</description>

```so i used xmodmap.fr :) closest to my original -but my numlcok key doesn't work, and key next to backspace and stuff :(
so i still haven't got the right one...
my Xorg.conf says:
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection
```does anyone have any idea which one to use??
or is there a way to reload xorg.conf's settings, without restarting X server?

edit: ok there's absolutely no way reloading xorg.conf without restarting X which is logic but I didn't know for sure.
I know only xmodmap the num keys and afterwards xmodwap it back :)

---

