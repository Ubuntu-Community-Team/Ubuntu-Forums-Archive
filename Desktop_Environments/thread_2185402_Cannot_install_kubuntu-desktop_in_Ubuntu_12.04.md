---
title: "Cannot install kubuntu-desktop in Ubuntu 12.04"
date: 2013-11-02
forum: Desktop Environments
---

### Post by krespim on 2013-11-02
I have Ubuntu 12.04 installed on my laptop and wanted to install also the kubuntu-desktop following these instructions:

```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get install kubuntu-desktop
```


 Unfortunately I am getting this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 kubuntu-desktop : Depends: kde-window-manager
E: Unable to correct problems, you have held broken packages.


```


If I try to install the kde-window-manager, this is what I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 kde-window-manager : Depends: libgles2-mesa (>= 7.8.1) or
                               libgles2
                      Depends: libkwinglesutils1 (= 4:4.11.2-0ubuntu1~ubuntu12.04~ppa2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I have searched for quiet a bit now and nothing seemed to solve my problem. Any ideas on how to solve this? I have not yet tried to install kde-full.

The main reason to have kubuntu is because some features of kate (which I really want to have for work) are not working properly (Python plugins and changing themes). So I naively thought that perhaps there are some KDE dependencies missing. I also like to have some extra desktops environments to play with :)

---

### Post by uzumakifahim on 2013-11-02
Try
```
sudo apt-get autoclean
```

and then trying again installing KDE.

---

### Post by deadflowr on 2013-11-02
What happens if you run
```
sudo apt-get install -f
```
This is the command for fixing broken packages.

Also, is there something in the ppa that is better then what you would get from the version in the repos?

---

### Post by krespim on 2013-11-03
Just did that and got the same error.

---

### Post by krespim on 2013-11-03
> **deadflowr said:**
> What happens if you run
```
sudo apt-get install -f
```
This is the command for fixing broken packages.

Cheers, did that but again same error. 

> **deadflowr said:**
> Also, is there something in the ppa that is better then what you would get from the version in the repos?

Not really, I just did it because those were the instructions I've found. I have tried with the repo (software centre) and the errors are still there. There seems to be some package conflicts. 

Also @uzumakifahim:

Thank you for your suggestions. I now got kate working with the python scripts and themes, which was my original goal anyway, by adding some missing libraries that are recommended for [installation from source]("http://kate-editor.org/get-it/"): 

```
sudo apt-get install g++ make git cmake kdelibs5-dev libqjson-dev python-kde4-dev python-qt4-dev
```

 Note that the source code installation did not work, so I've installed with:
```
sudo apt-get install kate
```

after installing the above libraries. All appears to be fine now. That said, I am leaving this thread open (if the mods allow it) and listen to suggestions on how to solve this because this issue - inability to install kubuntu-desktop on Ubuntu 12.04 - is common to a few people out there and there is no accepted solution.

---

### Post by grahammechanical on 2013-11-03
Perhaps if you have install kubuntu-desktop first and then installed the backports PPA. I have had no problem installing Kubuntu Desktop on 13.10 during its development. I used the Ubuntu Software Centre.Regards.

---

### Post by ozg-order13 on 2014-03-29
Just go to software-center and install these 2 dependencies: 
Depends: "libgles2-mesa" or "libgles2"
and
 Depends: "libkwinglesutils1"
After SC finishes installing libs, you do the trick by typing 
```
 
sudo apt-get install kde-windows-manager && kubuntu-desktop

```
and voila...

---

### Post by su:bhatta on 2014-03-30
> **ozg-order13 said:**
> Just go to software-center and install these 2 dependencies: 
Depends: "libgles2-mesa" or "libgles2"
and
 Depends: "libkwinglesutils1"
After SC finishes installing libs, you do the trick by typing 
```
 
sudo apt-get install kde-windows-manager && kubuntu-desktop

```
and voila...

There is no kde-windows-manager package.

It is kde-window-manager

---

### Post by monkeybrain20122 on 2014-03-31
Just wondering why didn't you just install kubuntu. You can easily install a lxde (not lubuntu-desktop, only lxde) to switch between unity and lxde session, but kubuntu-desktop is a huge download with a lot of dependencies and since kde is not modular you are going to bring in even more duplications. I suspect you may also run into conflicts are problems later.

---

