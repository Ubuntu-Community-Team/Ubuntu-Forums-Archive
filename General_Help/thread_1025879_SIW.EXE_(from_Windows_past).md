---
title: "SIW.EXE (from Windows past)"
date: 2008-12-30
forum: General Help
---

### Post by Barney on 2008-12-30
When I was using Windows, I often used this file, siw.exe, (not an installed program) to check just about anything that needed to be known about what was in my CP, and what was running.

Has anyone used this siw.exe for Windows, and more importantly does a similar thing exist for Ubuntu-Linux?

I have tried to run siw.exe in WINE, but it tunes up, and does nothing.

---

### Post by amauk on 2008-12-30
hwinfo - it's in the repositories

will tell you absolutely everything there is to know
(even the serial numbers for your CPU & RAM chips !!)

because it kicks out such a large volume of info,
I tend to use the --short flag to get a short version, showing just the basics

```
sudo hwinfo --short
```

---

### Post by Barney on 2008-12-30
amauk,

Thanks a million!

hwinfo & hwinfo --short both we're what I was looking for; and in the looking, I also found lshw which also provides what I wanted.

Having this available is one more nail in the coffin of two other old computers that will be totally Ubuntu shortly.

Thanks, again.

Barney

---

