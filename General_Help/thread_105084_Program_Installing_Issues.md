---
title: "Program Installing Issues"
date: 2005-12-17
forum: General Help
---

### Post by TheSe7enthProphet on 2005-12-17
Ok, first off, I'm new to Linux, os the following may sound really stupid.

Since I installed Ubuntu, I've been using the Synaptic Package Manager to install additional products, such as the K Desktop Environment, which I am currently using. Well, I want  to install programs from the internet that are not in the PAckage MAnager such as Firefox 1.5 and Azureus, but I can't quite figure it out.

I'll use Azureus as an example of my problem. I downloand the .bz2 file to my desktop, then unarchive it to my home folder. After unarchiving it, I try to execute the "azureus" (Has a picture of a black screen and a ">" on the icon) object within the folder and nothing happens.

Once that didn't work, obviously, I tried moving the folder to what I belive to be where all the other files for other programs are (Similar to Program Files in Windows) and it tells me that I do not have permission to access said folder (/etc/azureus). I have been told that I need to log in as root or sudo (or several others, but those are the top two) to pull this off, but I do not know how I would go about doing this.

If I am doing something wrong or you have any kind of advice on how I can get this working, please share. Thanks!

---

### Post by aysiu on 2005-12-17
[https://wiki.ubuntu.com/AzureusHowTo](https://wiki.ubuntu.com/AzureusHowTo)
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by madtinkerer on 2005-12-17
if you want to execute a program that is in a location not in your path, you have to a) execute it with the entire path >  /home/momo/azureus/azureus
 or b) go into the directory where the program is located and type ./azureus

to use sudo, you type sudo and the command
for example you want to run apt-get update to see if there are new packages available to download.  so you would go

sudo apt-get update

and enter the password of the user that you are logged in as.

Hope that helps.

---

