---
title: "Synaptic Package Manager is broken"
date: 2006-06-08
forum: Desktop Environments
---

### Post by spymaster on 2006-06-08
Hey, I hope this is the right forum for this.  I just installed Ubuntu 6.06 and I was trying to change the repositories settings to include universe and multivers.  I copied and pasted a repository from the Ubuntu wiki, but I didn't get the whole line, which caused an error when loading the program.  It was having a problem with the sources.list file, so I tried to just go into the file and delete the line that was messed up, but it's a root file so I wasn't able to change it.  I figured out how to change root files with sudo, so I went into the terminal and deleted the file, thinking I could just use the program and it would create a new file, but now it doesn't seem to work at all.  Can I just create a new sources.list file and put it in the folder?  If so, how?  If that's not the answer, what should I do?

---

### Post by RavenOfOdin on 2006-06-08
Does it say something like "Software index is broken"?

I think creating a new file should work.  There's no reason for it not to.

---

### Post by spymaster on 2006-06-08
So how do I do that?

---

### Post by nix4me on 2006-06-08
sudo gedit /etc/apt/sources.list


then paste in the correct repositories and save.

nix4me

---

