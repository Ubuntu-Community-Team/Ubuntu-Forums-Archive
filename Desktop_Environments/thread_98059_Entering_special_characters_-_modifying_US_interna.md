---
title: "Entering special characters - modifying US international keymap?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by sander marechal on 2005-12-02
Hello, 

Is there any way how I can modify how I enter special characters in Ubuntu? I am talking about things like é è ë ç etcetera. The way this works (on windows and I had it under Ubuntu 4.10) was to first press the " ' or ` or something (it would not appear) and then the letter where it should be applied to. If it could not be applied to that letter, both single characters would appear. If you just want the ' or " then you'd press space after it.

(ps, does anyone know what this is called? It used to be sticky keys, but that's something different now. I googles my ass off, but without knowing the term to search for I get zip :( )

I turned it off for Ubuntu 4.10 because there were far too much characters it applied to (e.g. ' and s works in U4.10, not in Windows) and it greatly slowed down my programming. Now I'm converting my parents to Ubuntu this weekend and I would like to give them the same keymap as Windows uses for special characters. 

I don't care if I have to create it myself, but please, someone point me in the right direction how I can do this. The keymap under windows is called "United States - International". Ubuntu has one as well, but it has far too much of those sticky-key special characters to be of use to me. I want to remove the one's I don't need.

Thanks in advance!

---

### Post by Cyhatch on 2005-12-02
That's called dead keys. You might want to experiment with (AKA read about) xmodmap & xev; xkb vs. keyboard (of X11).

As an option: you can have English set as your default layout; a layout that has the required keys second; and a "... switches group while pressed" checkbox in the Layout Options.

---

### Post by sander marechal on 2005-12-02
Thank you! Now I finally know what to google for :)

---

