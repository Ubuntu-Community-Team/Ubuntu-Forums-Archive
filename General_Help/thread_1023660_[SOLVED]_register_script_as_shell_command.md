---
title: "[SOLVED] register script as shell command"
date: 2008-12-28
forum: General Help
---

### Post by delta16 on 2008-12-28
lets say i have a python script called "youtube".
For now every time i want to you the script i need to run:
```
$sudo python ./youtube
```

I know that there is a way to register it as a single shell command ( i had it done before ).

so that the script will run with just using a shell command like
```
$youtube
```

As far as i can remember it was something about moving the script to a specific folder.

But witch one , or am i totally wrong ??

Any help with this will be appreciated.

---

### Post by kaivalagi on 2008-12-28
There are 2 things you'll need to satisfy

1) Put the script into a path where it can be found, you should be good with the bin folder under your home folder e.g. ~/bin
If ~/bin doesn't work for you then place the file into /usr/local/bin (you will need root privileges to do this though, i.e. sudo)

2) Make sure the script is executable, this can be done through file properties or using the terminal and running this:

```
chmod +x ~/bin/youtube
```

If the file is in the ~/bin folder, change to suit...

---

### Post by unutbu on 2008-12-28
Along with what kaivalagi suggests, also make sure that 
```
#!/usr/bin/env python
```
is the first line of the python script. This so-called 'she-bang' line is what would allow you to run
```

sudo youtube
``` instead of
```

sudo python youtube
```

---

### Post by delta16 on 2008-12-28
hey thanx guy's
That really was a quick reply and a full answer to my question.

---

### Post by kaivalagi on 2008-12-28
Glad to be of help

Can you mark the thread as solved if you're happy with that...

Cheers

---

