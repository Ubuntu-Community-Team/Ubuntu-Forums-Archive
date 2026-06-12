---
title: "Americas Army"
date: 2007-12-02
forum: Gaming &amp; Leisure
---

### Post by RuB3N on 2007-12-02
I am downloading americas army from [www.aaotracker.com](www.aaotracker.com). I am downloading the full version for Linux. Is that all i have to do to get it to run? after i downloads i run it but do i have to download a patch for it or is it all there? And is it like the windows version? the same severs on it and the same training? Or is it completely different?



Thank You For Your Time!!:guitar:




-Ruben

---

### Post by RuB3N on 2007-12-02
Ok if no one has a solution to that please help me here.

When I try to install it the game tryes to write to the file /usr/local/games.  But it gives me this when i try to install it there.



No write permission to /usr/local/games


How do I get permission to install it to that file?



thank you for your time


-ruben

---

### Post by dashnak on 2007-12-02
Try running the installer with "sudo"

---

### Post by RuB3N on 2007-12-02
yes but how do i run it with sudo?

---

### Post by Vadi on 2007-12-02
Do you know how to use the terminal, and the "cd" and the "ls" commands in the terminal?

---

### Post by RuB3N on 2007-12-02
I know how to use the terminal but i dont know how to use all the commands...... the installer has to run in the terminal. its called

armyops250-linux.run


but i have to run it through the terminal with sudo, but i dont know how to do that.

it blocks me from installing because it has to have permission.

---

### Post by hyperchickens on 2007-12-02
just type sudo before your existing commands and it should ask for your password

---

### Post by RuB3N on 2007-12-02
when i run amryops it just blinks in the terminal and disappears.

where did it go?

---

### Post by Monkey77 on 2007-12-03
The exact command would be:

sudo armyops250-linux.bin

You will need to enter your root password then it will then decompress the contents and run the installer.  It might fail if the download was corrupt (I have had that before).

Another thing to check is that the file has execute rights, you can do this with:

chmod -x armyops210-linux.bin

This changes the mode of the bin file to be an executable.

Hope that helps.

---

### Post by de_valentin on 2007-12-03
If that doesn't help check if your file is aprox. 778 MB if not you heven't gotten the full version, I had that the first time round.

I think I got my version from here
[http://treefort.icculus.org/armyops/](http://treefort.icculus.org/armyops/)
here there also is a bit of help
[http://treefort.icculus.org/armyops/](http://treefort.icculus.org/armyops/)

---

### Post by de_valentin on 2007-12-05
Do you have armyops working now?

---

### Post by RuB3N on 2007-12-09
nope... :(  i have no clue how to do it :(

---

