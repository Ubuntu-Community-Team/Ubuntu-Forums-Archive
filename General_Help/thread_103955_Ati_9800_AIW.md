---
title: "Ati 9800 AIW"
date: 2005-12-15
forum: General Help
---

### Post by freagel on 2005-12-15
Is there anyone who has succes in making the tv-tuner to work with this card? I really have no clue. Tried several things and hoped that the gatos package would work. Now i get this output running atitv -c 1.

GATOS: No ATI PCI/AGP Cards ?
GATOS: gatos_inita(): Invalid argument
Segmentation fault

Any ideas?

---

### Post by mike4ubuntu on 2005-12-15
Video capture however is not supported for the ATI Radeon AIW cards according to this ati linux driver release notes:

[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)

I tried GATOS also with no luck in Ubuntu Hoary.  I did however manage to get my Radeon 8500 AIW TV Tuner working with GATOS in Mandrake 10.1

I Keep waiting for the ATI  fglrx driver to support the video4linux standard api, but it doesn't look like it's going to happen anytime soon.

---

