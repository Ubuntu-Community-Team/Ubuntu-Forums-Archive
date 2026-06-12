---
title: "I need help hosting a Dayz Modded Server on ubuntu server"
date: 2020-09-06
forum: Gaming &amp; Leisure
---

### Post by cosmic2910 on 2020-09-06
Hey guys and gals
So dayz is new to the whole modded thing. making modding a dayz server hard to start with, adding the whole CLI and Ubuntu server is just extra extra steps making it a lot harder, but basically so far I've got a vanilla dayz server running and working on an old LinuxGSM working think its Linux gsm version 16. but it works, im not to sure how to add mods though, im not really good at this stuff, so i have a few questions i was hoping you guys could help me with. BTW under the server files folder is a addons folder where im assuming mods go, considering all files there are .pho and .bisign's which is what mods contain, mods also contain a folder called keys with .bikeys in them so im assuming you just put all the files with there respected extension so all the .pbo and .bisign go with the .pbo and the . bikeys. but here's where i get lost, the mods folder also contains .cpp file in the root directory of the mods file, the actual mod files, which containts the aforementioned addon file which has the .pbo and .bisign files and the key file which contains the .bikey files ... how do i download the mod file to the sever which i am SSH'ing into, and then how to i copy each file to its respected location, and then in the parameter script for the launch which contains "dayzparameter="-config=${config} -port=${port} -freezecheck ${BEpath} ${logs}"  " i read i had to add -mod= and then the mod name, where do i get the correct mod name, name and how do i add it.

can you guys please help me and explain whats going on

---

### Post by EuclideanCoffee on 2020-09-08
LinuxGSM is a program developed on top of Linux platform. It appears to run ontop of the tool called Bash, which is the commandline tool for Linux. You may have more success from its official support community located on its website. [https://linuxgsm.com/support/](https://linuxgsm.com/support/)

On Bash the typical way of downloading files is with the following tools, which can be appended: curl or wget.

For your task, I think wget is the best tool.

To install:

$ sudo apt install wget

To run in your current directory:

$ wget [http://example.com](http://example.com)

Check your directory.

$ ls

Now move the file from this directory to a different location.

$ mv file_name file_location

You can move your current directory to this location and run the script.

$ cd location

$ ./script

Finally to discuss your questions on parameters, you can check with the cat or nano tool what is inside of files.

$ cat file

$ nano file

You can also use grep to locate strings within files.

$ grep "text here" file_name

And then to check your current directory, run pwd.

$ pwd

---

