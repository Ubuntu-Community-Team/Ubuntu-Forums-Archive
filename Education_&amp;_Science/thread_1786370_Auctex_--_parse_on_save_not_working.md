---
title: "Auctex -- parse on save not working"
date: 2011-06-19
forum: Education &amp; Science
---

### Post by tekkenlord on 2011-06-19
Hello all,

Could someone please explain to me why the following is happening. I have a latex document which has one equation labeled "eq:1". If I type "\ref{" and then try to autocomplete (C-M-i), then emacs fills in the macro with the correct label, i.e "eq:1".

Now, if I change the label to "eq:2", save the file, and try auto-completion, it still fills in the macro with "eq:1".

In my .emacs file I have the following two lines:

(setq TeX-auto-save t)
(setq TeX-parse-self t)

which, in theory, should update the labels everytime I save the file.

The only way that I have managed to make this work, is to give "C-c C-n" which forces the generation of the style information.

How I can make Auctex update the style information automatically when the file is saved? I thought that this was the whole point of setting "TeX-auto-save" to "t", but I am probably mistaken. If so, what does "TeX-auto-save" do?

Thanks for any suggestions!

---

### Post by perroazul on 2011-06-20
> **tekkenlord said:**
> Hello all,

Now, if I change the label to "eq:2", save the file, and try auto-completion, it still fills in the macro with "eq:1".



the way I deal whit that kind of things is completely different. Any time I install emacs, I install auctex and reftex at the same time. reftex handles all the labels and cross-references and it does it well. It also has functions for parsing the whole document, find repeated labels, and renaming labels as well.

---

### Post by tekkenlord on 2011-06-20
Thanks, but the exact same thing happens with reftex as well. Pressing C-c ) gives me the wrong list of labels; only by refreshing the document (by pressing r) shows the right labels.

---

