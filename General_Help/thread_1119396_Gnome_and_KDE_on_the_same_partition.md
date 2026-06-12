---
title: "Gnome and KDE on the same partition"
date: 2009-04-07
forum: General Help
---

### Post by eruptionjoojo on 2009-04-07
Hello everyone,

                     Ok .............. Let me first tell you as to what all i have already done :-
                                  I was having Kubuntu(8.10) 32 bit version.


I wanted to have Kubuntu and Ubuntu on the same drive ............ as i had read about doing it in a similar thread just by installing the Ubuntu-desktop using the Adept Package Manager ............ so i tried doing it ............  after the download was complete Adept package manager had asked to keep which as mine default one i.e.KDE or Gnome and i had selected the KDE option.............but due to some reasons (Due to power failure) while the ubuntu-desktop was getting installed i had to close the Adept Package Manager(installation process) so as a result the installation was not complete and interrupted inbeetween.........
                                


After a while i restarted my computer and everything was working fine i mean i was able to boot into Kubuntu successfully .......... but then since i wanted to have both Kubuntu and ubuntu on the same drive so i re-tried installing the Ubuntu-desktop using the Adept package manager at first it showed some error (i don't remember exact) but it was like it was recovering from last incomplete installation but then it displayed that it has successfully re-covered and then i installed the ubuntu-desktop  which got installed without any problem .....
                   


Then in order to check i restarted my computer and Kubuntu desktop seemed loading as the Kubuntu loading screen which contains Kubuntu written over and the bar getting filled from hollow was displayed ..........but the desktop which got loaded was Gnome i.e. ubuntu .......... now while i retried by re-starting my computer but each time the same happens ............ while on the contrary i suppose i must be provided the option as to which one to load i.e. GNOME or KDE .........


so this is what the problem is .......... 
                                        





 now i want to restore my KDE and have a option going in as to whether to load KDE or GNOME ............
thnxx in advance ..........

---

### Post by dcstar on 2009-04-08
> **eruptionjoojo said:**
> Hello everyone,
........
 now i want to first of all r**estore my KDE and have a option going in as to whether to load KDE or GNOME** ............
thnxx in advance ..........

First, please learn how to use paragraphs to make anything you want to communicate legible.

Second, a forum search will bring up many items on your question.

---

### Post by mb_webguy on 2009-04-08
I got one line into your post before it induced a migraine, but I think you want to use both Gnome and KDE.  If that's the case, all you have to do is install both the ubuntu-desktop and kubuntu-desktop packages (one of which you should already have installed, unless you started with Xubuntu).  Then, at the login screen, click Options in the bottom left corner, then Select Session to choose whether you want to use Gnome or KDE once you login.

---

### Post by SunnyRabbiera on 2009-04-08
you dont need two different partitions for each DE

---

### Post by eruptionjoojo on 2009-04-08
> **mb_webguy said:**
> I got one line into your post before it induced a migraine, but I think you want to use both Gnome and KDE.  If that's the case, all you have to do is install both the ubuntu-desktop and kubuntu-desktop packages (one of which you should already have installed, unless you started with Xubuntu).  Then, at the login screen, click Options in the bottom left corner, then Select Session to choose whether you want to use Gnome or KDE once you login.

sorry to have made you suffer from migraine .... 
hopefully you are alright now .....
and yeah you are totally correct as to what i was referring to  ...........


but i don't get the login screen because i have enabled auto-login .......... i tried to change the setting of login via login manager but as of now the login manager is not responding and seems to hang ...........


thus i'm unable to make the change ..........

---

### Post by eruptionjoojo on 2009-04-09
> **eruptionjoojo said:**
> sorry to have made you suffer from migraine .... 
hopefully you are alright now .....
and yeah you are totally correct as to what i was referring to  ...........


but i don't get the login screen because i have enabled auto-login .......... i tried to change the setting of login via login manager but as of now the login manager is not responding and seems to hang ...........


thus i'm unable to make the change ..........

in order to disable auto-login ............ i got the answer in another forum as follows :-


As root edit /etc/kde4/kdm/kdmrc maybe
sudo kate /etc/kde4/kdm/kdmrc
and at about line 252 you will find
AutoReLogin=true
Comment it
# #AutoReLogin=true
and restart the X server.

and this did the job thnxx everyone ...........

---

