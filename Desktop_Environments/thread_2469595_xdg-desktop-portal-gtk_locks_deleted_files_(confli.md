---
title: "xdg-desktop-portal-gtk locks deleted files (conflicting with VeraCrypt)"
date: 2021-12-03
forum: Desktop Environments
---

### Post by jfitservices on 2021-12-03
Hi all,

I have a strange phenomenon here. Regularly working with VeraCrypt containers for confidential data works for the most part, but whenever I delete a file inside a VeraCrypt container, I won't be able to unmount it later as VeraCrypt claims the volume is still busy. This does not resolve even if I tell the desktop to empty all trashcans. **lsof** reveals that a process called **xfg-deskt** (actually: xdg-desktop-portal-gtk) has multiple locks open on any deleted file inside the **.Trash-1000** folder of the container. One is the root thread (or task) as it seems, and more threads (or tasks) have established their own locks (among them: **gmain, gdbus, dconf\x20, xfg-deskt **itself**, pool-/usr**)
The only way to dismount the container is to run lsof, reducing the result to anything that points towards the VeraCrypt volume in question, and then killing the process by the root PID previously retrieved. This will immediately let me dismount the container, and until now never had any side-effects besides being annoying.
So the question is how can I tackle this behavior? Why are deleted files getting locked anyway? They are never locked for a different reason such as being edited or new files created. I mean I could understand if the files locked are still open in some application but in my case that's never the case.
I would really appreciate any clues here. Hope I have not cross-posted or repeated the same issue from somebody else but so far I could not find any result on this specific issue.

Here is some information about the system used, maybe it helps:


[LIST]
[*]Hardware: Lenovo ThinkPad P50 
[*]Ubuntu 20.04.3 LTS amd64 
[*]Gnome 3.36.8 
[*]X11 Windowing System 
[*]Keeping updated automatically with Canonical updates as well as apt update / upgrade daily 
[*]VeraCrypt version 1.24-update7 
[*]VeraCrypt containers are on a LUKS-encrypted partition that is unlocked at logon time 
[*]File Managers: nautilus and Ubuntu files, both cause the same issue 
[/LIST]

Thanks everbody! :KS

Cheers,
Joe

---

