---
title: "Open Office update gone bad in 8.10 (help)"
date: 2009-05-10
forum: General Help
---

### Post by pjmed on 2009-05-10
I am currently running 8.10 and have attempted to upgrade Open Office to the newest version. I followed the instruction listed in this web page:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Everything went according to the instructions until I got to STEP 2. At this point something about Open Office appears on the Update Manager but it is grayed out and can't be check marked. OO has been removed from the Applications list. Also if I go to Add/Remove and check Openoffice.org Office Suite I get the following message:

Cannot install 'openoffice.org'

This application conflicts with other installed software. To install 'openoffice.org' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Can anybody help? I am new to Ubuntu and Linux so I really don't understand what I did wrong. Thanks in advance.

---

### Post by pytheas22 on 2009-05-11
Please open a terminal, run these commands and post the output:
```

sudo apt-get update
sudo apt-get upgrade

```

This should provide more feedback that will help to figure out what's wrong.

---

### Post by pjmed on 2009-05-11
sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/main Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                       
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid Release                   
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/main Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/main Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/universe Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/universe Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome
  openoffice.org-gtk python-uno
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by pjmed on 2009-05-11
By the way, thanks for replying I hope I can fix the problem with your help.

---

### Post by pytheas22 on 2009-05-11
hmmm, I'm not sure why it wants to hold those packages back.  You might be able to solve the problem easily by just removing OpenOffice by typing:
```

sudo apt-get remove openoffice.org
```

Then install it again with:
```

sudo apt-get install openoffice.org
```

Does this work?

---

### Post by pjmed on 2009-05-11
THANKS! 
I just looked under Applications and I have OO again.  Better yet, it appears to be the latest version. Thanks for the help.
By the way I do have a minor problem with my trackpad which you might know how to fix. My problem is that in order to drag a window or file I have to double tap the trackpad in a way that you have to slide the finger on the second tap or you won't grab anything. You also have to do it very fast. Thanks again for the help.

---

### Post by pytheas22 on 2009-05-11
I'm glad OpenOffice is fixed.  As for the trackpad, the only thing I can say is try going to System>Preferences>Mouse and see if changing some of the options there might help--you might be able to increase the delay for the second tap, for example.  I'm on a desktop so I don't really know much about trackpads and Ubuntu.

---

### Post by pjmed on 2009-05-11
I have already tried everything in the mouse settings. But thanks for your help with Office, really.

---

