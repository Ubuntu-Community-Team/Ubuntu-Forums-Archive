---
title: "Parts of GTK theme remain when switching them"
date: 2008-05-25
forum: Desktop Environments
---

### Post by crhis on 2008-05-25
I used to use the slickness gtk theme. I followed the instructions [here]("http://gnome-look.org/content/show.php/SlicknesS?content=71993"). One of the steps changes the firefox menu's color so it is legible on the black background. Unfortunately, I switched my GTK theme again and now the text is white, on a white background. Does anyone know how to revert it back to the original color? I have tried reinstalling firefox, and using a new firefox theme.

---

### Post by powerpleb on 2008-05-29
I have exactly the same problem.

---

### Post by Keywil on 2008-06-26
Hats off to LennyX for posting the solution here.

[http://ubuntuforums.org/showthread.php?t=753979&highlight=SlicknesS]("http://ubuntuforums.org/showthread.php?t=753979&highlight=SlicknesS")

I had the same problem but simply altered the $Home/.mozilla/firefox/xx.default/chrome/userChrome.css file to use a color of #00000 instead of #d7d7d7

---

