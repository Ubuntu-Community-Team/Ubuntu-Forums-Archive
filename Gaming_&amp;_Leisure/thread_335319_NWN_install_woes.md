---
title: "NWN install woes"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by ceno-byte on 2007-01-10
hello all i recently did a clean install of ubuntu 6.10 on my computer. i went to install neverwinter nights diamond following Leechs guide but when i get to the part that asks for the destination where NWN will be installed. i enter my home directory /home/steve but then it gives me this error:

-en Enter the install directory. (/usr/local/games/nwn): 
/home/steve/Games
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/steve/Games

how is this possible being that im installing to my home directory i would greatly appreciate any help with this issue

---

### Post by pay on 2007-01-10
try ```
chown 755 /home/steve/nwn.sh
```

---

### Post by po0f on 2007-01-10
ceno-byte,

```
[FONT="Courier New"]sudo dpkg-reconfigure dash[/FONT]
```
Answer 'No'.  IIRC this was covered in the guide, did you read it all the way through?

---

### Post by ceno-byte on 2007-01-10
thnxs for the help guys but i fixed the problem when i entered the code "sudo dpkg-reconfigure dash" i kept clicking yes instead of no when i clicked no this time around the installer worked and installed the game with no problem thnxs for the help though.

PROBLEM SOLVED:SELF HELP

---

