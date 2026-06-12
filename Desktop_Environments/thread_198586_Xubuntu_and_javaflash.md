---
title: "Xubuntu and java/flash"
date: 2006-06-17
forum: Desktop Environments
---

### Post by satbunny on 2006-06-17
I have read the wiki, and how to install Java into Ubunto 6.06.
I have intalled Xubuntu 6.06, but Synpatic does not report the application sun-java5-bin, not can does apt-get.
I d have the multiverse and universe repositories enabled..

Help?

Oh and the same question goes for Flas player as well.

---

### Post by shuttleworthwannabe on 2006-06-17
Boet, I saw your other thread. Try the wiki again, or use automatix for FLASH and JAVA.
                                     _**OR try these options**_
For FLASH try this: [http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

For Java: [http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by satbunny on 2006-06-21
Sorry but this doesn't work:

> tom@evo:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
tom@evo:~$


Xubuntu does not seem to see the packages, even though I have all the usual repositories selected in my sources.list

Is there an Xubuntu expert here who can say if the normal method (above) should work?

---

### Post by lamego on 2006-06-21
First and about the suggestion from shuttleworthwannabe, DO NOT use automatix it is more probable that it will break your system thant it will help you. Easybuntu is ok.

Regarding not beeing able to install java using the "normal" install procedure your problem is that you are missing the  multiverse applications repository from which the sun java is available.

Read about the repositoreis [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by deathbyswiftwind on 2006-06-21
I dunno if bumps has the option for xubuntu but if so go with bumps :)

---

