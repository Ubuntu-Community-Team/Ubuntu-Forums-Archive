---
title: "how to edit what symbols are produced on the keyboard, specifically dead_tilde"
date: 2009-04-26
forum: General Help
---

### Post by Irishpolyglot on 2009-04-26
I am having a tiny problem with my keyboard and I have finally found out why it is happening. Basically I want to type Portuguese letters on my Spanish keyboard. i.e. ã and õ. In Windows, pressing Alt Gr+4 creates what's called the "dead_tilde" key so when you press it nothing happens, but when you press a or o immediately after, it will produce the characters with the tildes over them. When I press it in Ubuntu, ~ is immediately produced with Alt Gr+4 so the same combination gives me ~a or ~o, which is not useful at all.

I found a program called xkeycaps and I can see that instead of dead_tilde Alt+Gr has been set to asciitilde. Normally xkeycaps can be used to edit your keys so I would simply change it in the GUI, but there is a strange problem with the scroll bar so I can only go down in the list and not up, so I can't find dead_tilde to select it.

Is there another program I can use, or more directly, where is the text file I can edit with gedit to just change asciitilde to dead_tilde directly, specifically for the Spanish keyboard layout? Thanks!!

---

### Post by Irishpolyglot on 2009-04-29
No ideas on this?

---

### Post by Irishpolyglot on 2009-05-19
I've got a temporary solution of adding a character palette to the panel with the symbols that I want, but it's getting bigger and bigger, since I've to write in Czech too now and need inverted circumflexes on letters like &#345;&#269;&#283;&#328;šž. It would be great if I could figure out the way to assign a "dead" character for the inverted circumflex and for the Portuguese tilde letters as before, since the panel works by copy-and-paste and interrupts the flow for writing fast.

Any indication of the right direction to go really appreciated :)

---

### Post by Irishpolyglot on 2009-05-21
Hm.. I was sure this was something really simple, but it would seem not if the whole forum is stumped... :(

---

### Post by mcduck on 2009-05-21
Usually you can select two alternative keyboard layouts, one with dead keys and one without.

With most keyboard layouts you can also get large variety of special letter and characters directly with AltGr+letter (or Shift-AltGr+letter).

---

### Post by Irishpolyglot on 2009-05-21
Yes I know, but the whole point is that I want to add these keys to the keyboard I already use. I've tried switching between 3 keyboard layouts (with the shortcut key option to switch) and it's more time consuming than having a single key for the particular accent I want (like I do in Windows; Alt Gr + 4 + a = ã for Spanish keyboard in Windows but not in Linux, so I want to simply edit it).
I really think this has a simple solution. I just need to know which file I need to run gedit on to change the one keyboard layout directly.

---

### Post by Irishpolyglot on 2009-11-21
I came back to this problem after months of using more awkward work-arounds. I found that going back to the xkeycaps application and selecting the last option in the list and then double clicking the selected term on the left part of the screen brought the list up (I couldn't scroll down before).
I couldn't find the "deadtilde" that I wanted, but found atilde and otilde, which I simply added as Alt+Gr options for A and O on the keyboard and they were applied immediately. Not *exactly* the solution I was looking for, but just as quick so I'm happy :)

Just thought I'd mention this if anyone else ever has a similar issue.

---

