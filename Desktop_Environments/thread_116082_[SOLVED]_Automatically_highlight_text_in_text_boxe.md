---
title: "[SOLVED] Automatically highlight text in text boxes?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by CatKiller on 2006-01-11
I recently switched to Ubuntu from Windows 2000, and I really like it. But there's currently one niggly thing that irrationally winds me up - to go with the many, many things that make me go "wow, that's great".

Under Windows when you click on a text box, the text is automatically highlighted, making it easy to overwrite it with something else. The one I use most is the search box in Firefox, but it's useful other places too. This seems to me to be more efficient, since if I don't want to overwrite the text, I only have to click the mouse again where it is, but without the text highlighted I have to mess around with either click-and-drag or Shift-Ctrl-End.

I have no idea if this would be a GNOME-thing, or a something-else-thing, or even if it exists as a configurable option, so I don't really know what to look for. It's only a tiny thing, but having it the other way would make me a surprising amount happier. Any guidance would be much appreciated.

---

### Post by 23meg on 2006-01-11
It's an X thing; in X, whenever you select something, it's copied to the clipboard, ready to be pasted with the middle button (or both mouse buttons if you don't have a middle one), so auto highlighting would mean auto copying; that's the reason most (if not all) GUIs avoid it as a default.

In Firefox you can change this default for the address bar by setting the value of the browser.urlbar.clickSelectsAll key which you can find by typing "about:config" in your address bar.

---

### Post by srt4play on 2006-01-11
If you double click in the field, it will highlight all of the text.

---

### Post by Randomskk on 2006-01-11
[QUOTE=23meg]It's an X thing; in X, whenever you select something, it's copied to the clipboard, ready to be pasted with the middle button (or both mouse buttons if you don't have a middle one), so auto highlighting would mean auto copying; that's the reason most (if not all) GUIs avoid it as a default.

In Firefox you can change this default for the address bar by setting the value of the browser.urlbar.clickSelectsAll key which you can find by typing "about:config" in your address bar.[/QUOTE]
Thanks for that,  gotta admit that's the one place I need it and I've been looking for a while :)

---

### Post by srt4play on 2006-01-11
I don't understand why it's so hard to just double click instead of single click?

---

### Post by CatKiller on 2006-01-12
[QUOTE=srt4play]I don't understand why it's so hard to just double click instead of single click?[/QUOTE]

Erm, because I didn't know? Thanks for the tip, and thanks to 23meg for the explanation.

---

### Post by ardchoille on 2006-01-12
[QUOTE=23meg]It's an X thing; in X, whenever you select something, it's copied to the clipboard, ...[/QUOTE]

Uhm.. no it isn't. Here's a test:

1. open gedit, or your favourite text editor
2. hilight some text and press CTRL+C to copy to the clipboard
3. hilight some different text (for middle click later) but don't press CTRL+C
4. go to your text editor and CTRL+V to paste what you copied with CTRL+C in step 2
5. now middle-click to paste the different text from step 3

Simply hilighting text doesn't copy it to the clipboard, but CTRL+C does copy to the clipboard.

---

### Post by 23meg on 2006-01-12
I know; another way of putting what you've illustrated is that there are two separate hypothetical clipboards, and simply selecting some text copies it to one, whereas selecting and hitting ctrl+c or choosing "copy" from the context menu copies it to the other. But note that in both, you have to highlight the text, so the "ctrl+c clipboard" overwrites the other one when you use it. 

Also, for some reason (maybe an intended one) the middle-click method doesn't work for me in gedit; it works everywhere else.

---

### Post by doclivingston on 2006-01-12
[QUOTE=ardchoille]1. open gedit, or your favourite text editor
2. hilight some text and press CTRL+C to copy to the clipboard
3. hilight some different text (for middle click later) but don't press CTRL+C
4. go to your text editor and CTRL+V to paste what you copied with CTRL+C in step 2
5. now middle-click to paste the different text from step 3

Simply hilighting text doesn't copy it to the clipboard, but CTRL+C does copy to the clipboard.[/QUOTE]

There are two different clipboards in X (well three actually, but no-one uses the third one). The "normal" one (CLIPBOARD) copies with applications' Copy function, and pastes with applications' Paste function. The other one (PRIMARY) copies when you select something, and pastes when you middle click.

Selecting text won't overwrite the CLIPBOARD clipboard, and using Copy shouldn't overwrite the PRIMARY clipboard. However it is generally hard to Copy text without selecting it, and some applications overwrite PRIMARY when copying (e.g. Firefox's "copy link address").

---

### Post by ardchoille on 2006-02-10
Well, I stand corrected. I had no idea there was more than one clipboard in X. Thank you for the information:)

---

