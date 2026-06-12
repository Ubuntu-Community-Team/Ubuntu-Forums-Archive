---
title: "Created a local repo but can't find files ?"
date: 2006-01-19
forum: General Help
---

### Post by petef on 2006-01-19
Hi guys

Im a newbie to Linux\Unix and have created a local repo on my machine at home as I don't have Internet access. I have filled the repo with about 200 meg of Deb files from my Ubuntu machine at work but when I try to install eg Gnomebaker I get "file not found" in a window pop up ? I have created Packages.gz Sources.gz 

Any ideas ? :confused: 

Thanks in advance

Pete

---

### Post by cotcot on 2006-01-19
This means you have added a local folder to your repository list (/etc/apt/sources.list)?  Have you done "apt-get update" afterwards ?

---

### Post by petef on 2006-01-19
I get the icon in the top right stating I have new updates but when I try to install these it fails ?

I have added the local repo to /etc/apt/sources.list

I haven't done 'apt-get udpate' at the terminal afterwards do you think this could be the problem ?

Thanks

Pete

---

### Post by ozorba on 2006-01-19
[QUOTE=petef]I get the icon in the top right stating I have new updates but when I try to install these it fails ?

I have added the local repo to /etc/apt/sources.list

I haven't done 'apt-get udpate' at the terminal afterwards do you think this could be the problem ?
[/QUOTE]

You need to do sudo apt-get update and then sudo apt-get upgrade to ensure that everything gets updated.

---

### Post by petef on 2006-01-19
Will the apt-get update and upgrade work OK from my local repos ?

Cheers

Pete

---

### Post by petef on 2006-01-19
Bump

---

### Post by lysis on 2006-01-19
yes.

update tells apt you updated the repos.


upgrade tells apt to do all of the updates that you have available (the popup window you mentioned)

---

