---
title: "strange key mapping behavior"
date: 2009-05-09
forum: General Help
---

### Post by ztime on 2009-05-09
This behavior just started up a few hours ago.
I'm running Intrepid 8.10 server.
I think somehow I changed my key mapping configuration...

Behavior 1
whenever I depress the ' [read:quotation mark key], it doesn't register until after I depress another key. 

Behavior 2
if the ' key is followed by a vowel the letter is displayed with a mark above it (eg, á é í ó ú ý).


Examples
keystroke:     '
output:

keystroke:    'c
output:       'c

keystroke:    'a  
output:        á

any ideas would be greatly appreciated

Mahalo

---

### Post by soro2005 on 2009-05-09
You have changed your keyboard layout to another language. --> System -- Preferences -- Keyboard, and then the "Layouts" tab.

---

### Post by andthen.. on 2009-05-10
Im glad someone else is having the same problem. I got essays to write and iv tried different layouts according to cuntry and language.

I tried different "keyboard model" in "keyboard preferences" too but the key is still the same and I havent got quotation marks - same as ztime.

Can anyone shed some light please?

---

### Post by geirha on 2009-05-10
Such keys that do not appear until another key is typed are called dead keys. If you don't want to have dead keys, you can add a layout which has the "Eliminate dead keys" variant (in System -> Preferences -> Keyboard -> Layout)

For the console, you can change the keyboard layout with ```
sudo dpkg-reconfigure console-data
```

---

### Post by andthen.. on 2009-05-10
Thank you geirha for quick reply :)
OK i see so the problem is I have dead keys and I dont want them..

I looked in "System -> Preferences -> Keyboard -> Layout" to find the "Eliminate dead keys" variant but there isnt one for any language.

My Jaunty didnt seem to have "console-data" so i ran:

apt-get install console-data
dpkg-reconfigure console-data

I tried selecting a keymap from "arch list" and from "full list" but still no change (!)


I found a temporary fix though..
I pressed:

[AltGr + '] = [ ' ]
or [Shift + AltGr + "] = [ " ]

---

### Post by geirha on 2009-05-10
> **andthen.. said:**
> 
I looked in "System -> Preferences -> Keyboard -> Layout" to find the "Eliminate dead keys" variant but there isnt one for any language.


Add a new Layout to the list. There are two dropdown boxes in the new dialog window that pops up when you click the add button. In the first, layout, you select the language, in the second, variant, you can set Eliminate Dead keys.

---

### Post by andthen.. on 2009-05-10
It worked! Kind of, the keys have changed so that I no longer have to AltGr to get [ " ] and [ ' ].

I set the language as "English"
Then the variant dropdown box shows about 20 or so options..

The "United Kingdom" variants are:

United Kingdom
United Kingdom Colemak
United Kingdom Dvorak
United Kingdom Dvorak (UK Punctuation)
United Kingdom International (with dead keys)
United Kingdom Macintosh

it doesnt give me any "eliminate dead keys" but I chose United Kingdom and it seems to have worked
BUT...
now the [ " ] and the [ @ ] keys are the wrong way round. Though a fix would be good.. it wont kill me to have them the other way round...

---

