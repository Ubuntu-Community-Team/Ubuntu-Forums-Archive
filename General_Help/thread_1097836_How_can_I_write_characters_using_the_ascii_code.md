---
title: "How can I write characters using the ascii code?"
date: 2009-03-16
forum: General Help
---

### Post by DeepSeaNautilus on 2009-03-16
Hello, I am using ubuntu 8.04. I want to write characters using the ascii code, like ALT + 56, but I can't. How can I solve this?

---

### Post by LegendofTom on 2009-03-16
How are you doing this? With Bash?

---

### Post by DeepSeaNautilus on 2009-03-16
Yes, I am using bash

---

### Post by jwbrase on 2009-03-16
> **DeepSeaNautilus said:**
> Hello, I am using ubuntu 8.04. I want to write characters using the ascii code, like ALT + 56, but I can't. How can I solve this?

Alt+XXXX is an input method that was originally programmed into DOS and made it's way into Windows. It doesn't work in Linux simply because it's an entirely different system. You can go to System->Preferences->Keyboard, and then to the Layouts tab to see if you can set up a keyboard layout that has the character you want. What character are you looking for?

---

### Post by casaredondo on 2009-03-27
I often use special symbols, like to type "It was 78° today.", using the degree symbol. Couple of others I use regularly.

Anyway, under Windows you'd do ALT+0176 to get the degree symbol, but under Ubuntu that doesn't work.

Here's how to make them. CTRL+Shift+U, then release the U and type in the unicode for the symbol. For the degree symbol it's 00B0 (zero zero b zero).

Here's a Unicode table to find the ones you use.
[http://www.alanwood.net/demos/ansi.html](http://www.alanwood.net/demos/ansi.html)

---

### Post by Agent ME on 2009-03-28
If you set your keyboard to use the "USA International (AltGr dead keys)" mode (under System -> Preferences -> Keyboard -> Layout) then you can use special symbols easily by using the right alt button.
Examples -
é is rAlt+e.
° is rAlt-shift-0-0 (press 0 twice while holding the other buttons).

---

### Post by CatKiller on 2009-03-28
You can also use the [Compose key]("http://en.wikipedia.org/wiki/Compose_key") to generate symbols that aren't included as keys on your keyboard. [Here is a list]("http://www.hermit.org/Linux/ComposeKeys.html") of some Compose key combinations.

---

