---
title: "glChess on Dapper"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by Virgo53 on 2007-03-19
I just installed glChess (deb pkg). It's listed now in the system's games, but when I click to open it
nothing happens. :confused: 
 Has anyone else have/had this problem? Any ideas on resolving this would be truly appreciated!

---

### Post by raja on 2007-03-19
Have not tried it. But a good way to troubleshoot is to run it from the terminal. Open a terminal and type glchess. You should be able to see if there are any errors.

---

### Post by Virgo53 on 2007-03-19
Okay- I tried to run it from a terminal and got an ImportError: No module named glchess.main
Does the game need a reinstall?  :confused:

---

### Post by raja on 2007-03-19
Yes. I would think so.

---

### Post by Virgo53 on 2007-03-19
I reinstalled glchess but it still won't open by clicking on it in games and still get the same ImportError: no module named glchess.main in terminal. :confused:

---

### Post by cor2y on 2007-03-20
i got it to run
but i had to install a chess engine like gnuchess to get a pc vs user game going.

Before installing follow directions for ubuntu on the site exactly.
remember to add sudo before all the terminal cmds listed on th page.

[http://glchess.sourceforge.net/?q=node/7](http://glchess.sourceforge.net/?q=node/7)

---

### Post by Virgo53 on 2007-03-20
I got the problem resolved- I had the Edgy/Feisty deb version 1.0.4-1installed.
According to Robert Ancell (the program's developer) the last version for Dapper
was 1.0.1-1. Here's how I fixed it: First, I did a search in Synpatic for glChess
and after it located 1.0.4-1 I had Synpatic completely remove it. Then I downloaded
package `glchess_1.0.1-1dapper_all-1.deb`  from Sourceforge.net.
The idebi package installer handled the pain-free installation! I already had
gnuchess running on xboard, so glChess now runs w/o any problems!!
Thanks to all the replies everyone!


:guitar:

---

