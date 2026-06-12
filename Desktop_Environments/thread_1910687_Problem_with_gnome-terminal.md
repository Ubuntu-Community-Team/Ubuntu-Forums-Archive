---
title: "Problem with gnome-terminal"
date: 2012-01-17
forum: Desktop Environments
---

### Post by schizoss on 2012-01-17
Hello,

I got a problem in gnome-teminal,
thr font have changed and look to tight

screenshot:

Thanks

---

### Post by saneearth on 2012-01-17
It appears to be Ariel. Did you per chance change the default system fonts in Settings-Appearance?

---

### Post by schizoss on 2012-01-17
nope, but it started when I accidentally removed the /usr/share/fonts folder.

I recovered it, but still have problems with the fonts

---

### Post by bluexrider on 2012-01-17
looks like it defaulted to system font

---

### Post by mcduck on 2012-01-17
Just set it to use any *monospace font*, either in the Gnome-terminal's profile settings, or using gnome-tweak-tool or ubuntu-tweak to set your default monospace font to one that actually *is* monospace.

(the "too tight" look is because the font currently in use isn't a monospace one but instead a variable-width font. Command-line interfaces are built as a grid of rows and columns of characters, and therefore require each character to use equal amount of space, otherwise things just won't align correctly.)

---

### Post by schizoss on 2012-01-22
> **mcduck said:**
> Just set it to use any *monospace font*, either in the Gnome-terminal's profile settings, or using gnome-tweak-tool or ubuntu-tweak to set your default monospace font to one that actually *is* monospace.

(the "too tight" look is because the font currently in use isn't a monospace one but instead a variable-width font. Command-line interfaces are built as a grid of rows and columns of characters, and therefore require each character to use equal amount of space, otherwise things just won't align correctly.)
Thx, fixed the problem

---

