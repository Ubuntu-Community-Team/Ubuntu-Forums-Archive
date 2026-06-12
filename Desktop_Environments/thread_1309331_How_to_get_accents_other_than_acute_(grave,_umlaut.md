---
title: "How to get accents other than acute (grave, umlaut, etc)"
date: 2009-11-01
forum: Desktop Environments
---

### Post by frisket on 2009-11-01
I just installed 9.10 and it's working fine. I live in Ireland, so it installed the en.ie keyboard layout, so I can use AltGr to access most of the common Unicode symbols that I need, plus áéíúóÁÉÍÓÚ...but no sign of how to get umlauts, graves, circumflexes, or any other accents. The AltGr key can't do it, because (unlike earlier versions) it does not now work as a dead key but generates characters in combination with other keys.

This is a Dell Dimension 4550 with the original keyboard, so to the right of the spacebar I have: AltGr, a menu key of some kind, and Ctrl. There is no "Compose" key as illustrated in the X.Org printout generated from Karmic's System|Preferences|Keyboard|Layouts|<select>|Print menu. 

The key with the menu icon on the keycap brings up the current application's menu (unsurprisingly), so I tried resetting this to be the Compose key (in System|Preferences|Keyboard|Layouts|Options, and that now works in simultaneous combination with v to preform a ha&#269;ek on the next character, and similarly with c to create a çedilla, and n to create a tilde, but NOT in combination with b to create an umlaut (as it ought to, according to the printout). And there is no indication of which key ought to be pressed in combination with Compose to preform a grave, circumflex, or other accent.

Have I missed something in the menus, or is there some documentation on this, or is the Dell keyboard simply not usable for the purpose?

///Peter

---

### Post by leorolla on 2009-11-19
What does shift+2 produce?

---

### Post by frisket on 2009-11-29
> **leorolla said:**
> What does shift+2 produce?

The double-quote mark. 

Sorry, I should obviously have added: I'm in Ireland; I use a UK keyboard layout, so double-quote is shift-2 and the @ sign is on shift-single-quote.

In what way would that affect how I generate letters with umlauts?

---

### Post by the8thstar on 2009-11-29
If you are using Gnome, try adding the character pane to one of the panels. Then you can call them by a click and a single CTRL-V in a document.

---

### Post by frisket on 2009-12-05
> **the8thstar said:**
> If you are using Gnome, try adding the character pane to one of the panels. Then you can call them by a click and a single CTRL-V in a document.

Nice idea, thanks, and it works well if you only want the occasional character. But I sometimes write in German and French, and it's a bit puzzling to find that the German ß is available from the keyboard, but none of the other accented letters; and for French, the acutes are available but not the graves. Whoever designed the selection available was obviously no linguist :-)

---

### Post by frisket on 2009-12-06
Found it. I had to go through all possible combinations on all keys and document them. Maybe someone has already done this, or perhaps it's buried somewhere at x.org but it's not evident.

The answer is AltGr-8 is the dead-key for umlauts and AltGr-backslash is the dead-key for graves. Neither is guessable; and why these were chosen instead of the obvious " and ` is anyone's guess. Maybe the mappers just like making things difficult for people.

I have put a PDF keyboard map with some comments at [http://silmaril.ie/linux/keyboard.pdf](http://silmaril.ie/linux/keyboard.pdf) in case it's any use to others.

Thank you all for your comments.

If someone knows how to mark this thread SOLVED I'd be grateful. There doesn't seem to be a button for this anywhere.

---

