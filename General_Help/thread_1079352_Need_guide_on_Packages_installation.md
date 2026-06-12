---
title: "Need guide on Packages installation"
date: 2009-02-24
forum: General Help
---

### Post by ADi_06 on 2009-02-24
Hi friends (New To Linux Ubuntu Here)
          I want to know that how can i download all the packages available in "Package Manager" directly not from "Package Manager" because many user in my region don't have good internet speed and they wont be able to download them directly through "Package Manager". So i want to download them all and distributes them to the users in shape of CDs.

2nd: I have download many packages and have made its ISO through "AptonCd". How can i use that image to install those packages in someones others Ubuntu Machine.

3rd: I see that after downloading and installation, packages are stored in Var/Cashe folder; Are those temporary files or they are being used for running. Because if they are not being used how can i delete them; Because there is no option to right click and delete.

Please do guide
Regard
~ADi~

---

### Post by roccivic on 2009-02-24
Download packages here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then open terminal (applications > accessories > terminal) and install the packages using dpkg:

```
sudo dpkg -i /home/user/packages/*
```

obviously you will have to change "/home/user/packages/" to the actual path of where the packages are ;)

Peace

---

### Post by plucky on 2009-02-24
> 3rd: I see that after downloading and installation, packages are stored in Var/Cashe folder; Are those temporary files or they are being used for running. Because if they are not being used how can i delete them; Because there is no option to right click and delete.


Those .deb files are used to create the AptonCD iso,and if you have to re-install an application.If they are not there,then the file is downloaded from the repository.
To delete them use ```
sudo apt-get clean
``` but there are other options available e.g autoclean,autoremove etc. 

Use **man apt-get** to explain the different options.

Good Luck

---

### Post by ADi_06 on 2009-02-25
> **plucky said:**
> Those .deb files are used to create the AptonCD iso,and if you have to re-install an application.If they are not there,then the file is downloaded from the repository.
To delete them use ```
sudo apt-get clean
``` but there are other options available e.g autoclean,autoremove etc. 

Use **man apt-get** to explain the different options.

Good Luck
Dear Plucky,
            You are a wise person and guided well. Could you please explain me "I have download many packages and have made its ISO through "AptonCd". How can i use that image to install those packages in someones others Ubuntu Machine." I had the image and i dont want to type all the command one-by-one in terminal to install all those Debian; they are about   and i want this to be more user friendly to myself and others.
I am new to Linux and really impressed and want others from my region to adopt it. Many of them are not handy to these technical things and i want then to use Linux easily. please do guide.

Pardon my English & please use simple English word.

---

### Post by plucky on 2009-02-25
Burn the AptonCD image to a CD and use the CD as a Source.

To add the CD as a Source,put the CD in a drive and open **System > Administration > Software Sources > Third Party Software** and select Add CDrom.

Once the CD has been added as a source,the update manager will open and any updates will be installed.Other applications have to be installed individually or use the AptonCd restore command to copy  the .deb files to the /var/cache/archives.Then use the command that **roccivic** specified and point it at the Archives.


Good Luck

---

### Post by ADi_06 on 2009-02-25
***roccivic & plucky***
Thanks to both of you. I really appritiate your help. It was a big deal 4 me but because of both of you i am able to do many of my work done.
All People repect and recognize others works; That is most inrusting Fact i got in This Forum. I would greatly like to thanks you and alll other humanity lovers.

I Will request for help in future from both of you if i needed any.):P

Regard
~ADi

---

