---
title: "HP Printer Drivers"
date: 2010-12-24
forum: Desktop Environments
---

### Post by octocat on 2010-12-24
Hey guys, I recently got a HP Wireless D110a printer. I'm using Pinguy OS, which uses Ubuntu 10.10. I went to the HP site and got the linux drivers because the disk does not support linux. I downloaded the drivers and when im running it in terminal it get an error mid way saying i need the python development files. So i go about and download and install them. Run the drivers again, same thing, need python development. What am I doing wrong? What do I do?

---

### Post by bowens44 on 2010-12-24
which package did you install? When I compiled the drivers I had to install python2.6-dev. That resolved the dependency for me.

If I remember correctly there were several dependencies I had to resolve after that.

---

### Post by octocat on 2010-12-24
I just downloaded and installed python2.6 dev and i still have the same amount of dependencies (6)

---

### Post by bowens44 on 2010-12-24
what are the other dependencies?  I know there were several. I believe that it tells you which ones you need .  the names of the packages listed are not exactly the name they have in ubuntu.

Post the output  that you see in the terminal.

---

