---
title: "Stuck in Terminal"
date: 2006-09-07
forum: Desktop Environments
---

### Post by GhandiBurger on 2006-09-07
Using this how to to set up Dapper as a server: [http://howtoforge.com/perfect_setup_ubuntu_6.06_p3]("http://howtoforge.com/perfect_setup_ubuntu_6.06_p3")

When I finish editing /etc/network/interfaces and press escape to stop inserting text, I cannot exit the document. and the only way I casn get to the command line is to hit /. I tried doing /etc/init.d/networking restart but that didn't work. any help?

---

### Post by etank on 2006-09-07
This may be a dumb question but are you editing the file as root? If not the you will have to use ```
sudo vi /etc/network/interfaces
```If you try to edit the file as a normal user then it will complain because it is read only to you.

---

### Post by GhandiBurger on 2006-09-07
Yeah, I am editing as root. I can edit the document fine, but I cannot exit from it.It is being edited in the terminal if that helps.

---

### Post by hanzomon4 on 2006-09-07
Try this 
1. Hit the Esc key
2. Then press : x (no space, I just had to put a space because it triggers this :x)

---

### Post by jISh on 2006-09-07
Just type ZZ (yes, capitals). Writes the file and exits.

For the record, you can execute shell commands from vi, with :! followed by the command.

---

### Post by hanzomon4 on 2006-09-08
vi is the same as vim right?

---

### Post by AZzKikR on 2006-09-08
IIRC, executing vi will automatically execute vim. 

In reality, vi and vim are quite different from each other!

---

