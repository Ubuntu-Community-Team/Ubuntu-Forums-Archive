---
title: "I can't find an installed font"
date: 2011-06-09
forum: Desktop Environments
---

### Post by Lucas Malor on 2011-06-09
I opened the [Teletype font]("http://www.dafont.com/teletype-1945-1985.font") with the integrated font viewer and I installed it. Now I want to remove it. I've not only searched in /usr/share/fonts/truetype/ but also in **root**. Where is that damned font?

---

### Post by ajgreeny on 2011-06-09
Why does it need un-installing; it's only 64kb in size, so not wasting any space worth bothering about?  Just ignore it and/or set the default font for whatever is using it at the moment to something else.

You could also just run ```
locate TELETYPE1945-1985.ttf
```and then delete it manually.

---

### Post by neu5eeCh on 2011-06-09
> **Lucas Malor said:**
> I opened the [Teletype font]("http://www.dafont.com/teletype-1945-1985.font") with the integrated font viewer and I installed it. Now I want to remove it. I've not only searched in /usr/share/fonts/truetype/ but also in **root**. Where is that damned font?

Try looking in your home folder? ~/.fonts

---

### Post by Lucas Malor on 2011-06-10
> **VTPoet said:**
> Try looking in your home folder? ~/.fonts
Ah, thank you. I didn't know that GUI "search for files" doesn't search for hidden files by default.

> **ajgreeny said:**
> Why does it need un-installing
Because it's the default for much [.ssa subtitles]("http://en.wikipedia.org/wiki/SubStation_Alpha") I download from a site that do them for English stand-up comedy shows, but I don't like it. I think it's more simple to remove the font instead of edit every .ssa ;)

---

