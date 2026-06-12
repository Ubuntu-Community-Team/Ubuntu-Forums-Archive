---
title: "i8k help - can I set the temps and have auto fan controll without gkrellm running?"
date: 2008-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gohanssjn on 2008-06-16
I don;t need anything except i8k running all the time, but I need to set better temps.

Can this be done without gkrellm?  I have a Dell XPS m1210 if that helps, and i8k does run fine with gkrellm installed and running.

Thanks!

---

### Post by mtbsoft on 2008-06-23
All you need to do is setup your i8k file to include the daemon option then add i8kmon to your session, it'll run as a daemon in the background doing all you want without a UI.  I have it on mine.

---

### Post by mtbsoft on 2008-06-24
Sorry that was a bit vague, was away from the laptop.

Put the following in your /etc/i8kmon config file...

[I]set config(daemon) 1

set config(auto) 1

set config(0) {{0 0}  -1  39  -1  44}
set config(1) {{1 0}  36 44 41 49}
set config(2) {{1 1}  41 49 46 54
set config(3) {{2 2}  46 128 49 128}[/I]

Then add an entry into your session startup programs to run */usr/bin/i8kmon*

...and don't forget to read up on changing your modules file if necessary.

The config file will start (low) the left fan at 39C and stop it at 36C on AC or start (low) at 44C and stop it at 41C on battery, read the subsequent lines accordingly.

Hope this helps.

---

### Post by motin on 2008-06-27
I put up a guide on how to configure i8k here: [http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

---

