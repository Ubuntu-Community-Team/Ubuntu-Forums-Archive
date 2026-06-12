---
title: "JRE &amp; Flash"
date: 2006-08-30
forum: Desktop Environments
---

### Post by lugos on 2006-08-30
I know has probably been asked hundreds of times, which leads me to my question.  Does Ubuntu have a tutorial or something on how to install Java Runtime Environment and the Macromedia Flash plug-in for Firefox?

Thanks for the help.

lugos

---

### Post by catlett on 2006-08-30
Do these commands. Just copy and paste from here into your terminal. (just in case, the terminal is found on the top panel under Applications<Accessories<Terminal)
The first thing is to change the repository list. Ubuntu leaves most of the repos off the installation list,
Backup a copy of your original list.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Now open your list in a text editor
```
sudo gedit /etc/apt/sources.list
```
Delete everything on the page. (do not worry, if anything ever hapened you have a backup. You would recover the original list with sudo cp /etc/apt/sources.list /etc/apt/sources.list) 
Copy and paste this list in the blank page. 
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```
Save the file and close it. Enter this into the terminal ```
sudo apt-get update
```That will update your cache of applications. You will nowe be able to access the repositories with flash and java.
For flash enter this into the terminal```
 sudo apt-get install flashplugin-nonfree
``````
sudo update-flashplugin
```
For java enter this command ```
sudo apt-get install sun-java5-jre sun-java5-plugin
```The list I just gave you is the repository list for the Dapper Guide. You can now go to the guide and copy/paste in any commands they have for applications you want. You already have the repos they use, just browse to an application you want and do what we just did. Copy/paste the commands from the guide to your terminal. 
Here is the link [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by lugos on 2006-08-30
Thank you so much!  Worked perfectly.

lugos

---

