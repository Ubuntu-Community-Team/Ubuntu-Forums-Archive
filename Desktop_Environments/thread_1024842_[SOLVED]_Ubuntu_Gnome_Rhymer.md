---
title: "[SOLVED] Ubuntu Gnome Rhymer"
date: 2008-12-29
forum: Desktop Environments
---

### Post by Dale Sexton on 2008-12-29
This is not what I'm looking for, but it was a learning experience. I want a gui rhymer. I know perl, and php, but not so much python, plus I'm a 6 month noobi to Linux.

For a dirty rhymer I used gnome-terminal -x rhyme. I ran into problems using the command because the terminal exited before I could use it. It was running so fast that I thought it was not working at all.

After a lot of searching and researching, I found out gnome-terminal was working, but exiting. The fix:
open gnome-terminal
edit>>profiles>>new
add name
go to new name
edit>>title and command>>when command exits>>hold the terminal open

This left the terminal open. Then I made a launcher from the desktop:
click on the desktop>>create launcher>>type>>application in terminal
in command add 'rhyme -i' (-i keeps rhyme open for multiple uses)
and in name add 'Rhymer' or what ever you want to call it, and click 'ok'.

This puts an icon on your desktop called 'Rhymer' that opens a terminal with Rhyme launched and waiting for a word to rhyme.

This is not limited to rhyme. Try it on other applications.

This will work for now until someone, or myself can make a Ubuntu Gnome gui rhymer.

---

### Post by Dale Sexton on 2008-12-31
Now this is a working!!!

```

#!/bin/bash

wWord=$(zenity --title "Rhymer" --entry --text "Word to rhyme?");

rhyme $wWord | zenity --title "Rhymer" --text-info

```

and the laucher...

```

sh /home/xxx/rhymer.sh

```

---

