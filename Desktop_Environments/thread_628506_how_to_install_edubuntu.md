---
title: "how to install edubuntu"
date: 2007-12-01
forum: Desktop Environments
---

### Post by ubiubi on 2007-12-01
Hi all. 
I've just installed ubunto and I'd like to install edubunto desktop environment for my daughter as a second user. The problem is that I can't find edububtu desktop in the software packet list. I did see kububtu-desktop, though. I installed ubuntu from a live cd I got with a magazine. The magazine advises that Edubuntu, xubuntu, mythbuntu and ubuntustudio should all be available. Any way around the missing desktop package?

---

### Post by Vixis on 2007-12-01
Application -> Accessories -> Terminal

```
sudo apt-get install edubuntu-desktop
```

---

### Post by ubiubi on 2007-12-02
HI
I tried the sudo command you suggested but it said too many files missing.SO, Ive downloaded the edubunto.iso CD. But was unable to install it without uninstalling ubintu. My next step is to do just that and try to add a kubuntu desk invironment from that installation. the only problem is that I couldn't see the kubunto desktop in the left window of the package installation manager. I did see, however, the KDE enviroment in the right window. The last time I tried to install kubuntu under ubuntu I got the kubuntu log in page followed by the ubuntu desk top. What a waste of time! I'd really like to have ubuntu/kubuntu desktop for me and the edubuntu for my daughter. Any suggestions?

Thanks for reading this

---

### Post by XVII on 2007-12-02
That command should have worked.  Try:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by Danikar on 2007-12-02
I think u mean.
```
sudo aptitude update && sudo aptitude install edubuntu-desktop
```

---

### Post by XVII on 2007-12-02
> **Danikar said:**
> I think u mean.
```
sudo aptitude update && sudo aptitude install edubuntu-desktop
```

He said he also wanted to install Kubuntu for himself.

---

### Post by ubiubi on 2007-12-03
hi all, again. I installed edubuntu from the cd and tried to install the kubuntu desktop environment using the sudo command you gave me. It claimed kubunto-desktop did not exist. So I reinstalled ubuntu from the magazine cd and typed in the update and install commands with a very similar negative result. here is the error message in full

mark@mark-desktop:~$ sudo aptitude update && sudo aptitude install kubuntu-desktop
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
mark@mark-desktop:~$ 

Any suggestions for what to do next, anyone?

---

### Post by maybeway36 on 2007-12-03
Go to System>Administration>Software sources and enable main.

---

### Post by XVII on 2007-12-03
> **ubiubi said:**
> hi all, again. I installed edubuntu from the cd and tried to install the kubuntu desktop environment using the sudo command you gave me. It claimed kubunto-desktop did not exist. So I reinstalled ubuntu from the magazine cd and typed in the update and install commands with a very similar negative result. here is the error message in full

mark@mark-desktop:~$ sudo aptitude update && sudo aptitude install kubuntu-desktop
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
mark@mark-desktop:~$ 

Any suggestions for what to do next, anyone?

Try kubunt**u**-desktop. :wink:

---

### Post by LinuxLuver29 on 2007-12-03
I don't know too much about dual-booting linux and linux but are you sure you aren't able to dual-boot ubuntu and edubuntu with grub?

---

### Post by XVII on 2007-12-03
> **LinuxLuver29 said:**
> I don't know too much about dual-booting linux and linux but are you sure you aren't able to dual-boot ubuntu and edubuntu with grub?

You can just switch desktop environments.

---

### Post by maybeway36 on 2007-12-04
Won't both user's settings change to Edubuntu defaults?

---

### Post by XVII on 2007-12-04
> **maybeway36 said:**
> Won't both user's settings change to Edubuntu defaults?

Maybe.  I've never tried Edubuntu.

---

### Post by ubiubi on 2007-12-05
to continue ...

I activated "main" in software sources and tried the "sudo aptitude update && aptitude install edubuntu- desktop" command. It then responded  by downloading files for 1hr and then asking me which desktop I wanted as a default. When I logged of and on again I had the edubuntu log on screen and the ubuntu desktop. So, I did a clean install, this time with my edubuntu disk and used the above command , altered of course, to install kubuntu-desktop. It went through the same proceedure, this time it asked me to put the edubuntu disk back in the drive. Unfortunately (I suppose) I grabbed the ubuntu dik, mistakenly, there was a break in the terminal script ( No error message) and the script started "apt-get ****files
I left the computer downloading and went to bed. A second window had opened displaying the contents of the cd and an error message saying there were packages it wanted to install but another installation package was operating and it could not do so untill I closed it. I closed the error window, considering that the ubuntu cd was not the correct  cd in any case and that the edubuntu installation would download any missing files it needed. ( I know, I'm my own worst enemy!)

This morning I was faced by a text window asking me which system Gnome/ kubuntu I wanted as default start up. and how to change it in a particular file if I wanted to at a later date. I pressed return
A similar window appeared asking me something else which I don't remember off-hand. It seamed not so important and I was unable to effect the Y/N at the bottom. So I just closed the window. I logged out selected a system But did not see the kubuntu option. 

I had to go to work so turned off the computer. Ill check tonight to see if it mysteriously appears. I can always uninstall kubuntu using aptitude and then install again (this time using the correct cd if it asks me)but it must be on the system. How can I find it and use it?

Thhanks for your help

---

### Post by XVII on 2007-12-05
> **ubiubi said:**
> to continue ...

I activated "main" in software sources and tried the "sudo aptitude update && aptitude install edubuntu- desktop" command. It then responded  by downloading files for 1hr and then asking me which desktop I wanted as a default. When I logged of and on again I had the edubuntu log on screen and the ubuntu desktop. So, I did a clean install, this time with my edubuntu disk and used the above command , altered of course, to install kubuntu-desktop. It went through the same proceedure, this time it asked me to put the edubuntu disk back in the drive. Unfortunately (I suppose) I grabbed the ubuntu dik, mistakenly, there was a break in the terminal script ( No error message) and the script started "apt-get ****files
I left the computer downloading and went to bed. A second window had opened displaying the contents of the cd and an error message saying there were packages it wanted to install but another installation package was operating and it could not do so untill I closed it. I closed the error window, considering that the ubuntu cd was not the correct  cd in any case and that the edubuntu installation would download any missing files it needed. ( I know, I'm my own worst enemy!)

This morning I was faced by a text window asking me which system Gnome/ kubuntu I wanted as default start up. and how to change it in a particular file if I wanted to at a later date. I pressed return
A similar window appeared asking me something else which I don't remember off-hand. It seamed not so important and I was unable to effect the Y/N at the bottom. So I just closed the window. I logged out selected a system But did not see the kubuntu option. 

I had to go to work so turned off the computer. Ill check tonight to see if it mysteriously appears. I can always uninstall kubuntu using aptitude and then install again (this time using the correct cd if it asks me)but it must be on the system. How can I find it and use it?

Thhanks for your help

The Kubuntu option should be under the WM list, instead of Gnome pick KDE.

---

### Post by ubiubi on 2007-12-06
I'm sorry for my ignorance but what is the "WM list"  ?

---

### Post by ubiubi on 2007-12-06
hi all

Iv' reinstalled for the umpteenth time  (ubuntu) and tried to ude the aptitude commnd to install a new environment. It failed with the following message

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-desktop:~$ 

What does it mean?

Also I installed edubuntu from the package manager and now I've lost ubuntu from the log in page 'options< new session etc...   It seems to have overrided the gnome as a default . On the menue  ebuntu does not exist, so when I click gnome the edubutu environment eppears. I'm completely clueless. Another issue, I tried to install ubuntu, during a previous clean install (successfully as it seems clean installing from my DVD disk allows me to install without problem  ONE environment. The problem arises when I try to install a second! Anyway, under kubuntu I've no idea how to connect to the internet . In the other packages Steve harpers usbadslmodemmanager works just fine. but not in Kubuntu. It keeps giving me a file type error. I don't even know how to activate the menus to find the modem attached. Any ideas. Cheers everyone!

---

### Post by XVII on 2007-12-06
> **ubiubi said:**
> I'm sorry for my ignorance but what is the "WM list"  ?

Window manager.  It's on the login screen under sessions I believe.

---

### Post by maybeway36 on 2007-12-10
> **ubiubi said:**
> hi all

Iv' reinstalled for the umpteenth time  (ubuntu) and tried to ude the aptitude commnd to install a new environment. It failed with the following message

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-desktop:~$ 

What does it mean?

Also I installed edubuntu from the package manager and now I've lost ubuntu from the log in page 'options< new session etc...   It seems to have overrided the gnome as a default . On the menue  ebuntu does not exist, so when I click gnome the edubutu environment eppears. I'm completely clueless. Another issue, I tried to install ubuntu, during a previous clean install (successfully as it seems clean installing from my DVD disk allows me to install without problem  ONE environment. The problem arises when I try to install a second! Anyway, under kubuntu I've no idea how to connect to the internet . In the other packages Steve harpers usbadslmodemmanager works just fine. but not in Kubuntu. It keeps giving me a file type error. I don't even know how to activate the menus to find the modem attached. Any ideas. Cheers everyone!
Put sudo before aptitude.

---

