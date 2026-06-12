---
title: "[SOLVED] shortcut doesn't work"
date: 2009-01-07
forum: General Help
---

### Post by PGScooter on 2009-01-07
Hi,

I'm using xubuntu and I want to have a shortcut that allows me, after pressing ctrl-c to copy something I see on firefox, to append the copied thing to a file. The command works from the terminal, but not when I assign it a shortcut in xubuntu (by going to applications>settings>settings manager>keyboard>shortcuts )

I have done other shortcuts that work just fine.

Anything else I could try?
Here is the code:
```
xclip -o >> /home/james/archive.txt
```

and I use ctrl-alt-s to call it.

thanks

---

### Post by phisher1 on 2009-01-07
Long shot, but perhaps supply full path to xclip

---

### Post by bc90021 on 2009-01-07
Another long shot, but check the permissions on both xclip and the file to which you're trying to append.  If all else fails, try it with "sudo xclip..."

Also make sure the Ctrl+Alt+S key binding isn't assigned to something else.

---

### Post by PGScooter on 2009-01-07
thank you both for the good suggestions. I tried the full path, but that did not change anything (but again, it works fine in the terminal). I checked permissions and they seem fine to me, and I tried it with sudo and that did not work either (although I do not know if you can do shortcuts with sudo... can you?)

any other ideas?

thanks

---

### Post by PGScooter on 2009-01-07
I guess I solved it for now:

I put the command in a script and ran
gksudo xfce-setting-show
and then did everything normally to run the bash script and it worked.

I might have done something else as well though. I will have to see if I can replicate it.

---

