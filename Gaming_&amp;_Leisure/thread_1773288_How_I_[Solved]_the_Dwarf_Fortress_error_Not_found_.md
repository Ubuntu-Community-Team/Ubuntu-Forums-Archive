---
title: "How I [Solved] the Dwarf Fortress error: Not found: data/art/curses_640x300.png"
date: 2011-06-01
forum: Gaming &amp; Leisure
---

### Post by gategatebodhisvaha on 2011-06-01
Since I couldn't find any solved threads on this, albeit a closed one without an answer on the archlinux forum I thought I'd post how I solved it here.

The answer was simply to run it with sudo.

I've got a icon in my main menu and for the command I simply wrote sudo sh /path/to/df, and has it running in terminal. If you don't want to run it in terminal try gksudo sh /path/to/df.

Anyways hope it helps someone!

---

### Post by R33D3M33R on 2011-06-02
If you are the only one using the system you should always install custom content to your home folder. You could also **chown** the current installed files and sudo should't be needed.

---

### Post by gategatebodhisvaha on 2011-06-02
Well I did both putting it in home, and chmod 777, and still had no luck. Since others seemed to have this problem as well, I thought I'd put a solution up, as there was no one online.

---

