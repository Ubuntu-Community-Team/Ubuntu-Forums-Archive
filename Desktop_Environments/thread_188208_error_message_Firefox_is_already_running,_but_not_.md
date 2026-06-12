---
title: "error message: Firefox is already running, but not responding&quot;"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Joda on 2006-06-03
hey,
whenever I try to start firefox using the icon, I get the error message above, and firefox does not start.  I've discovered that I can start firefox using "sudo -H firefox" in a command prompt, but this is less than satisfactory, in the long run :-?

Can anyone tell me what to do to get passed this problem?

Thanks, Jonas

---

### Post by Ramses de Norre on 2006-06-03
Was it running before? killall firefox-bin kills the process so you should be able to run it again then. Check the command for the launcher if it still wont work, /usr/bin/firefox works perfect here.

---

### Post by Joda on 2006-06-03
[QUOTE=Ramses de Norre]Was it running before? killall firefox-bin kills the process so you should be able to run it again then. Check the command for the launcher if it still wont work, /usr/bin/firefox works perfect here.[/QUOTE]

Thank you for your reply.

I've tried the killall, but it says "no process killed". the command for the launcher is the default, and looks to be the right one. I've tried typing /user/bin/firefox in a terminal with the same results.

This is a completely fresh install of Dapper.

/Jonas

---

