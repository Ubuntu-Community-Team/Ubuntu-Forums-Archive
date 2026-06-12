---
title: "AD-LDAP Auth and Software Center/Software Updater"
date: 2015-11-13
forum: Desktop Environments
---

### Post by mstjohn1974 on 2015-11-13
I am working on a procedure for my Company to set up Ubuntu Desktops that will authenticate against a Windows Active Directory Server. I was able to get the Desktop Logon, sudo and ssh access configured to authenticate against AD. I used a procedure written up at [http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/%5Btutorial%5D-ad-integration-with-ubuntu-14-04-and-winbind-4175516531/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/%5Btutorial%5D-ad-integration-with-ubuntu-14-04-and-winbind-4175516531/) and it works like a charm. The only thing so far left is to get the Ubuntu Software Center and Software Updater to work with it as well. Right now when I install something it wants to authenticate with the installation user that  you have to set up during the initial Ubuntu installation. 

Thanks for the help much appreciated

MSJ

---

### Post by mstjohn1974 on 2015-11-16
I guess I figured out an acceptable workaround.
I installed gksu with **sudo apt-get install gksu** from the CLI
then I went ahead and edited three files located under **/usr/share/applications/** ubuntu-software-center.desktop, updatemanager.desktop and system-config-printer.desktop. 
at the line that starts with exec= I added gksudo right after the = sign and in front of the command itself for example:

from exec=system-config-printer  to exec=gksudo system-config-printer

saved it and tried it. Now it will asks every time for authentication which is just fine.

Hope you guys like that solution.

---

