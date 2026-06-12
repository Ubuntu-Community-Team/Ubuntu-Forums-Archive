---
title: "Deja Vu sans condensed does not appear in AbiWord or OpenOffice"
date: 2009-06-23
forum: General Help
---

### Post by alas-poor-yorick on 2009-06-23
DejaVuSansCondensed.ttf appears in /usr/share/fonts/truetype/ttf-dejavu/, but it does not appear in the drop-down menu for either AbiWord or OpenOffice. How do I fix this? Also, is there a better condensed font to use?

(newbie)

---

### Post by sdennie on 2009-06-23
What's the output of:

```

fc-list | grep -i condensed

```

If you don't see anything, possibly try running:

```

fc-cache

```

And then check again.

---

### Post by alas-poor-yorick on 2009-06-23
The output is:
> DejaVu Serif,DejaVu Serif Condensed:style=Condensed,Book
DejaVu Serif,DejaVu Serif Condensed:style=Condensed Bold Italic,Bold Italic
DejaVu Serif,DejaVu Serif Condensed:style=Condensed Bold,Bold
DejaVu Sans,DejaVu Sans Condensed:style=Condensed Oblique,Oblique
Nimbus Sans L:style=Bold Condensed
DejaVu Sans,DejaVu Sans Condensed:style=Condensed Bold Oblique,Bold Oblique
Nimbus Sans L:style=Regular Condensed Italic
DejaVu Sans,DejaVu Sans Condensed:style=Condensed,Book
DejaVu Sans,DejaVu Sans Condensed:style=Condensed Bold,Bold
Nimbus Sans L:style=Regular Condensed
Nimbus Sans L:style=Bold Condensed Italic


It was the same after I ran the second line. The problem still occurs. What now?

---

### Post by alas-poor-yorick on 2009-06-23
bump?

---

### Post by alas-poor-yorick on 2009-06-28
bump?

---

### Post by fragos on 2009-06-29
When you set font on the toolbar you won't see Condensed as an option. If you do Format-> Character you'll see that for the DejaVu Sans font Condensed will be a Typeface option to select much like Bold or Underline. There was a time when Condensed was handled as a Font and not a Typeface but it hasn't been that way for a while. You can assign Condensed in one or more Styles and access it that way. I highly recommend you become familiar with Styles if you aren't already.

---

### Post by alas-poor-yorick on 2009-06-30
I expected it to be something simple I was overlooking like that. Thanks very much for your help!

---

### Post by daniele80 on 2010-04-28
On Ubuntu 10.04 Lucid Lynx after installing ttf-dejavu-extra they appear on Openoffice,
but they do not work. The size remains the same. :(

---

### Post by fragos on 2010-04-28
I'm still running Ubuntu 9.10 but am using Open Office 3.2 which is what I believe is in 10.4. Condensed used to appear as a separate font. Now Condensed is treated as an attribute in Character formating like bold but doesn't change the appearance in OO. When changing the font in appearances Condensed does work. Very strange and repeatable. Have you filed a bug report?

---

### Post by daniele80 on 2010-04-29
> **fragos said:**
> I'm still running Ubuntu 9.10 but am using Open Office 3.2 which is what I believe is in 10.4. Condensed used to appear as a separate font. Now Condensed is treated as an attribute in Character formating like bold but doesn't change the appearance in OO. When changing the font in appearances Condensed does work. Very strange and repeatable. Have you filed a bug report?

[https://bugs.launchpad.net/ubuntu/+source/ttf-dejavu/+bug/571568](https://bugs.launchpad.net/ubuntu/+source/ttf-dejavu/+bug/571568)

---

### Post by fragos on 2010-04-29
> **daniele80 said:**
> [https://bugs.launchpad.net/ubuntu/+source/ttf-dejavu/+bug/571568](https://bugs.launchpad.net/ubuntu/+source/ttf-dejavu/+bug/571568)

I added comments to the bug with additional information to help locate the problem.

---

