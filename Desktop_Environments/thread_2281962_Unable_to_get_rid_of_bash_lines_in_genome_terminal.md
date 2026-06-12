---
title: "Unable to get rid of bash lines in genome terminal"
date: 2015-06-11
forum: Desktop Environments
---

### Post by Karthik_Karra on 2015-06-11
I am new to the Ubuntu and tried to install SDN controller ONOS and executed "bash-profile" document which went wrong. 
From then on, these line of "bash" are consistently present on the terminal. I have tried the cmd "kill -9" but of no use.( I dont know whether to use it or not).
And even I deleted the corresponding file of ONOS and even checked there if there is any installation wrt to ONOS and there is nothing. 
I have attached the screen shot of the terminal. 

Thanks in advance for help.

---

### Post by steeldriver on 2015-06-11
Hello and welcome to the forums

What do you mean exactly by 'executed "bash-profile" document which went wrong'?

You probably just need to open the file that you modified in a text editor e.g.

```

gedit ~/.bash_profile

```

and undo your changes

---

### Post by wyliecoyoteuk on 2015-06-11
Looks like the script you ran has changed your default bash profile, which is what is set up when you login. 
The system is looking in the wrong place for it, which is why you are getting those errors.
You may need to edit /home/karra/.bash_profile as stated above, or /home/karra/.bash.rc you will need to remove a line like:

 ~/onos/tools/dev/bash_profile

It might be easier to create a new user login if you are unfamiliar with Linux, unless ONOS has edited the system-wide settings.

---

