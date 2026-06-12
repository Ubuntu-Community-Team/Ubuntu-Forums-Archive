---
title: "Quick Beryl installation question"
date: 2007-03-01
forum: Desktop Environments
---

### Post by otazman on 2007-03-01
[SIZE=3]I am following the directions here:[/SIZE] [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

 How to install Beryl/AIGLX (Nvidia):
Under these instructions are these steps.
    * Add the following line at the end of this file (x86 and amd64): 
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

    * Add key 
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

    * Save the edited file then update package lists 
[COLOR=Black]
[/COLOR] [SIZE=3][COLOR=Black]Adding the deb line makes sense but what does the 'edgy main' do at the end of the line?

Second question, is the wget line supposed to be added to the source file or is this a command that is supposed to be run?[/COLOR]

Thanks, OT
[/SIZE]

---

### Post by mexlinux on 2007-03-01
First line: is they waya a repository is specificed in /etc/apt/sources.list
Look insde that file, and you will see that its the common syntax.

Second line: is a command you have to run in order add the key to test the packages from that specific repository.

---

### Post by Stemp on 2007-03-01
Under ubuntu.beryl-project.org there is repostories for edgy, dapper, etc... so thats's why you have to specify edgy

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
It's a command to run in a terminal to add the keys of the repostoriy

---

### Post by otazman on 2007-03-01
Second line don't you need to save the file before running the command?

---

