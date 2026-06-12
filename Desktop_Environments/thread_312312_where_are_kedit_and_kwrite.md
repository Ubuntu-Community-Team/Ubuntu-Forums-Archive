---
title: "where are kedit and kwrite?"
date: 2006-12-04
forum: Desktop Environments
---

### Post by likes2skate on 2006-12-04
Hi, 

I am trying out kubuntu.  I am a long-time KDE user from the RedHat world.  

I am used to getting kate, kwrite and kedit, and I use all three.  So far, I have not figured out how to install kedit and kwrite.  Where are they?  

Also, where is kget?  

Thanks,

likes2skate aka Rick Graves

---

### Post by drphilngood on 2006-12-04
> **likes2skate said:**
> Hi, 

I am trying out kubuntu.  I am a long-time KDE user from the RedHat world.  

I am used to getting kate, kwrite and kedit, and I use all three.  So far, I have not figured out how to install kedit and kwrite.  Where are they?  

Also, where is kget?  

Thanks,

likes2skate aka Rick Graves

```
sudo apt-get install kate kwrite kedit
```

see here:
[sources]("http://www.psychocats.net/ubuntu/sources")

and here:
[installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by likes2skate on 2006-12-04
drphilngood,

I tried sudo apt-get kedit and sudo apt-get kwrite (separately), but it said "Couldn't find package kedit" and "Couldn't find package kwrite".  

Do I need to uncomment some lines in sources.list, like for universe or backports?

Thanks,

likes2skate

---

### Post by likes2skate on 2006-12-04
drphilngood,

I am using Edgy, 6.10. 

I put the Edgy text from the link you included,

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

into sources.list, just like the page said.

It still says "Couldn't find package kedit" and "Couldn't find package kwrite". 
 
????

Thanks,

Rick

---

### Post by drphilngood on 2006-12-04
> **likes2skate said:**
> drphilngood,

I tried sudo apt-get kedit and sudo apt-get kwrite (separately), but it said "Couldn't find package kedit" and "Couldn't find package kwrite".  

Do I need to uncomment some lines in sources.list, like for universe or backports?

Thanks,

likes2skate

enter the following in a terminal and post the results:


```
sudo kedit /etc/apt/sources.list
```

or

```
sudo nano /etc/apt/sources.list
```

edit:
You posted before I posted but I´ll check the repos for you and see if they are unavailable and post back.

---

### Post by drphilngood on 2006-12-04
I just checked the repos and kate and kedit are available but not kwrite for some reason.  However, you can try leafpad in place of kwrite.

Double check your repos and then try installing kate,kedit and leafpad again.

edit:
You can use this guide to help you with your repositories as I suspect you have yet to uncomment the deb repositories.

[Adding Repositories]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Repositories")

Kubuntu has a nice GUI to install apps from if you wish to use it.  Just see here:

[Add/Remove Programs - the basic method]("https://help.ubuntu.com/community/InstallingSoftware#head-5f84c7b4fe3122d8f220464cabff1195644e840f")

---

### Post by likes2skate on 2006-12-04
drphilngood,

What I did not know to do after changing the sources.list file is this:

sudo aptitude update

So I got kedit.  

I found the Adept Installer (Add/Remove Programs from the Menu).

I also took a look at Menu, System, Adept Manager.  That seems to be more comprehensive.  

I will take a look at leafpad.

Thanks,

Rick

---

### Post by drphilngood on 2006-12-04
> **likes2skate said:**
> drphilngood,

What I did not know to do after changing the sources.list file is this:

sudo aptitude update

So I got kedit.  

I found the Adept Installer (Add/Remove Programs from the Menu).

I also took a look at Menu, System, Adept Manager.  That seems to be more comprehensive.  

I will take a look at leafpad.

Thanks,

Rick

My apologies, Rick.  In my haste to be helpful, I dropped the ball.  

On the other hand, it is good to hear that you are sorted now.  I hope you enjoy Kubuntu.

Good luck!

---

### Post by likes2skate on 2007-01-05
For the record!

kwrite was there in /usr/bin/

There is also a kwrite icon on the applications icons list.

It is just not on the menu automatically.  

I had to edit the menu to put it on. 

I assume it is there because kate is a rewrite of kwrite, according to the debian package page here:

[http://packages.debian.org/stable/editors/kate](http://packages.debian.org/stable/editors/kate)

Yeah!

---

