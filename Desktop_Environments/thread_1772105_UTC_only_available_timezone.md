---
title: "UTC only available timezone"
date: 2011-05-31
forum: Desktop Environments
---

### Post by lusepuster on 2011-05-31
Hi folks; 

I've just gone from Ubuntu to Kubuntu (mostly out of curiosity) by removing most of the Gnome software on my install and installing the kubuntu-desktop package in synaptic.

Mostly it works fine, but I cannot get the time settings right, which is quite annoying. It does not let me choose any other time zone than UTC. when logged in as a user.

When sudo'ing the system settings, I see a lot of available time zones, but get an error message and cannot change it after all (wrong ownership to some file, IIRC). 

Is there really no way to let users choose which time zone they want displayed? Or at least for me now to make sure that system time is UTC while my desktop time is my local time?

---

### Post by wildmanne39 on 2011-05-31
> **lusepuster said:**
> Hi folks; 

I've just gone from Ubuntu to Kubuntu (mostly out of curiosity) by removing most of the Gnome software on my install and installing the kubuntu-desktop package in synaptic.

Mostly it works fine, but I cannot get the time settings right, which is quite annoying. It does not let me choose any other time zone than UTC. when logged in as a user.

When sudo'ing the system settings, I see a lot of available time zones, but get an error message and cannot change it after all (wrong ownership to some file, IIRC). 

Is there really no way to let users choose which time zone they want displayed? Or at least for me now to make sure that system time is UTC while my desktop time is my local time?
Hi, I suspect that might be from removing most of gnome, you can install the kde4 desktop and have kubuntu without uninstalling gnome then you can choose which one you want at login.

---

### Post by lusepuster on 2011-05-31
> **wildmanne39 said:**
> Hi, I suspect that might be from removing most of gnome, you can install the kde4 desktop and have kubuntu without uninstalling gnome then you can choose which one you want at login.
I know they can run in parallel, but I removed it to reduce system clutter. I didn't think Kubuntu-desktop would rely on parts from Gnome?

---

### Post by wildmanne39 on 2011-05-31
> **lusepuster said:**
> I know they can run in parallel, but I removed it to reduce system clutter. I didn't think Kubuntu-desktop would rely on parts from Gnome?Hi, saw some one else with an issue like yours but it did not have a answer for it.

---

### Post by ankspo71 on 2011-05-31
Hi,
> Is there really no way to let users choose which time zone they want displayed? Or at least for me now to make sure that system time is UTC while my desktop time is my local time?

Did you already check to see if right clicking on your analog clock or digital clock will let you change your displayed time, or are you having the same problem changing the time zone there too? 

Be sure to tell the analog or digital clock 'not' to display the local time (the system's time), but rather your preferred displayed time, like shown in the screenshot below.

---

### Post by ankspo71 on 2011-05-31
Hi,
> **lusepuster said:**
> When sudo'ing the system settings, I see a lot of available time zones, but get an error message and cannot change it after all (wrong ownership to some file, IIRC). 


About the error:
It's possible that there is a configuration file in your home folder that has accidentally changed ownership permissions from 'you' to 'root'. This can prevent applications (such as systemsettings) from being able to read (and or write to) that file. 

To check for this particular ownership problem, you can use this command in your terminal:
```
ls -alR ~ | grep root
```
(note: it is normal to see one line saying the ownership has "root root" which would be the parent folder /home.)

Everything inside your home folder is supposed to be owned by you, as far as I know, so if you do find configuration files with the wrong ownership permissions you can use the command below to change ownership of all of the files recursively in your home folder.

```
sudo chown -R yourusername:yourusername /home/yourusername
```
(replace yourusername with your actual username) 

A little more info on the chown command:
[https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group](https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group)

P.S. I don't think removing Gnome applications would mess up the time zone settings for Kubuntu, but if it has, you could try reinstalling kubuntu-desktop to make sure no important things were removed.

```
sudo apt-get install --reinstall kubuntu-desktop
```
if the above command gives you an error saying kubuntu-desktop is already installed (and it probably will because the --reinstall option doesn't work as expected with metapackages), then try these commands:
```
sudo apt-get remove kubuntu-desktop
sudo apt-get install kubuntu-desktop
```

Hope this helps.

---

