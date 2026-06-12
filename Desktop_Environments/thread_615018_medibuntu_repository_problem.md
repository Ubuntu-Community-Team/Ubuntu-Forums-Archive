---
title: "medibuntu repository problem"
date: 2007-11-16
forum: Desktop Environments
---

### Post by 321on on 2007-11-16
Below is the message I get when I try to do anything

E: Type ‘--19:32:31--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

The upgrade icon will not work as is orange colour and has message 

This usually means that your installed packages have unmet dependencies

What to do next - this is my first week with Ubuntu

---

### Post by integr8e on 2007-11-16
Try opening a console and running the following command:
```
sudo apt-get install -f
```

(Make sure you don't have another package manager running - such as Synaptic or Adept)

---

### Post by 321on on 2007-11-16
Just tried that and get the message

E: Type ‘--19:32:31--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
nigel@nigel-desktop:~$

---

### Post by ruibernardo on 2007-11-16
Hi 321on,

it seems that the file has a timestamp that shouldn't be there. Can you post that file?

---

### Post by 321on on 2007-11-16
Tell me how to do it and I will.

---

### Post by ruibernardo on 2007-11-16
Open the file with a text editor. You can do this by selecting Applications > Accessories > Text Editor. Then click "Open" in the taskbar and select the file /etc/apt/sources.list.d/medibuntu.list.

Copy and paste its content here.

---

### Post by 321on on 2007-11-17
What is the full address of the file you want to see?  Still a beginner in Ubuntu - next task to get the wireless PCs attached to the network.

---

### Post by ruibernardo on 2007-11-17
> **321on said:**
> What is the full address of the file you want to see?
I'd like to see this one:
> **epimeteo said:**
> /etc/apt/sources.list.d/medibuntu.list

---

### Post by 321on on 2007-11-17
--19:32:31--  [http://www.medibuntu.org/source.list.d/feisty.list](http://www.medibuntu.org/source.list.d/feisty.list)
           => `feisty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:32:32 ERROR 404: Not Found.

This is the file content for pasting above into Text Editor

---

### Post by 321on on 2007-11-17
The problem begun when I tried to install Skype using the instructions on the 
this link

[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Was the terminal instruction that started the problem

The rest of process is :

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype

I have not completed yet (not sure what character the vertical line is gpg -O- | sudo apt) on my keyboard

---

### Post by ruibernardo on 2007-11-17
You have made a typo when you added this repository. You typed "...source.list.d/feisty.list" and it should have been "...source**s**.list.d/feisty.list".

This are the [instructions to add the medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"). Copy/paste them to a terminal (it is just one line):
```
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
```Add the GPG key of the repository and update your apt to use the new repository (it is just one line):
```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```In the end type this command in the terminal to see the content of the file:
```
cat /etc/apt/sources.list.d/medibuntu.list
```The output should be something like this:
```
# Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free
```Hope this helps you.

---

### Post by ruibernardo on 2007-11-17
If you don't know which is the | character in your keyboard, just copy/paste the instructions :)

---

### Post by 321on on 2007-11-17
Followed the first part of instruction no problem result is
Try `wget --help' for more options.
nigel@nigel-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
--12:21:29--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 224 [text/plain]

100%[====================================>] 224           --.--K/s           

Doing the rest now

---

### Post by 321on on 2007-11-17
Thanks for the help - package manager working again updating Ubuntu.

---

