---
title: "vim behaves oddly in xmonad"
date: 2009-05-01
forum: General Help
---

### Post by darthshak on 2009-05-01
I installed Ubuntu 9.04 on my Thinkpad T61 about a week back. I decided to try xmonad for my window manager as I wanted to try a lightweight tiling WM. 

I was able to configure much of it without a hassle, but Vim started behaving very oddly. First off, vim never tells me which mode I am in, which makes for some highly annoying periods during which I have typed a whole line to see that I'm not in insert mode. Secondly, when I press 'Up', 'A' is printed on the screen. Similarly, 'Down' prints B, 'Right' prints C, 'Left' prints 'D'. 

Pressing 'Delete' on a word, the letter on the left of the cursor changes case(lower becomes upper and vice versa). Backspace doesnt respond at all.

vim works just fine under GNOME, but I cant stand working in GNOME any more. Any one has an idea as to what is going on?

---

### Post by taurus on 2009-05-01
Maybe you need the vim-full package.

---

### Post by darthshak on 2009-05-03
I have installed the vim-full package already.

---

### Post by lloyd_b on 2009-05-03
> **darthshak said:**
> I installed Ubuntu 9.04 on my Thinkpad T61 about a week back. I decided to try xmonad for my window manager as I wanted to try a lightweight tiling WM. 

I was able to configure much of it without a hassle, but Vim started behaving very oddly. First off, vim never tells me which mode I am in, which makes for some highly annoying periods during which I have typed a whole line to see that I'm not in insert mode. Secondly, when I press 'Up', 'A' is printed on the screen. Similarly, 'Down' prints B, 'Right' prints C, 'Left' prints 'D'. 

Pressing 'Delete' on a word, the letter on the left of the cursor changes case(lower becomes upper and vice versa). Backspace doesnt respond at all.

vim works just fine under GNOME, but I cant stand working in GNOME any more. Any one has an idea as to what is going on?
What is the output from typing the following in a terminal window:```
echo $TERM
```That "'Up' prints 'A'" etc. business is an indicator that it's not set to the correct terminal type.

Lloyd B.

---

### Post by delcypher on 2009-05-03
You're running vim in compatibility mode. Try running this
```
vim -N [filename]
```

or try using vim and then issuing :set nocp

Hope this helps.

Also as lloyd_b says your terminal may be incorrectly set.

---

