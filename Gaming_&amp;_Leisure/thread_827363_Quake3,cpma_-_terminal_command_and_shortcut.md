---
title: "Quake3,cpma - terminal command and shortcut"
date: 2008-06-12
forum: Gaming &amp; Leisure
---

### Post by Invaderen on 2008-06-12
Hi everyone.
I installed quake3 for linux using this guide: [http://www.klausharris.de/install_quake_3.php](http://www.klausharris.de/install_quake_3.php)

With quake3 installed, I can execute it from anywhere in the terminal by writing "quake3". Now I have installed the CPMA-modification for quake3 - is there any way so I can write "q3cpma" to execute the quake3 cpma program?

Furthermore, the game will not work if I start it from either a link or a launcher - could that be related to that I can execute quake3 from its directory but not from any other directory (even though the path is correct)? Is there any way to fix it? Outside the Quake3 directory, the program can't see any packet files (pk3's).

Thank you for trying to help!

---

### Post by DoktorSeven on 2008-06-12
Write a script that runs Q3 from its directory:

```

#!/bin/bash
cd /where/Quake/3/directory/is
# of course, you'll actually put the directory path above, not literally what I wrote.
./quake3
# or whatever the launcher name is.

```

And make it executable:
**chmod 755 quake3launcher**
(or whatever you named it)

Then just point a shortcut to it.

For the CPMA, you just use whatever you do to launch that in another script similar to the one above.

---

