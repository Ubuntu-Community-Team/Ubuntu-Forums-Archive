---
title: "[SOLVED] pressing return in gnome-terminal causes system bell"
date: 2008-12-21
forum: General Help
---

### Post by tartley on 2008-12-21
Pressing the return key in gnome-terminal (terminal) just causes a system beep (which is indicated by a visual bell). The command-line I'm typing is not executed.

If I press Ctrl-Return, then the command is executed as normal.

What have I done? Any clues much appreciated. Many thanks,

  Jonathan

--
[email]tartley@tartley.com[/email]

---

### Post by sandyd on 2008-12-21
have you setup your keyboard type correctly?

---

### Post by tartley on 2008-12-21
Yes thanks, it works fine in all other applications. Just gnome-terminal is affected.

Obviously I'm looking at the config for that application but haven't seen anything yet.

---

### Post by drs305 on 2008-12-21
In gnome-terminal there is an option in Edit, Profiles, General for a 'terminal bell'. Is that disabled and causing the beep? According to the online Help, you tick it to disable the bell, which seems backwards. Maybe just change from whatever is there.

---

### Post by tartley on 2008-12-21
Thanks drs305. I tried toggling that. With it unchecked, then pressing return doesn't cause a system beep / visual bell, but the command still doesn't get executed. It just sits there, as though I hadn't pressed return at all.

Ctrl-Return still works as I would expect Return to work.

Ohdear. :-)

---

### Post by tartley on 2008-12-21
Aha! It's not just gnome-terminal! It also happens in xterm!

Other applications (firefox, etc) it works fine.

So presumably it's actually something to do with by bash session!

I'll keep digging.

---

### Post by tartley on 2008-12-21
Solved it.

It was something to do with my .inputrc.

I recently svn updated to my standard .inputrc file, which looked identical, but apparently it had DOS line endings in it (I had been using it on Cygwin under Windows)

changing the file line endings to unix (I loaded it in gvim and did a

 :set fileformat=unix

then resave. All good now. Hooooray!

---

