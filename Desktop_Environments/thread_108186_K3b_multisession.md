---
title: "K3b multisession"
date: 2005-12-25
forum: Desktop Environments
---

### Post by Jagunço on 2005-12-25
Does K3b actually support multisession?
I'm having some problems trying to write multisessions cds with K3b. When I try to add a session to a cd (even if recorded with K3b in the first time) I get some "funny" results. If I try to add files to an existing folder in the cd, the result is a cd with __two__ folders with the same name (one of them capitalized), and not a sight of the new files.
Thanks for the help and happy new year.

---

### Post by noigeaR on 2005-12-25
what's the version number of your k3b?
if it's below 0.12.7 you can get this newer version from the backports. this might fix your problem.

---

### Post by Jagunço on 2005-12-25
The version is 0.12.7. I'm using Kubuntu 5.10.
I'm not sure, but I think everything was all right before I use Automatix. Is that somehow related?

---

### Post by noigeaR on 2005-12-26
i haven't used automatix so i can't tell you if there's a problem with automatix and k3b.
just to make sure you correctly add the second session. you burn the cd as multisession, then when you want to add another session, you open k3b. then you select a new data cd project. then you have the empty window where you can drag and drop the files you want, right?
now for the important part. **import the old session.** push the import button next to the burn cd button (it's the blue gear symbol to the right of the burning cd symbol). select the previous session and the files and folders from the old session should appear in grey color on the screen. newly added files and folders are displayed in black color. if you drag and drop a folder that already exists in the old session, a dialog should pop-up and ask you if you want to overwrite or ignore existing files. at least that's what it does for me.
if this doesn't work for you, try to use the setup assistant again (you will need your admin password for this).

---

### Post by Jagunço on 2005-12-26
Yes, I did all the procedure you described.
I installed NeroLinux demo just to test, and all worked perfectly. I´ll try to remove K3b, mkisofs and all related stuff and install again.
Thanks for the help.

---

