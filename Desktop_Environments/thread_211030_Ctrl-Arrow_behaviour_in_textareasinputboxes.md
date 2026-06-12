---
title: "Ctrl-Arrow behaviour in textareas/inputboxes"
date: 2006-07-07
forum: Desktop Environments
---

### Post by kalamar on 2006-07-07
Hi,

Since i moved from windows to ubuntu gnu/linux i'm having a problem i can't solve.
If i'm in the location bar or any other xul/gecko input box/textbox the "ctrl+[left|right]arrow" command does not work as expected.
I don't know if it's a bug or a feature, maybe a feature in gnome, because nautilus location bar works the same way.

When i'm in a textbox and do a ctrl+arrow the write cursor moves to the next space or the beggining/end. I.E: "www.firefox.com/download".
If my write cursor is in the end of the string and i do ctrl+left arrow, it goes to the begginin, not to the / as i expect it to work.

Is there any setting in FF or gnome to change this?

thanx!

---

### Post by KhaaL on 2007-10-10
In firefox, type about:config in the adress bar and change **layout.word_select.stop_at_punctuation** to **True**

---

