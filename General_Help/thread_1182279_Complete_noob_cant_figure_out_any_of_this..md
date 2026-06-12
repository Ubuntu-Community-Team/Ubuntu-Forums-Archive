---
title: "Complete noob cant figure out any of this."
date: 2009-06-08
forum: General Help
---

### Post by Steakumz on 2009-06-08
Ok. So a friend suggested ubuntu to me and gave me an install disc, so I installed it on my laptop earlier today. Now i am entirely lost. I have firefox working and can browse the web, but past that nothing. I've been trying to get java so i can run online games, but all of the linux installers on the java website are not working. I have downloaded alot of stuff but cant get any of it to install. Can someone explain how i can get anything to work?

---

### Post by synapsys on 2009-06-08
Start here. [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)
If you're using an older version just google "ubuntu perfect desktop 'your version here'"
I followed this guide the first time I installed ubuntu and it's very helpful for beginners.

---

### Post by Steakumz on 2009-06-08
Ok... is there a way i can easily check which version i am using?

---

### Post by Iowan on 2009-06-08
Ordinarily, Firefox opens with a page that mentions what (numeric) version you have.  Another option is to use CTRL-ALT-F1 to drop to a terminal. The version is a couple of lines above the prompt.  CTRL-ALT-F7 will get you back to desktop. There are probably a couple of other (even easier) ways - System>About Ubuntu is one.

---

### Post by Wiebelhaus on 2009-06-08
> **synapsys said:**
> Start here. [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)
If you're using an older version just google "ubuntu perfect desktop 'your version here'"
I followed this guide the first time I installed ubuntu and it's very helpful for beginners.

Good suggestion.

---

### Post by Wiebelhaus on 2009-06-08
Open the terminal under accessories type:

```
sudo apt-get install sysinfo 
```

Wait for it to complete....then:

```
sysinfo
```

For multimedia run these commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```Then:

```
sudo apt-get install libdvdcss2
``````
sudo apt-get install w32codecs
``````
sudo apt-get install ubuntu-restricted-extras
``````
sudo apt-get install flashplugin-nonfree 
```

Then start installing from add remove things you think you might like to try , you'll be able to find everything under Applications once installed.

[Also here's a pocket guide:]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by Steakumz on 2009-06-08
wow. 130 updates in update manager. Estimated time of 8days and 6 hours.
That just sucks

---

### Post by alphacrucis2 on 2009-06-08
> **Steakumz said:**
> wow. 130 updates in update manager. Estimated time of 8days and 6 hours.
That just sucks

You must have an extremely slow connection or the estimate is way out.

---

### Post by Steakumz on 2009-06-08
so I'm trying to do that code you gave me and i got this
:~$ sudo apt-get install sysinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sysinfo

then the next line of code doesnt work
what am i doing wrong?

oh im useing 8.10 if that helps at all

---

### Post by alphacrucis2 on 2009-06-08
> **Steakumz said:**
> so I'm trying to do that code you gave me and i got this
:~$ sudo apt-get install sysinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sysinfo

then the next line of code doesnt work
what am i doing wrong?

oh im useing 8.10 if that helps at all

sysinfo is in the universe repos. 

From the menu, select System Administration Software Sources and make sure that main, universe, restricted and multiverse are all ticked.

---

### Post by Steakumz on 2009-06-08
I looked and they all have check marks. So ya. Still giving me that same error.

---

### Post by alphacrucis2 on 2009-06-08
> **Steakumz said:**
> I looked and they all have check marks. So ya. Still giving me that same error.

OK. Try this 

```
sudo apt-get update
```

This will download the latest package info from the repos.

Then 

```
sudo apt-get install sysinfo
```

---

### Post by lovinglinux on 2009-06-08
> **Steakumz said:**
> wow. 130 updates in update manager. Estimated time of 8days and 6 hours.
That just sucks

Open "System >>> Administration >>> Software Sources" then click the "Download from" drop-down menu, then select "Other", then click "Select Best Server". It will test which server is the fastest and automatically select it for you. You download speed should improve considerably. If you have a decent broadband connection it should take less than a couple of hours.

---

### Post by synapsys on 2009-06-08
OK...let's keep it noob here. Forget about sysinfo for now. You know you're running 8.10 which is an older version, that is the reason you have so many updates. I highly doubt it will take 8 days (unless you're on dial-up maybe.) Most downloads start out saying they will take forever, but once data gets flowing it takes much less time. When you first install any operating system expect a good half hour of downloading updates....no way around it. 

Anyways, follow the howtoforge.com guide for ubuntu 8.10 'perfect desktop' and you will have a good base system going. Don't worry about installing VMware unless you really need it. You will have flash, media players, email client, etc, pretty much everything an average user needs. Plus you will learn how to install/uninstall programs and enable the Medibuntu repository which is a very nice collection of useful programs. The only problem with this set-up is that they tell you to install 8,000 different media players, but you can try them out and find the ones you like and uninstall the rest. Once you have everything working you will feel much more comfortable with ubuntu. Once you master ubuntu you will never use anything else.

---

### Post by Sealbhach on 2009-06-08
Hey there, just make sure you do all this stuff (quoted below from Wiebelhaus), it will solve all your media problems. A quick way to find out your release is
```

cat /etc/issue
```as well as

```
uname -a
```Hope you enjoy Ubuntu, most of us do... ):P

.


> **Wiebelhaus said:**
> Open the terminal under accessories type:

```
sudo apt-get install sysinfo 
```Wait for it to complete....then:

```
sysinfo
```For multimedia run these commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```Then:

```
sudo apt-get install libdvdcss2
``````
sudo apt-get install w32codecs
``````
sudo apt-get install ubuntu-restricted-extras
``````
sudo apt-get install flashplugin-nonfree 
```Then start installing from add remove things you think you might like to try , you'll be able to find everything under Applications once installed.

[Also here's a pocket guide:]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by Wiebelhaus on 2009-06-09
> **alphacrucis2 said:**
> sysinfo is in the universe repos. 

From the menu, select System Administration Software Sources and make sure that main, universe, restricted and multiverse are all ticked.

My bad , I forgot.

---

