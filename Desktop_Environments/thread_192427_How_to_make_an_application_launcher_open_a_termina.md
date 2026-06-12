---
title: "How to make an application launcher open a terminal and keep it open?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by rosslaird on 2006-06-08
I have a little script that runs offlineimap, then opens mutt-ng.
I want to run this from the gnome panel, so that when I click the icon a terminal fires up, syncs my imap mail locally, then opens mutt-ng for reading. I have specified "run in terminal" in the properties for this launcher, but the terminal simply flashes open and disappears. How can I keep it open?

Ross

---

### Post by 23meg on 2006-06-08
Put the following line at the end of your script so that it will wait for some kind of user input to exit. ```
read
```

---

### Post by rosslaird on 2006-06-08
Thanks for the feedback.
So the problem seems to be the script, and since I'm not too familiar with how to write them I suppose I've done things not quite right.

This is the entire script:

offlineimap -u TTY
muttng

Adding "read" at the end did not resolve the launch problem.
The script works perfectly in a terminal that is already open.

Ross

---

### Post by 23meg on 2006-06-08
There are other ways to accomplish this; [here]("http://ubuntuforums.org/showthread.php?t=33955") is where I asked the same question and learnt them. See if they help you.

---

