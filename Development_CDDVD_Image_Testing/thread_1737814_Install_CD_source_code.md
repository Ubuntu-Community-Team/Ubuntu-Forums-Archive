---
title: "Install CD source code"
date: 2011-04-23
forum: Development CD/DVD Image Testing
---

### Post by Shiryu on 2011-04-23
Hello, I want to create a custom CD to install Kubuntu.
Where do I get the source code of the softwares used by Kubuntu Alternate CD?

---

### Post by Joe of loath on 2011-04-23
How custom? Most customisation can be done via remastersys or similar.

---

### Post by Shiryu on 2011-04-24
Many tools such as Remastersys and UCK work only with live CD instead of alternate CD. These tools can create a CD with all data that is stored in the computer, and it can not be used to install Kubuntu to different computers for different users.

I want to edit a CD, I want to add and remove packages, remove other languages, add all packages for my language, add repositories, and finally, run a bash script after everything be installed and configure specific details.
I want to simplify the instalation steps.

---

### Post by Joe of loath on 2011-04-25
You don't need the source code to do that. You will need to modify the packages and package lists, and burn the finished product to a bootable CD.

The source code is for each individual application, having it won't let you add and remove things, only edit the applications themselves.

---

### Post by Shiryu on 2011-04-29
The source code that I am looking for is the source of the software that is used to install Ubuntu. This software is run when we boot an Alternate CD to install Ubuntu.
I could edit it to simplify installation questions with custom default answers.
I want the source to understand better how Ubuntu works and how it is installed.

---

### Post by oldos2er on 2011-05-01
```
apt-get source ubiquity
```

---

