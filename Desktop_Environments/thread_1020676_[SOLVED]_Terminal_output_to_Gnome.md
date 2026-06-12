---
title: "[SOLVED] Terminal output to Gnome"
date: 2008-12-24
forum: Desktop Environments
---

### Post by Dale Sexton on 2008-12-24
Is there terminal command from Gnome where one can get the terminal output to a gnome gui?

A for instance: in the terminal you can type 'rhyme test' and get an output of all words that rhyme with test. I want to make gui's that can take terminal commands and retrive the outputs.

---

### Post by Dale Sexton on 2008-12-28
I've tried a couple of approaches with a desktop icon opening the terminal with a sub command and glade 3/autoglade to make a gui, but no avail.

Any one?

---

### Post by Dale Sexton on 2008-12-29
Well, it's kinda like talking to myself. The doctor said I can do that, but it might mean problems if I answer myself. Hmmmm...

Ok. I found a dirty way to do this. Not what I wanted, but it'll work in the interim. The answer is here [http://ubuntuforums.org/showthread.php?t=1024842](http://ubuntuforums.org/showthread.php?t=1024842)

---

### Post by anthro398 on 2008-12-29
I use zenity for something similar.  I have a launcher on my panel that launches a zenity dialog that allows me to configure rsync to a)sync birectionally, b) sync deleting files on my laptop, or c) sync deleting files on my desktop.  When it's finished, a zenity dialog pops up offering to show the output of rsync.  Seems like it'd be very simple to do what you're trying to do with zenity.

---

### Post by Dale Sexton on 2008-12-30
Could you give an example of how you used it in the launcher?

Thanks in advance,

---

### Post by Dale Sexton on 2008-12-31
I did some research...

```

#!/bin/bash

wWord=$(zenity --title "Rhymer" --entry --text "Word to rhyme?");

rhyme $wWord | zenity --title "Rhymer" --text-info

```and the laucher...

```

sh /home/xxx/rhymer.sh

```Man, I like it.

---

