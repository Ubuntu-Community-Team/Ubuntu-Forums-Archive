---
title: "How do I set Codepage 437 in konsole?"
date: 2007-07-14
forum: Desktop Environments
---

### Post by eroper on 2007-07-14
Hi folks,

I'm trying to get codepage 437 support under Konsole. Settings->Encodings has quite a few to choose from, but for whatever reason there's no cp-437. Any ideas where Konsole gets its list of supported codepages, and/or what I'd need to do to get it there (if possible)? In the mean-time I've been using ibm850 and the terminus-dos font (a cp437 font), but it certainly isn't a perfect replacement.

Alternatively, anyone aware of an X terminal emulator with (near) full ANSI support (not just ANSI-colors) that does support cp437?

As a side note for anyone else that might be trying to do the same thing &#8211; or something similar &#8211; I did manage to get the Linux console back into cp-437 friendly mode with the following:
```

unicode_stop
consolechars -m cp437 -f /usr/share/consolefonts/default8x16.psf.gz

```

Thanks in advance!

---

