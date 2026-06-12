---
title: "Hanging application executing as a shell script"
date: 2009-01-31
forum: General Help
---

### Post by csete on 2009-01-31
I have a small shell script on my Ubuntu (Intrepid) server machine.  It has a single line:

abcde -p -o mp3:"-m j --vbr-new -V 4 -b 112 -B 160"

Recently, I've found that running this shell script hangs the shell and I have to kill it.  Running the command directly from the command line works fine however.  I know this used to work, so I'm not sure what might have changed.

I'm not sure if it makes a difference, but this is being run via an SSH shell.

Thanks for any insights.
Craig

---

### Post by csete on 2009-01-31
I'm now thinking that the command may be running, but not showing the output.  Any ideas what might be going on here?

---

