---
title: "Gdesklets"
date: 2006-11-27
forum: Desktop Environments
---

### Post by ZERO_SHIFT on 2006-11-27
I am having problems with saving my session.

When I do save my session and reboot ubuntu Gdseklets doesn't start automatically, further more I keep on getting the home folder opened when I reboot.

What should I do?

Thanks in advance

---

### Post by Hwoarang on 2006-11-27
Yeah I had that problem , 

can you do the below

sudo nano /etc/init.d/bootmisc.sh 

and post here whatever the file says:)

---

### Post by taurus on 2006-11-27
System -> Preferences -> Sessions.

Then, remove the "Default" session and click the "Startup Programs" and add gdesklets to it.

Log out and back in again...

---

