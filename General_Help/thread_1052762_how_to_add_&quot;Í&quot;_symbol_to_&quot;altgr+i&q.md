---
title: "how to add &quot;Í&quot; symbol to &quot;altgr+i&quot; in english keymap in ubuntu gnome?"
date: 2009-01-28
forum: General Help
---

### Post by q.dinar on 2009-01-28
[http://ubuntuforums.org/showthread.php?t=1044134](http://ubuntuforums.org/showthread.php?t=1044134) :
[https://answers.launchpad.net/ubuntu/+question/57804](https://answers.launchpad.net/ubuntu/+question/57804) :
> hello.

i asked [https://answers.launchpad.net/ubuntu/+question/20524](https://answers.launchpad.net/ubuntu/+question/20524) one time, i tried that a little in several linux dustributions that time, but have not tried since then, have not learned. i was like lazy to do that.

this question 'how to add "Í" symbol to "altgr+i" in english keymap in ubuntu gnome?' is very concrete question and concretely this key assignment maybe useless, but this is as question about how to do, i use english keymap in the answer, because it is almost on all installed ubuntus if not on all.
...
...
thank you for the good advice. but i mean and want other thing. i want to make custom key combination on [any] layot i want.
for example if i switch layot to russia-tatar , that way you said do not work with this layot. for example i want get "Í" when pressing right alt + &#1080; in this layot (tatar).
please say at least how to make other general(?) new key combination for a/any keymap. like how to add "altgr"+"8" (and maybe "ctrl"+"8" or ctrl+shift+8 or alt+shift+8 if possible) to french or german or arabic or any keymap so that that combination gives some chinese hieroglyph for example. knowing how to make one extra combination for a keymap then i will know probably how to make others how i want.
after learning this i will ask about how to add another ["completely"] custom keymap to keymaps list, for example there are near 5 keymaps in "russia" category, i would want add to that list also tatar-latin or tatar-arabic or tatar-custom-qdinar keymap for example.

---

### Post by geirha on 2009-01-28
The following will print the current keymap to xmodmap.txt
```
xmodmap -pke >xmodmap.txt
```

Edit that and change keycode 31 to give iacutes with modifiers
```
keycode  31 = i I iacute Iacute iacute Iacute
```

Set this new modmap active, you can either just change that one line with:
```
xmodmap -e 'keycode  31 = i I iacute Iacute iacute Iacute'
```
or read the whole file again with
```
xmodmap xmodmap.txt
```

---

### Post by q.dinar on 2009-01-28
thank you.
i have read xmodmap --help and looked at its -pk and -pke option output and -pp and -grammar output.
pke i have saved to xmodmappke.txt . in it:
keycode  31 = i I Cyrillic_sha Cyrillic_SHA

so there is some problem in my case. it shows russian letters here though keyboard was not in russia-tatar mode when i runned that command, it was in english mode.

another wish. where i can know that "Cyrillic_sha" (if i need an other character)?
i have just looked at character map and "&#1080;"'s name is "cyrillic small letter i" there. its hex code is 438 (U+0438).
hex code would be more familiar for me than that "Cyrillic_sha" type name. as i know i can use them when modifying keymap. how?

---

### Post by geirha on 2009-01-28
You'll find a mapping between the hex code, unicode and the names in /usr/include/X11/keysymdef.h

```
$ grep 0438 /usr/include/X11/keysymdef.h
#define XK_Cyrillic_i                    0x06c9  /* U+0438 CYRILLIC SMALL LETTER I */
```

---

### Post by q.dinar on 2009-01-28
there is not keysymdef.h .

---

### Post by geirha on 2009-01-28
Then the package that installs it is not installed apparently. I assumed it was pre-installed. 

[x11proto-core-dev](apt:x11proto-core-dev) is the package to install then:
[http://packages.ubuntu.com/search?searchon=contents&keywords=keysymdef.h&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=keysymdef.h&mode=exactfilename&suite=intrepid&arch=any)

---

### Post by q.dinar on 2009-01-29
now i have installed it and looked that file.

i looked also that 0438. hm. what is 0x06c9 ? there is an explanation on beginning of the file. in it is said: "These 29-bit integer values identify characters or functions associated with each key ...". and i want to cite this: "For any future extension of the keysyms with characters already found in ISO 10646 / Unicode, the following algorithm shall be used. The new keysym code position will simply be the character's Unicode number plus 0x01000000."
there are seems to be not all symbols that are in unicode. do i have to add to this file and compile and install something if i need such character?
there are diacritic symbols in unicode. is it possible with this x11/linux system to set symbol+diacritic to a key. i mean not combination with diacritic for which also single character exists.

---

### Post by q.dinar on 2009-01-29
and what to do with that "keycode 31 = i I Cyrillic_sha Cyrillic_SHA"? try please yourself if needed to add russia-tatar keymap to your gnome and see that "xmodmap -pke". i should not delete Cyrillic_sha that is in tatar keymap, and i wanted to change only english keymap.
and more complex is the line next of that "keycode  31 = i I Cyrillic_sha Cyrillic_SHA":
"keycode  32 = o O Cyrillic_schwa Cyrillic_SCHWA Cyrillic_shcha Cyrillic_SHCHA"
what does that mean:
1: english keymap "o" key (=o)
2: english keymap shift+(capslock)"o" key (=O)
3: tatar keymap "o" key (=&#1241;)
4: tatar keymap shift+(capslock)"o" key (=&#1240;)
5: tatar keymap altGr+"o" key (=&#1097;)
6: tatar keymap altGr+(shift+(capslock))"o" key (=&#1065;)

so they are all just stay one by one in one line. what if i want to set
2.1: english keymap altGr+"o" key (=something)
2.2: english keymap altGr+(shift+(capslock))"o" key (=something)
and delete
5: tatar keymap altGr+"o" key (=&#1097;)
6: tatar keymap altGr+(shift+(capslock))"o" key (=&#1065;)
then it will look this way?:
"keycode  32 = o O something something Cyrillic_schwa Cyrillic_SCHWA
so if i list them as that previous version it is:
1: english keymap "o" key (=o)
2: english keymap shift+(capslock)"o" key (=O)
3: tatar keymap "o" key (=something)
4: tatar keymap shift+(capslock)"o" key (=something)
5: tatar keymap altGr+"o" key (=&#1241;)
6: tatar keymap altGr+(shift+(capslock))"o" key (=&#1240;)
but i wanted it to be
1: english keymap "o" key (=o)
2: english keymap shift+(capslock)"o" key (=O)
2.1: english keymap altGr+"o" key (=something)
2.2: english keymap altGr+(shift+(capslock))"o" key (=something)
3: tatar keymap "o" key (=&#1241;)
4: tatar keymap shift+(capslock)"o" key (=&#1240;)

and what would be if i add third keymap! or it is impossible? i now go to try. ok, it is possible. now i see xmodmap -pke. i have added azerbayjan cyrillic. now "keycode  32" line is:
keycode  32 = o O Cyrillic_schwa Cyrillic_SCHWA Cyrillic_shcha Cyrillic_SHCHA Cyrillic_shha Cyrillic_SHHA
and azerbayjani letters are &#1211; and &#1210; .
so how it is distinguished from this line to which keymap a letter applies? there can be 2 or 4 letters per keymap. how the system knows out that in english keymap are the first two letters, next 4 are of tatar keymap and last 2 are of azerbayjani?

---

### Post by q.dinar on 2009-02-04
[http://forum.mandriva.com/viewtopic.php?t=88377](http://forum.mandriva.com/viewtopic.php?t=88377)

---

