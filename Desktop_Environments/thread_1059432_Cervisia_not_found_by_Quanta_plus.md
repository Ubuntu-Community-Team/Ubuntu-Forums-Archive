---
title: "Cervisia not found by Quanta plus"
date: 2009-02-03
forum: Desktop Environments
---

### Post by Cerox Rex on 2009-02-03
When trying to run Cervisia from inside Quante this error pops up.

> The CVS Managment (Cervisia) plugin could not be loaded.
Possible reasons are:

-CVS Managment (Cervisia) is not installed
-the file kde3/libcervisiapart.la is not installed or is not reachable. 

Whne doing a file search for the above mentioned file (as i have Cervisia installed and can run it from outside Quanta) its nowhere to be found on my drives.

I'v tried every cervisia package i can find at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
I'v tried -- sudo apt-get install kdesdk
and to manualy install kdesdk-4.2.0 wich gave thefollowing results:

--cmake . (no errors)
--make    (gave following output)
> hallvar@pavilion:~/kdesdk-4.2.0$ make
Generating plugin.moc                
Generating kateapp.moc                                                          
Generating katemainwindow.moc                                                   
Generating katefilelist.moc                                                     
Generating application.moc                                                      
Generating katepluginmanager.moc                                                
Generating pluginmanager.moc                                                    
Generating pluginconfigpageinterface.moc                                        
Generating katedocmanageradaptor.moc                                            
Generating mainwindow.moc                                                       
Generating katesession.moc                                                      
Generating katemdi.moc                                                          
Generating katecontainer.moc                                                    
/home/hallvar/kdesdk-4.2.0/kate/app/katecontainer.h:36: Error: Undefined interface                                                                              
automoc4: process for /home/hallvar/kdesdk-4.2.0/kate/app/katecontainer.moc failed: Unknown error                                                               
pid to wait for: 0                                                              
Generating kateviewmanager.moc                                                  
Generating kateappadaptor.moc                                                   
Generating kateconfigplugindialogpage.moc                                       
Generating documentmanager.moc                                                  
Generating kateviewdocumentproxymodel.moc                                       
Generating katemainwindowadaptor.moc                                            
Generating kateconfigdialog.moc                                                 
Generating katesavemodifieddialog.moc                                           
Generating katemwmodonhddialog.moc                                              
Generating kateviewspace.moc                                                    
Generating katedocmanager.moc                                                   
returning failed..                                                              
make[2]: *** [kate/app/kateinterfaces_automoc.cpp] Error 1                      
make[1]: *** [kate/app/CMakeFiles/kateinterfaces.dir/all] Error 2               
make: *** [all] Error 2                                                  

I run a Kubuntu 8.10 install.

---

### Post by Primefalcon on 2009-02-04
Having the same issue myself atm tried doing a reinstall of cervisia without any luck

---

### Post by Cerox Rex on 2009-02-04
anoyone hava an ide on how to find and place > libcervisiapart.la
in its correct folder? > /usr/lib/kde3

or is there som way to install only cervisia from the kdesdk-4.2.0 pacakge?

---

### Post by mistypotato on 2009-02-08
Same problem here.

---

### Post by Tips on 2009-03-05
I'm having this same problem. Ubuntu 8.10 with Quanta & Cervisia installed. I also installed KDE but that didn't help.

There's a bug report here, but no reply:
[https://bugs.launchpad.net/ubuntu/+source/kdewebdev/+bug/299869](https://bugs.launchpad.net/ubuntu/+source/kdewebdev/+bug/299869)

---

### Post by t_ras on 2009-03-15
KDE 4.2
I failed to installed Quanta at all, it was looking for kde3 version of some applications (kfilereplace and such, not servicia). 
Any way to install Quanta on KDE 4.2?
I'm using Screem right now, but I like Quanta better.

---

### Post by t_ras on 2009-03-15
OK, it seems they have lack of developers, so it is going to take some time.

---

### Post by marc.cardo on 2009-03-22
The same problem here too

---

### Post by horusofoz on 2009-07-03
Same problem here

---

### Post by MattyDread on 2009-07-24
I also get this. It also crashes whenever I try to add a folder to a project - even if it's empty.. I was looking forward to playing around with Quanta Plus but I'm having no luck getting it to work.

---

### Post by Primefalcon on 2009-07-24
just as an added note this is also still happening as of Ubuntu 9.04 too, hope karmic fixes this

---

### Post by panther_21 on 2009-11-05
I have karmic and it is still an issue

---

### Post by nutznboltz on 2010-10-24
This appears to have been solved:
[http://ubuntuforums.org/showthread.php?t=1003635](http://ubuntuforums.org/showthread.php?t=1003635)

---

### Post by Primefalcon on 2010-10-24
> **nutznboltz said:**
> This appears to have been solved:
[http://ubuntuforums.org/showthread.php?t=1003635](http://ubuntuforums.org/showthread.php?t=1003635)
Be nice to have it automatic though, tbh I stopped using quanta quite a while ago because of these issues though

---

### Post by rmil on 2011-09-25
Easy solution:

locate in terminal where is the location of cervisiapart.so with command

**locate cervisiapart.so**

for me it was /usr/lib/kde4/cervisiapart.so

Under Settings menu in Quanta configure plugins for CVS cervisia by changing its path accordingly.

Worked for me.

---

