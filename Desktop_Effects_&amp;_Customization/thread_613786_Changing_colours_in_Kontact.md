---
title: "Changing colours in Kontact"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by poebae on 2007-11-15
Simple problem:

I'm using a grey/black theme in Kubuntu 7.10, but some applications don't play nice, and try to use ugly blue fonts against dark backgrounds. I've tried looking in the configuration but couldn't change the text in question.

If you look in the screenshot attached, you'll see the blue text in question on my summary page. The same text is used in the to-do list. I've tried changing the text colour for hyperlinks, but that didn't make a difference.

Thanks in advance for your help.

---

### Post by pointfivezero on 2007-12-01
Hi there,

 To return the link colour to the system-wide setting in kontact,  edit your ~/.kde/share/config/kontactrc file and _remove_ then save the line:

```

linkColor=0,0,255

```

NOTE:  You may also wish to set this to an arbitrary Red, Green, Blue value... 

PS:  I discovered your post when I had a similar if not exact same issue when loading a kontact or outlook 'style' profile, someone has written a bunch of what seem to be hard-coded overrides.very naughty indeed!

I hope this helps.

---

### Post by justinchudgar on 2008-04-05
Thanks!

---

