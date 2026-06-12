---
title: "sudo visudo help"
date: 2009-01-07
forum: General Help
---

### Post by Svensk023 on 2009-01-07
Hi,

I am running Ubuntu 8.10 and i am trying to configure my /etc/sudoers file so that terminal will never remember my root password

i typed in 

$ sudo visudo

then i went down to this line

defaults           env_reset

and i added timestep_timeout=0

so now it reads

defaults           env_reset,timestep_timeout=0

afterwards i hit "Esc" key and then entered "wq" to save and quit but its not recognizing the command

any suggestions/corrections?

---

### Post by oldos2er on 2009-01-07
Does your sudoers file open in nano? If so, to save the file, hit Ctrl-X, and choose 'Yes' when it prompts you.

---

### Post by Denestria on 2009-01-07
You forgot the colon
**:wq**

---

### Post by Svensk023 on 2009-01-07
i got it to work under nano, 
Thanks! :D

---

