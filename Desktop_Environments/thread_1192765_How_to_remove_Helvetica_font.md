---
title: "How to remove Helvetica font?"
date: 2009-06-20
forum: Desktop Environments
---

### Post by srikanthsrs on 2009-06-20
There are a few fonts I just don't like, and one of them is Helvetica. I don't like Arial too (on Ubuntu, for some reason I like it on Windows), so I removed it by finding them out like this:

```
find /usr/share/fonts "arial*" -exec rm {} \;
```

But I couldn't find and remove Helvetica using the above way. Anyone knows how to do it?

Thanks!

---

### Post by Bachstelze on 2009-06-20
Actually, the font you think is Helvetica is in fact Nimbus Sans L. Since Helvetica, being a commercial font, is not included in Ubuntu, fontconfig uses Nimbus Sans L as a replacement for it when a website asks for Helvetica, for example.

Run

```
fc-list | grep -i helvetica
```

Nothing should appear here.

---

### Post by srikanthsrs on 2009-06-20
HymnToLife, thanks a lot for that information! But I couldn't find any fonts in /usr/share/fonts or ~/.fonts folder that contains the name "nimbus".

The following command returned nothing:

```
find /usr/share/fonts ~/.fonts -iname "*nimbus*"
```

However, the fc-list command you mentioned, shows the information about the 'Nimbus *' fonts. Do you know the file names of these Nimbus* fonts? I tried googling for it, but I didn't have any luck. Is there a way to remove these fonts?

Thanks!

---

