---
title: "Konsole font issues"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Watter on 2005-10-14
The problem is fairly easy to fix, but it's just one of those polish issues that should be correct by default in (K)ubuntu. In any case here are the conditions under whcih it occurred:

Fresh Install of Kubuntu 3.10
AMD64 version
No theme changes
No font changes

The Konsole app appears to be defaulting to the 'Cursor" font. It's not easy to figure this out because when you choose Settings>Font>Custom, the font selector that comes up always has the first font in the list selected, even if that font is not actually being used in the console window. I went through every font in the list until I found the one that matched the default and it was "Cursor". 

The problem is that this font has major, major, display issues (at least in Konsole, anyway). Letters overlap each other constantly. A single | appears at the beginning of many lines of text. The spacing is so bad that there are number of times where it looks like a new word is starting when it actually isn't. 

Anyway, as I mentioned at the top, this is easly fixed by going to Settings>Font>Custom and choosing something different and then selecting Settings>Save as Default, but I hope the packagers (or whoever; I don't really know who's in charge of what) will take note and change the default font to something else, or even better, have console use whatever KDE default monospace font is set to in the KDE System Settings area.

---

### Post by ibanez88 on 2005-10-14
I agree, that font just doesn't look right at all.  Thanks for the fix.

---

### Post by thecrimsonking on 2005-10-15
That was one of the first things I fixed with Kubuntu.

I thought maybe it was just me.

---

