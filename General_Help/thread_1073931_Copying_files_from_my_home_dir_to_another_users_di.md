---
title: "Copying files from my home dir to another users dir"
date: 2009-02-18
forum: General Help
---

### Post by bellboa45 on 2009-02-18
Hello, I am relatively new to linux. I created another user account for one of my roommates to use and start to learn linux. On my desktop I have a linker (link to folder) that point to a folder in my home dir that contains some shell scripts that launch different Doom mods. I would like to copy that linker on to the other users desktop. When I try to use the GUI file manager I get an error saying "permission denied" and the paste option in grayed out so I tried the command. 

sudo cp /home/spencer/Desktop/DoomShellScripts /home/dave/Desktop

Which returns 

cp: omitting directory `/home/spencer/Desktop/DoomShellScripts'

Any ideas? thanks!

---

### Post by mikewu on 2009-02-18
Add the -r flag to recursively copy. It should go into the folder and copy everything correctly.

---

### Post by bellboa45 on 2009-02-18
Thank you, worked fine!

---

