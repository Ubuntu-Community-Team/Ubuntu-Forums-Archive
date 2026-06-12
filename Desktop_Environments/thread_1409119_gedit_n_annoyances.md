---
title: "gedit \n annoyances"
date: 2010-02-17
forum: Desktop Environments
---

### Post by Wokzombie on 2010-02-17
Recently I've been learning C, my text editor of choice is gedit.

When you want to tell C that your string of text needs to go on a new line you type *\n*.

Last night I completely forgot about it and didn't close a lot of the text with *\n* so everything ended up in one line when I ran the code. (Actually the book told me to do it ;))
Then I went to the search & replace function in gedit and told it to replace every instance of *")* with *\n")*.
What gedit did was search for every instance of *")* and actualy put it in a new line IN the editor, like I pressed enter, not what I wanted.

So I was curious what happened if I did it the other way around.
If I search for every instance of *\n*, the editor doesn't look for the actualy text, but it shows me every place I pressed enter instead.

Does anyone maybe know if this is supposed to happen and if I could maybe fix it? Because for the rest I really love it as an editor to learn with.

**[**edit**]** I'm talking about gedit 2.28.0 in Karmic if it matters.

---

### Post by BbUiDgZ on 2010-02-17
> **Wokzombie said:**
> Recently I've been learning C, my text editor of choice is gedit.

When you want to tell C that your string of text needs to go on a new line you type *\n*.

Last night I completely forgot about it and didn't close a lot of the text with *\n* so everything ended up in one line when I ran the code. (Actually the book told me to do it ;))
Then I went to the search & replace function in gedit and told it to replace every instance of *")* with *\n")*.
What gedit did was search for every instance of *")* and actualy put it in a new line IN the editor, like I pressed enter, not what I wanted.

So I was curious what happened if I did it the other way around.
If I search for every instance of *\n*, the editor doesn't look for the actualy text, but it shows me every place I pressed enter instead.

Does anyone maybe know if this is supposed to happen and if I could maybe fix it? Because for the rest I really love it as an editor to learn with.

**[**edit**]** I'm talking about gedit 2.28.0 in Karmic if it matters.

i'm not 100% as my ubuntu box is at home and i'm at work atm. But i'm pretty sure gedit has a language format for code so if you pick another format it may or may not line break every \n

try and pick just plain text as the format

---

### Post by Wokzombie on 2010-02-17
Pretty stupid of me, I didn't even think of trying it out in plain text mode.
But it didn't work, gedit does the exact same.

Pretty strange for something like that to be a feature.
Well, if it really **is** a feature and not a bug there will probably be very good logic behind it, but as far as I can see it it's just strange.

---

### Post by mcduck on 2010-02-17
> **Wokzombie said:**
> Pretty stupid of me, I didn't even think of trying it out in plain text mode.
But it didn't work, gedit does the exact same.

Pretty strange for something like that to be a feature.
Well, if it really **is** a feature and not a bug there will probably be very good logic behind it, but as far as I can see it it's just strange.

I's say there is a logic behind it, since I've intentionally used that feature to add/remove new lines and fix files with broken control characters or otherwise bad formatting.

I must say I've never even thought that it would become a problem, but after seeing this thread it seems that it might be a good idea to have a checkbox in the search/replace tool (or somewhere) to enable/disable control characters in search strings.. :)

edit: I found a solution for you. Gedit supports using '\' as escape character, so you just need to use '\\n")' as your replace text instead of '\n")'

---

### Post by Wokzombie on 2010-02-17
> **mcduck said:**
> Gedit supports using '\' as escape character, so you just need to use '\\n")' as your replace text instead of '\n")'

Awesome, that worked. Thank you ^^

---

