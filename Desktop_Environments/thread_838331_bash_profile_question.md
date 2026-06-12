---
title: "bash_profile question"
date: 2008-06-23
forum: Desktop Environments
---

### Post by alastone on 2008-06-23
Hi,

- Ubuntu 8.04

After installing an application, it's instructed to add a command to the bash_profile file.

From what I understand after some research, I created a

.bash_profile

file (using gedit) in my user folder (don't know whether that's the correct name) /home/alan, so

/home/alan/.bash_profile

and added the following:

#!/bin/bash
source /opt/path1/setuptx /opt/path1  <--- required command

Is this correct ?

I'm asking because it doesn't seem to be taken into account after logging in again.

Thanks,
Alan

---

### Post by forger on 2008-06-23
sorry for being suspicious, but what kind of program?

---

### Post by alastone on 2008-06-23
after some head scratching...

the problem isn't with the application ( which is invoked within the SciTE editor), it's with SciTE itself which doesn't read the .bash_profile and .bashrc files

---

