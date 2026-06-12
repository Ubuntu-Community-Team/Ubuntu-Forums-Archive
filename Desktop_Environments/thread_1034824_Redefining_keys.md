---
title: "Redefining keys"
date: 2009-01-09
forum: Desktop Environments
---

### Post by ericwb on 2009-01-09
Hi all,

I was looking all over the place for a way to redefine the output of one of my keys. After much googling around, I was about to give up when I finally found out how to do it. (Note that this is not a question, it just might come in handy for someone who has the same problem.)

If you use a particular symbol a lot, you might want to have one of your keys redefined to output that particular symbol. For example, I wanted to be able to output "Ç" without having to do [Alt Gr]+[Shift]+[ç] or [Compose], [,], [Shift]+[C]. The idea was to reassign "Ç" to one of the keys I don't use, such as [µ] or [§]. (I use a French keyboard.)

To modify a key's output, you can modify a text file under **/usr/share/X11/xkb/symbols** (note: this has changed since I upgraded to Intrepid Ibex; it used to be /etc/X11/xkb/symbols if I remember correctly). This directory contains text files named after keyboard layouts, such as **us**, **en**, **fr**, etc. The files' contents are commented and are usually pretty self explanatory. Basically, you just edit the file with your favorite text editor, for example:
```

ledoc@Titou:~$ cd /usr/share/X11/xkb/symbols
ledoc@Titou:/usr/share/X11/xkb/symbols$ sudo gedit fr

```
Obviously, you must replace "fr" with whatever keyboard layout you are using. If you are unsure which portion of the file you should edit, you can issue **setxkbmap -print**, which in my case yields:
```

ledoc@Titou:~$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(azerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+fr(oss)+gr(polytonic):2+fr(bepo):3+us(dvorak-intl):4+inet(evdev)+level3(ralt_switch_for_alts_toggle):1+level3(ralt_switch_for_alts_toggle):2+level3(ralt_switch_for_alts_toggle):3+level3(ralt_switch_for_alts_toggle):4+group(alts_toggle)+compose(lwin)"	};
	xkb_geometry  { include "pc(pc104)"	};
};

```
The interesting line here is the one that starts with **xkb_symbols**. The part that reads "fr(oss)" indicates I have to modify the "oss" section within the "fr" file. The beginning of a section looks like this: **xkb_symbols "oss" {**, and a typical line within the section looks like this:
```

    key <AB10>  { [ exclam, section, exclamdown, 0x1002212 ] }; // ! § ¡ &#8722;   

```
This obviously describes the output of the <AB10> key, which yields [!] when alone, [§] when shifted, [¡] with [Alt Gr] and [&#8722;] with [Shift]+[Alt Gr]. Since I have no real need for the "section" symbol, I replaced it with "Ç":
```

    key <AB10>  { [ exclam,      Ç, exclamdown, 0x1002212 ] }; // ! Ç ¡ &#8722;  

```

Reset the X server by logging out and back in, and there you are.

This might not be the best solution, but it works for me. If you have any suggestions, feel free to comment.

---

### Post by cirorodrigues on 2009-03-12
Thank you for posting a good idea . I'm facing some trouble with a French keyboard. Differently from what you did, I'd like to assign a dead-key (an accute accent) to key combination AltGr+1. Do you any idea about how to setup dead-keys ?
Thanks in advance

---

### Post by ericwb on 2009-03-13
> **cirorodrigues said:**
> Thank you for posting a good idea . I'm facing some trouble with a French keyboard. Differently from what you did, I'd like to assign a dead-key (an accute accent) to key combination AltGr+1. Do you any idea about how to setup dead-keys ?
Thanks in advance

The dead acute and dead grave keys are already linked to [AltGr]+[ù] and [AltGr]+[*] on my French keyboard.

If you really want to redefine the [AltGr]+[1] key, you should go to the "fr" file, find the "oss" section, then modify the line that starts with "key <AE01>" :
```
key <AE01> { [ ampersand, 1, dead_caron, dead_ogonek ] }; // & 1 &#711; &#808;

```
Replace "dead_caron" with the keyword "dead_acute", and *voilà*.  ;)

```
key <AE01> { [ ampersand, 1, dead_acute, dead_ogonek ] }; // & 1 ' &#808;
```

Hope this helps.

---

### Post by cirorodrigues on 2009-03-13
thank you. You provided me some path to explore.

Ah, je pense que vous êtes peut-être français, alors merci beaucoup.

---

