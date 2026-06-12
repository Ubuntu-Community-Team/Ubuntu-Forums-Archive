---
title: "Install Pop Shell Window Tiling Extension On Ubuntu"
date: 2020-07-18
forum: Desktop Environments
---

### Post by nikiubu2020me on 2020-07-18
i have Install Pop Shell Window Tiling Extension On Ubuntu 20.04
With these commands :

sudo apt install node-typescript make git


git clone [https://github.com/pop-os/shell](https://github.com/pop-os/shell)

cd shell

./rebuild.sh
But because I already had the git installed
The shell folder was created in my Home directory
My Home partition is separate from the root partition
But at the end of the installation I encounter this error



---------------------------------------------Please help-----------------------------
[COLOR=#000000]+ make enable[/COLOR]
[COLOR=#000000]UUID is "pop-shell@system76.com"[/COLOR]
[COLOR=#000000]gnome-extensions enable "pop-shell@system76.com"[/COLOR]
[COLOR=#000000]+ make restart-shell[/COLOR]
[COLOR=#000000]UUID is "pop-shell@system76.com"[/COLOR]
[COLOR=#000000]echo "Restart shell!"[/COLOR]
[COLOR=#000000]Restart shell![/COLOR]
[COLOR=#000000]if bash -c 'xprop -root &> /dev/null'; then \[/COLOR]
[COLOR=#000000]busctl --user call org.gnome.Shell /org/gnome/Shell org.gnome.Shell Eval s 'Meta.restart("Restarting Gnome...")'; \[/COLOR]
[COLOR=#000000]else \[/COLOR]
[COLOR=#000000]gnome-session-quit --logout; \[/COLOR]
[COLOR=#000000]fi[/COLOR]
[COLOR=#000000]Failed to set address: No such file or directory[/COLOR]
[COLOR=#000000]make: *** [Makefile:69: restart-shell] Error 1[/COLOR]

---

### Post by emanlluf on 2020-07-23
just download the zip file {https://github.com/pop-os/shell/archive/master_focal.zip} instead of git clone and then ./rebuild.sh

---

