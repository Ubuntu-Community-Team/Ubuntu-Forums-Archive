---
title: "[SOLVED] Add/Remove applications doesn't show any applications"
date: 2008-12-24
forum: General Help
---

### Post by andresmh on 2008-12-24
For some reason "Add/Remove Application" is not showing any applications: 
"There is no matching application available"

I made sure the search field is empty and I even tried changing the  drop-down to "All available applications", "Installed applications" and everything in between. 

It also is not showing any categories on the left pane as it used to.


[[IMG]http://img166.imageshack.us/img166/5918/screenshotaddremoveapplsf9.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotaddremoveapplsf9.png)

The Software Sources are shown here:

[[IMG]http://img152.imageshack.us/img152/2524/screenshotsoftwaresourcoe1.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshotsoftwaresourcoe1.png)


[[IMG]http://img126.imageshack.us/img126/6982/screenshotsoftwaresourcuh7.th.png[/IMG]](http://img126.imageshack.us/my.php?image=screenshotsoftwaresourcuh7.png)
What can I do?

---

### Post by kostkon on 2008-12-24
First of all, open a terminal and do
```
sudo apt-get update
```
and check if you get any errors.

Also, try to run *Add/Remove* from the terminal, like this
```
gnome-app-install
```
and check again for any errors that you may get.

---

### Post by 2hot6ft2 on 2008-12-24
Did you just install Adobe Air and the new BBC iPlayer Desktop? Seems to be happening a lot lately.

try reinstalling gnome-app-install


```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by andresmh on 2008-12-24
There is only a warning when running from the comand line:

```

andresmh@ibex300:~$ gnome-app-install
** (gnome-app-install:7361): WARNING **: return value of custom widget handler was not a GtkWidget

```

No errors show up when doing sudo apt-get update:

```

andresmh@ibex300:~$ sudo apt-get update
[sudo] password for andresmh: 
Ign http://www.openprinting.org lsb3.2 Release.gpg
Ign http://www.openprinting.org lsb3.2/postscript-hp Translation-en_US                                                                       
Get:1 http://www.openprinting.org lsb3.2 Release [26.2kB]                                                                                    
Ign http://ppa.launchpad.net intrepid Release.gpg                                                                                            
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                                                           
Ign http://www.openprinting.org lsb3.2/postscript-hp Packages                                                    
Hit http://archive.canonical.com intrepid Release.gpg                                                            
Ign http://archive.canonical.com intrepid/partner Translation-en_US                        
Hit http://deb.opera.com stable Release.gpg                                                
Ign http://deb.opera.com stable/non-free Translation-en_US                                                       
Hit http://archive.ubuntu.com intrepid Release.gpg                                                               
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                                                    
Hit http://www.openprinting.org lsb3.2/postscript-hp Packages                                                    
Ign http://ppa.launchpad.net intrepid Release.gpg                                                                
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                               
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://archive.canonical.com intrepid Release                                                 
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US                      
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US    
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US  
Hit http://archive.ubuntu.com intrepid-updates Release.gpg           
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://deb.opera.com stable Release                                                    
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]                                   
Hit http://archive.ubuntu.com intrepid Release                       
Hit http://archive.canonical.com intrepid/partner Packages                                                      
Ign http://deb.opera.com stable/non-free Packages                                          
Ign http://ppa.launchpad.net intrepid/main Packages                  
Ign http://ppa.launchpad.net intrepid/main Sources                   
Hit http://archive.ubuntu.com intrepid-updates Release               
Hit http://archive.canonical.com intrepid/partner Sources                                  
Hit http://deb.opera.com stable/non-free Packages                                          
Ign http://ppa.launchpad.net intrepid/main Sources                   
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid/universe Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/universe Sources
Hit http://archive.ubuntu.com intrepid/multiverse Packages
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Fetched 3B in 2s (1B/s)
Reading package lists... Done

```

---

### Post by andresmh on 2008-12-24
Reinstalling gnome-app-install worked! :) Thanks 2hot6ft2

---

### Post by 2hot6ft2 on 2008-12-24
You're welcome. Once you finish and are satisfied that this solved your problem please mark your thread as solved by clicking on Thread Tools at the top of the thread and selecting Solved.

Since some of us just go thru the threads trying to help those that need it.
It would help us save time by not going thru ones that have already been solved and it also helps others with the same issue find a quick solution to their issue by looking at the ones that have been solved.

---

### Post by hotweiss on 2008-12-31
> **2hot6ft2 said:**
> Did you just install Adobe Air and the new BBC iPlayer Desktop? Seems to be happening a lot lately.

try reinstalling gnome-app-install


```
sudo apt-get --reinstall install gnome-app-install
```

Thanks that worked for me too.

---

