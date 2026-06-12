---
title: "File Manager &quot;type to select&quot; broken"
date: 2009-05-13
forum: Desktop Environments
---

### Post by mjrmua on 2009-05-13
Normally when I have a Nautilus file manager window open and start typing, the file manager will select the first file whos name matches what I've typed (what's this feature called anyway?)

A couple of days ago this feature stopped working, not sure what caused it but can anyone suggest how I can get it back?

thanks,
Murray

---

### Post by drs305 on 2009-05-13
I was able to reproduce your problem by changing the following key from the default setting. Of course there could be other reasons as well, but check this:

Open up gconf-editor and "unset" this key if it doesn't read "search_by_text". You unset by right clicking the "search bar type" preference.

```

gconf-editor /apps/nautilus/preferences/search_bar_type

```

---

### Post by mjrmua on 2009-06-09
Thanks for the advice,

It turns out it was already set to search_by_text, but if I changed it to search_by_text_and_properties then back to search_by_text it started working again.

I'm happy, but no idea what caused it to break in the first place...

---

