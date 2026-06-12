---
title: "can' t install Yahoo messenger"
date: 2005-12-11
forum: General Help
---

### Post by Tominator on 2005-12-11
I just cannot figure out how to get yahoo messenger onto my machine. Can anyone help?

---

### Post by codejunkie on 2005-12-11
[quote=Tominator]I just cannot figure out how to get yahoo messenger onto my machine. Can anyone help?[/quote] what errors is it giving you? 
you should be able to just download the .deb package and install it with 
```
sudo dpkg -i nameofpackage.deb
``` 
edit:here are the steps that i used to install it, go to [http://messenger.yahoo.com/](http://messenger.yahoo.com/) on the right hand side you'll see a section for debian linux download that file place it in your home directory open a terminal and type
```
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
```
then run ```
sudo apt-get -f install
```this will download and install the required dependencies and complete the install and run it by pressing alt+f2 and entering ```
ymessenger
```.

---

### Post by Tominator on 2005-12-11
thanks, I can't activate quick reply. I will try your suggestion.

---

### Post by Tominator on 2005-12-11
when i try to install yahoo it tells me that it cannot access the archive. When I click on what i downloaded from yahoo, i am told that the archive type is not supported

---

### Post by codejunkie on 2005-12-11
[quote=Tominator]when i try to install yahoo it tells me that it cannot access the archive. When I click on what i downloaded from yahoo, i am told that the archive type is not supported[/quote]
you are trying to install it on ubuntu right?

---

### Post by Tominator on 2005-12-11
yes, ubuntu 5.10 i appreciate your help and i will try your directions

---

### Post by codejunkie on 2005-12-11
[quote=Tominator]yes, ubuntu 5.10 i appreciate your help and i will try your directions[/quote]here is the link to the file 
[http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb) 
click on it and choose save to disk if your using firefox.

---

### Post by codejunkie on 2005-12-11
[Tominator]("http://ubuntuforums.org/member.php?u=58902") 
just move the file you downloaded from [http://messenger.yahoo.com/](http://messenger.yahoo.com/) into your home folder, open a terminal and copy and paste these commands in order into a terminal
```
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
``` this installs yahoo messenger then
```
sudo apt-get -f install
``` this downloads additional dependencies needed to run yahoo messenger and finishes the install.
then you run the program with this command
```
ymessenger
``` as to your question about the quick reply function, the button in the attached screen shot is the one to use.[URL="http://ubuntuforums.org/showthread.php?t=102335"]
[/URL]

---

### Post by JoshHendo on 2005-12-12
If you can't get it to work you could always download the windows version and run it with wine :)

---

### Post by RAOF on 2005-12-12
[QUOTE=JoshHendo]If you can't get it to work you could always download the windows version and run it with wine :)[/QUOTE]
Except that's kind of like saying "If your new fridge doesn't work, you could always try picking up an old, mostly broken fridge, and fixing that up 'till it works" :p

---

### Post by purdy hate machine on 2005-12-12
Just out of curiosity, what reasons do you have for wanting to use Yahoo messenger over Gaim which should already be installed on your system?

---

