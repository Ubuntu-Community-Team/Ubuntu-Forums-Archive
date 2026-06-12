---
title: "garbled text in firefox (ibex)"
date: 2009-02-05
forum: Desktop Environments
---

### Post by felixnine on 2009-02-05
running ibex, nvidia ti4200 ("version 96" drivers as ubuntu tells me), compiz. it's even happening in the text box as i type this. i'm willing to bet it's an nvidia/compiz issue, but i have no idea where to even begin looking.

---

### Post by gettinoriginal on 2009-02-05
Try this:

System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full.

---

### Post by felixnine on 2009-02-05
thanks for the quick reply, but it didn't work. i should probably mention that it comes and goes as i scroll the page and on certain pages, it doesn't happen at all.

---

### Post by gettinoriginal on 2009-02-05
Is compiz working otherwise?  Have you checked System, Preferences, Appearance, Visual Effects to make sure it is set to Extra or Custom?  I also find I get better rendering using emerald as my window decorator.  If you don't have it, I find "fusion-icon" a helpful tool for switching between window managers and window decorators.

---

### Post by vontrapp on 2009-03-15
I also get the same behaviour. I went to the website in the screenshot and didn't get it there, but I see the same type of text randomly on different webpages. It seems to usually happen on changing fonts, maybe even largely fixed width, but I haven't done any sample analysis. It also clears up if you select the text, and will usually reappear when changing tabs or focusing other windows. It's very strange and it never happened before upgrading to 8.10.

---

### Post by vontrapp on 2009-03-15
I did some more poking around, and I'm reasonably certain the problem only occurs on fixed width fonts.

---

### Post by vontrapp on 2009-03-17
I just ran into the problem in GVim as well. I suspect the same issue is at play. Perhaps it's a bug in some font rendering lib?

---

### Post by orengolan on 2009-03-27
I am having the same issue.

I tried running this:
sudo dpkg-reconfigure fontconfig-config
and entered 'no' for bitmap fonts but it didn't help.

---

### Post by pluckypigeon on 2009-05-14
i have this problem as well

I can't even see this comment box

---

### Post by arikkfir on 2009-11-29
This happens to me too - using Ubuntu 9.10 fully updated on a T61 ThinkPad with an Nvidia card, using the nvidia 185 driver.

Usually if I open gedit or any big text-area software, scrolling garbles the text. Selecting it usually fixes it (probably because it re-renders it or something).

This is a major pain, since scrolling happens all the time... :(

---

### Post by pluckypigeon on 2009-11-29
> **arikkfir said:**
> This happens to me too - using Ubuntu 9.10 fully updated on a T61 ThinkPad with an Nvidia card, using the nvidia 185 driver.

Usually if I open gedit or any big text-area software, scrolling garbles the text. Selecting it usually fixes it (probably because it re-renders it or something).

This is a major pain, since scrolling happens all the time... :(

I believe that this is a slightly different problem. What graphics card do you have??

---

### Post by arikkfir on 2009-11-30
> **pluckypigeon said:**
> I believe that this is a slightly different problem. What graphics card do you have??

It's an nvidia card:> nVidia Corporation Quadro NVS 140M according to lspci...

---

