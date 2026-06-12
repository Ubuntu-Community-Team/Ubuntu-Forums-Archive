---
title: "[SOLVED] Auto-save screenshot at a set destination?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by howbag on 2006-08-09
Hey!
I was wondering if it was possible to setup the gnome-screenshot utility (top right corner) so that is auto-saves the pics in a set folder instead of asking about name and location every time I take a snapshot?

If not, any other program I could use?

Thanks for replies! :D

---

### Post by Jagot on 2006-08-09
I'm not sure how customizable that utility is.

You may want to check out the command line utility - gnome-panel-screenshot - may be psosible there:

```
man gnome-panel-screenshot
```

---

### Post by howbag on 2006-08-09
These seems to be the same utility (I wrote the wrong name, sorry), but it has no man page anyhow :p cant seem to configure it any way.

---

### Post by Jagot on 2006-08-09
Aha ok.  I'm at a Windows machine at the moment so I can't work it out from here - someone else will probably be able to help you.

---

### Post by howbag on 2006-08-10
Ok, alright thanks anyway.

---

### Post by ardchoille on 2006-08-10
[http://ubuntuforums.org/showthread.php?t=223758](http://ubuntuforums.org/showthread.php?t=223758)

---

### Post by howbag on 2006-08-10
Wow, the script of yours is  way better than gnome-screenshot, indeed! but it didn't solve the problem of having to type in location and filename for every pic. I want them to automaticly save at /bla/bla/bla with the name screenshot(1), screenshot(2) and so on.
Perhaps it does though, I am quite new at linux and haven't edited the script if that was necessary.

---

### Post by CIZZO20 on 2008-06-02
I know that this post is old but i just found a way to do this and wanted to share

Install Scrot in Ubuntu > sudo aptitude install scrot

Then open gconf-editor

From there go to apps/metacity/keybinding_commands

Change the value of command_screenshot 
from 
> gnome-screenshot
to > scrot 'screenshot-%s.png' -e 'mv $f ~/Pictures/'

Then just use the 'print screen' button to take screenshots and they will be in your pictures folder :)

I don't know what the %s command does but i found it when i was looking for a command to put in hour, minute and second for the screen shots name so that it would always change the name of it by a little but i didn't find what i needed there but it seems like the command %s does the job just as well. 

For more scrot commands this site has some
[http://onlyubuntu.blogspot.com/2008/05/how-to-create-screenshots-via-cli-with.html]("http://onlyubuntu.blogspot.com/2008/05/how-to-create-screenshots-via-cli-with.html")

---

### Post by howbag on 2008-06-17
Maybe old, but I never got it fix'd :) Now I have, this was very nice! Thanks:)

---

