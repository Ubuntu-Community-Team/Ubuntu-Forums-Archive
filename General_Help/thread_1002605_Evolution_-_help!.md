---
title: "Evolution - help!"
date: 2008-12-05
forum: General Help
---

### Post by cooperised on 2008-12-05
Hi all,

I've broken something.  Evolution fails to start, presenting the generic 'Your system configuration does not match your Evolution configuration.' dialog.  I've tried setting the bonobo server path in /etc/bonobo-activation/bonobo-activation-config.xml as suggested when the 'help' button is pressed, but to no avail.

If it helps, starting from the terminal gives the following output:

```
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:19728): evolution-shell-CRITICAL **: e_shell_set_crash_recovery: assertion `E_IS_SHELL (shell)' failed

(evolution:19728): e-utils-WARNING **: No parent set, or default parent available for error dialog
```

I also read, on another forum, that the command
```
bonobo-activation-run-query "repo_ids.has ('IDL:GNOME/Evolution/Component:2.0')"
``` should return results if the bonobo library path is set up correctly - but it doesn't, and I can't find any documentation on this command.

I've tried reinstalling evolution and evolution-data-server, and removing ~/.evolution and ~/.gconf/apps/evolution, with no success.

Please... can anyone help me get my email back?!

On Ubuntu 8.10 (Intrepid) x64 here.

Cheers
cooperised

---

### Post by mybunche on 2008-12-05
The best I can do for you is that if you have some of the files still on your drive you can save your emails and configuration, follow this procedure in this link. 

[https://answers.launchpad.net/ubuntu/+source/evolution/+question/36491]("https://answers.launchpad.net/ubuntu/+source/evolution/+question/36491")

Then you have to install evolution correctly and I don't have a clue on that. Good luck.

---

