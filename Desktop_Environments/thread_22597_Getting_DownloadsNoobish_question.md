---
title: "Getting Downloads/Noobish question"
date: 2005-03-28
forum: Desktop Environments
---

### Post by xNight Wraithx on 2005-03-28
Okay! I can't figure out how to get this to run. Where do I put in commands like this:

apt-get install adonthell-data



I tried inputting it in root and couldn't find a place to input it in the packet drive.
I am trying to download Adonthell

---

### Post by KLineD on 2005-03-28
Open a console (Applications | System tools | terminal) and there you can input the command.

PS. that command needs to be root to run. So add 'sudo' to that line
```
sudo apt-get install adonthell-data
``` 
It will ask for your root password and then run.

Alternatively, you can use the program Synaptic to download and install your software in a graphical way. Synaptic is located in System | Administration.

---

### Post by xNight Wraithx on 2005-03-28
Right, Synaptic is my packet program if I am not mistaken. But how do I get it to locate the download from Adonthell? All I could find was a method for updating the files currently on my computer. Sorry for the confusion.


Also, I didn't set up a root account I don't belieive but I can still boot the root terminal from the desktop if that matters.

---

### Post by xNight Wraithx on 2005-03-28
This is what I just tried:

Synaptics Package Manager--->Repositories----->New

apt-get install adonthell-data


wrong I suppose?

---

### Post by xNight Wraithx on 2005-03-28
I also went into root terminal and input the command and this is what I got:


sudo apt-get install adonthell-data

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package adonthell-data

---

### Post by lgb on 2005-03-28
You're not going to find it unless you add the repository it is found in to your sources list. I just did a search and came up empty in synaptic...  Here's a great resource, [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by xNight Wraithx on 2005-03-28
I thought that I was doing it right.....man, I am seriously clueless  #-o

---

### Post by carlc on 2005-03-28
Try following the link above to add more repositories. Actually, I would go ahead and read the whole [Ubuntu Guide (unofficial)](http://ubuntuguide.org/) if you have not already. Once you have added additional repositories, follow the instructions from the guide above to install the program using Synaptic. Here is a quote from the guide on how to use Synaptic.

> How to apt-get the easy way (How to apt-get the easy way (Synaptic)?
        
1. To refresh the list of known packages (equivalent to apt-get update)
     Edit Menu -> Reload Package List
2. To install all possible upgrades (equivalent to apt-get upgrade)
     Edit Menu -> Mark All Upgrades... -> Default Upgrade
     Edit Menu -> Apply Marked Changes
 3. To search for a package (equivalent to apt-cache search package_name)
      Edit Menu -> Search... (Specify the package name in Search box)
4. To install the selected package (equivalent to apt-get install package_name)
     Select the package to be installed
     Package Menu -> Mark for Installation
     Edit Menu -> Apply Marked Changes
 5. To remove installed package (equivalent to apt-get remove package_name)
      Select the package to be removed
      Package Menu -> Mark for Removal
       Edit Menu -> Apply Marked Changes)?

---

### Post by xNight Wraithx on 2005-03-29
Thank you for your help and as a side note:


Napoleon Dynamite rocks and sweet siggy Carlc

---

### Post by carlc on 2005-03-29
I think the Napoleon Dynamite gets better everytime you watch it. It is also a great movie to quote from. 

Napoleon, don't be jealous that I've been chatting online with babes all day.

---

