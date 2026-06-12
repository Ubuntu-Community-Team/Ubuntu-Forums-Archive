---
title: "Where is the programs in synaptic"
date: 2006-06-26
forum: Desktop Environments
---

### Post by lnxquestions on 2006-06-26
Hi 
I want to download some programs like nvu and k3d and a download manager and more so i opened synaptic and pressed reload . After that i searched for programs i want and i didnt find them ...
There is too many programs that are not listed .. What to do ?

---

### Post by frodon on 2006-06-26
You should enable some repositories, by default there're not all active.
Here is an example of a good source.list file (this file contain the list of the repositories) : 
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by lnxquestions on 2006-06-27
Thanks but let me get it straight
First i executed this command : sudo gedit /etc/apt/sources.list
Then i replaced the source list with the list provided in that thread after that i closed gedit and saved the changes .
Then i executed this one : apt-get update ; sudo apt-get upgrade , and it started to download from internet and after that i found lots of programs that i want and didnt found others .

Now what should i do ? What is the GPG key ? Could you explane it to me and tell me what to do now ?
Best Regards

---

### Post by frodon on 2006-06-27
Some repositories need a GPG key to work for example the cipherfunk repository but if you just paste the file from the link i gave you you have only the ubuntu repository enable and it should be enough. With the ubuntu repository you don't have to bother with GPG key.

Now, to install softwares just use synaptic which is a front end for apt-get commands, for example the reload button in synaptic will do the same thing than the "sudo apt-get update & sudo apt-get upgrade" commands.
I give you 2 links about synaptic and software installation, you should find in what you're looking for, if not feel free to ask for help :
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Have a nice day man ;)

---

### Post by lnxquestions on 2006-06-27
Hi frodon how are you ?

I was using a debian-based distro so i know synaptic and i installed lots of programes using it but in ubuntu i feel there is somthing different .
First of all you have to change the source list to get more programs and second not all the programs are listed in it ... Try to find Cinelerra you will not find it ... 
There is other programs i looked for but i couldnt find ....
What to do ?

---

### Post by frodon on 2006-06-27
Well, ubuntu by default do not include any apps which is not open source (almost) and it's why the universe and multiverse repositories are not enable after a fresh install.
Once you have enable them (what you did :) ) you have all the ubuntu packages available.

Unfortunatly not all the softwares are in the repositories, when you can't find a package in the repos you will have to find the .deb or the sources and install it by hand (not that difficult, a simple double click allow to install .deb files in dapper).

Now, let me introduce the backport repository which offer you some more softwares and recent release of some softwares, you could enable this repository if you wish but read this to understand what this repo is (be careful this thread was for hoary and breezy, i don't know if the dapper backport repo is opened yet) :
[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

To finish there's some external repositories made by volunteers to offer some propietary apps like the plf repository which is really popular now : 
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

For cinelerra here is a guide for its installation : 
[http://ubuntuforums.org/showthread.php?t=188264](http://ubuntuforums.org/showthread.php?t=188264)

---

### Post by lnxquestions on 2006-06-27
Thank alot frodon ... Great explanation

---

