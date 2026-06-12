---
title: "different default applications when opened from dolphin vs. folderview"
date: 2015-06-22
forum: Desktop Environments
---

### Post by rybnik on 2015-06-22
I'm going to use .odt files as an example here, but this problem occurs for more filetypes than just that.

When I open an .odt file from Dolphin (or Thunar, for that matter), it opens in LibreOffice Writer.
When I open the same .odt file from a Folderview Screenlet, it opens in AbiWord.

However, I want the settings for preferred applications to be universal.  I want an .odt file to open in LibreOffice Writer regardless of how I open it.

Any help?  Thanks.

---

### Post by flocculant on 2015-07-02
Does not right clicking on an .odt and setting the Open With in Properties > General not work?

---

### Post by rybnik on 2015-07-03
The issue is that the "open with" menu in the folderview screenlet does not give that option.  (screenshot [here]("http://i.imgur.com/zgi3aTa.jpg"))

---

### Post by rybnik on 2015-07-19
bump

---

### Post by flocculant on 2015-07-20
That's odd looking, I assume that Dolphin is mucking that about.

Though it is showing LO Writer as the default application.

You should be able to set this in Settings > MIME Type Editor

If you're not actually using Abiword - what happens if you purge Abiword?

---

### Post by rybnik on 2015-08-13
[quote=flocculant]
You should be able to set this in Settings > MIME Type Editor[/quote]
All the relevant settings in MIME Type Editor are set to LO Writer, and yet when I open a word file through a folderview screenlet, it nonetheless opens in Abiword.

[quote=flocculant]If you're not actually using Abiword - what happens if you purge Abiword?[/quote]
Well yes, then the word files would be forced into opening through LO Writer.  However, as I stated in the initial post, this problem does not pertain to ONLY word files.

---

