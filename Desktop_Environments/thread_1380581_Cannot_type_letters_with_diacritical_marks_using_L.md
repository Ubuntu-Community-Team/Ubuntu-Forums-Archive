---
title: "Cannot type letters with diacritical marks using Latvian keyboard layouts"
date: 2010-01-13
forum: Desktop Environments
---

### Post by anagor_lv on 2010-01-13
[FONT=Verdana]I have added a Latvian keyboard layout to my Ubuntu 9.10 system (Russian as the system language). I cannot type Latvian letters with diacritical marks. I chose an apostrophe-based keyboard layout, so that I get the letter I need by pressing an apostrophe before. For example, to get &#257;, I would press 'a.

The problem is, when I press ' followed by a letter or space bar, nothing appears on the screen. I continue typing as normal, but each time I press an apostrophe, the next character I press displays nothing on the screen. 

Here is what I tried doing:

I have tried installing a Latvian language pack through [/FONT]   [FONT=Verdana]*System -> Administration -> Language Support*. It was generally a useful addition. But it did not solve the problem. I still could not type Latvian. After that, I tried removing the Latvian layout from settings and adding it again. It did not help. I tried removing the layout, restarting my computer, and adding the layout back. The problem was not resolved.

I have tried different Lativan layouts (with tilde, with F, and standard). I had the same problem regardless of the layout I used. 

I browsed dozens of forum threads, and in one of them I found a workaround for this problem. For example, to type Š, I hold down Shift and Control together, and while holding them press u0160 (because 0160 is a hex code for Š in the character map). The first 0 is not significant, so to save time I type u160. I looked up the hex codes for the letters I need in [/FONT]  [FONT=Verdana]*Applications -> Accessories -> Character Map*. In that application, at the bottom of the window, for each letter there is a code U+(four hex digits) e.g. U+012A. I wrote out all the codes I need on a small paper slip and stuck it to my monitor.

Entering symbols this way is rather inconvenient. But at least it is possible.

How to enter Latvian letters using just a Latvian keyboard layout? Is it a bug I should file? Would be great to find out. ;)[/FONT]

---

### Post by anagor_lv on 2010-02-05
I have found a solution to my problem.


 To enter Latin characters with macrons, cedillas, etc, you should enable a Compose key.


 1) Go to: ***System*** --> **Preferences** --> **Keyboard**.
2) Select the **Layouts** tab
3) Click the **Layout Options** button
4) Under the option "**Compose key position**", select any key you prefer. I selected **Right Win**.
5) Now, to type &#257;, press Right Win, -, a;
   to type š, press Right Win, <, s;
   to type &#311;, press Right Win, comma, k.


 Now, I might as well disable the Latvian keyboard layout. I can enter Latvian text using a standard English USA layout. And not only in Latvian, but also in French, German, Spanish, etc


 I suppose the problem is caused by a bug, which makes it impossible to enter letters using the normal keyboard layout.

---

### Post by veidelis on 2010-02-11
Thank you very much for this thread. It helped a lot.

---

### Post by anagor_lv on 2010-02-17
Thank you for the feedback, Veidelis! I am glad to hear that it helped.

---

### Post by anagor_lv on 2011-02-21
Using a compose key is ok, but in this case some key combinations may not work correctly.

Here is how to solve the problem:
[http://ubuntuforums.org/showthread.php?t=1565339](http://ubuntuforums.org/showthread.php?t=1565339)

---

