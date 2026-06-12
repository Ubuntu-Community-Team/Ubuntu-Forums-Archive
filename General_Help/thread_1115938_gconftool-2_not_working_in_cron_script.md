---
title: "gconftool-2 not working in cron script?"
date: 2009-04-04
forum: General Help
---

### Post by Arancaytar on 2009-04-04
I have written a script that randomly cycles my desktop background to one of the pictures I have selected in the gnome-appearance-properties (stored in ~/.gnome2/backgrounds.xml).

The script works fine when called from the shell, but inexplicably fails when run via crontab.

Here it is:

```
#!/bin/bash
# workaround: crontab doesn't execute ~/.profile; extend the PATH manually.
PATH="$HOME/bin:$PATH"
# debug: log date of execution
date >> "$HOME/wallpaper.log"

# parse backgrounds.xml, read filenames.
# "randline" is a custom script, prints a random line from input.
filename=$(cat "$HOME/.gnome2/backgrounds.xml" | grep '<filename>' | perl -pi -e 's/.*?>(.*)<.*/$1/g' | randline)

# more debug: log new wallpaper filename
echo "$filename" >> "$HOME/wallpaper.log"

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$filename"

```

The first problem was the $PATH variable, but I fixed that so my custom randline script is found as it should be. 

Now whether the script runs from the shell or cron, the debug output is the same, so everything works except for the final gconftool-2 command. What I don't understand is why...

---

### Post by dcstar on 2009-04-04
> **Arancaytar said:**
> 
.........
Now whether the script runs from the shell or cron, the debug output is the same, so everything works except for the final gconftool-2 command. What I don't understand is why...

Any graphical program run in cron requires the screen to be explicitly specified.

---

### Post by Arancaytar on 2009-04-05
By graphical program, do you mean a program that launches a window? gconftool-2 is a non-interactive command-line utility...

---

### Post by msegmx on 2009-04-30
@Arancaytar

were you able to solve this problem ?
I also try to run a script like yours, but it fails to run gconftool-2, too.

Also, the script ran on Hardy, but it fails on Jaunty.

[http://trishankkarthik.blogspot.com/2005/12/howto-randomly-cycle-wallpapers-with.html]("http://trishankkarthik.blogspot.com/2005/12/howto-randomly-cycle-wallpapers-with.html")

---

