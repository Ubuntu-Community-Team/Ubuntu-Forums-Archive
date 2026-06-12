---
title: "Hindi Keyboard Layout question."
date: 2005-09-08
forum: Desktop Environments
---

### Post by kagashe on 2005-09-08
Hi,

In order to enable Hindi Keyboard support I did the following.
System/Preferences/Keyboard/Layouts
Clicked on "+Add"
Selected "Hindi" in layout.
Clicked OK.

I am keeping "US English" as my default Layout.
When I click both "alt" keys together the layout changes to "Hindi".

When I open gedit I can type in Hindi but there is a problem with some complex characters.

I did a search on Google to get help and found that the layout is almost similar to Indic INSCRIPT Devanagari layout except that top three keys with numerals 3, 4, 5, 6, 7 & 8 are not working in "shift" mode. I have attached the layout to the post.

Here is the Sun website giving various INDIC layouts:
[http://java.sun.com/products/jfc/tsc/articles/InputMethod/indiclayout.html](http://java.sun.com/products/jfc/tsc/articles/InputMethod/indiclayout.html)

kagashe

---

### Post by swamytk on 2005-09-08
Did you try with the "mangal" font (available in windows)? any hints?

---

### Post by kagashe on 2005-09-08
[QUOTE=swamytk]Did you try with the "mangal" font (available in windows)? any hints?[/QUOTE]
 Hi swamytk,

Thanks for responding. It is not a problem with fonts. I know that when I change fonts the complex characters (e.g. "Shri") gets altered.

Actually on the keyboard shown on Sun website and also attached with my post the complex characters "Shra" "Tra" "Dyna" etc could be typed directly by using shift+8 shift+6 shift+5 etc.

But the Keyboard available in Ubuntu 5.04 types the numerals 8, 6, 5 and not these characters.

I also know how to type these characters by using other keys e.g. shift+m+d+j to produce "shra" but my question is "can we alter the keyboard so that shift+3, shift+4, shift+5 upto shift+8 keys are available to type these characters?"

I hope it is clear.

kagashe

---

### Post by anil_robo on 2005-12-22
Just to make things more clear, please see my how-to for Hindi and similar languages here:
[http://ubuntuforums.org/showthread.php?t=102778](http://ubuntuforums.org/showthread.php?t=102778)

---

### Post by Arjunanda on 2006-09-10
> **kagashe said:**
> Hi swamytk,
Actually on the keyboard shown on Sun website and also attached with my post the complex characters "Shra" "Tra" "Dyna" etc could be typed directly by using shift+8 shift+6 shift+5 etc.
...
my question is "can we alter the keyboard so that shift+3, shift+4, shift+5 upto shift+8 keys are available to type these characters?"
kagashe

You can modify the file /etc/X11/xkb/symbols/in by entering those keycodes you wish to produce. I am not an expert with modifying the keyboard layouts, but I have once made one for sanskrit transliteration based on finnish (north-european) keyboard, and it worked perfectly. I think what is needed here is to add the unicode keycodes for the mentioned glyphs in the mentioned file.

I have not yet done this, but I will give it some thought. Please PM me if you have already done this or if you are interested - we could share our keymaps, test them and finally, submit them to indlinux.org and ubuntu developers for the benefit of others.

---

### Post by anantshri on 2008-03-27
any success in this till now i am also interested to know about this.

also is their any script available to convert non legacy ttf fonts to unicode for hindi

---

