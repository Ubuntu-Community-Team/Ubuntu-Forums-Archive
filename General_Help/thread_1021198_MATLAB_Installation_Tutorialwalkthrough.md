---
title: "MATLAB Installation Tutorial/walkthrough"
date: 2008-12-25
forum: General Help
---

### Post by StephenD on 2008-12-25
I have MATLAB R2008a and have installed it in Ubuntu three times.  Each time I had to go to several pages to get it to work the way I want it to so I am writing this for when I need to do it again, and for anyone else who is having similar issues.  I believe that this will work for most versions with minimal adaptation.

Pre Install:
[INDENT][/INDENT]Mount the ISO:
[INDENT][/INDENT][INDENT][/INDENT]sudo mkdir /media/iso
[INDENT][/INDENT][INDENT][/INDENT]sudo mount matlab.iso /media/iso/ -t iso9660 -o loop
Install:
[INDENT][/INDENT]Initial Install:
[INDENT][/INDENT][INDENT][/INDENT]sudo mkdir /opt/matlab
[INDENT][/INDENT][INDENT][/INDENT]sudo cp license.dat /opt/matlab
[INDENT][/INDENT][INDENT][/INDENT]cd /opt/matlab
[INDENT][/INDENT][INDENT][/INDENT]/media/iso/install
[INDENT][/INDENT]Secondary Install:
[INDENT][/INDENT][INDENT][/INDENT]/opt/matlab/install_matlab
Post Install:
[INDENT][/INDENT]Initial run of MATLAB:
[INDENT][/INDENT][INDENT][/INDENT]sudo matlab
[INDENT][/INDENT][INDENT][/INDENT]quit MATLAB
[INDENT][/INDENT]Fix Permissions:
[INDENT][/INDENT][INDENT][/INDENT]sudo chmod a+w -R /home/usr/.matlab/R2008a (usr is your user name)
[INDENT][/INDENT]Make Launcher:
[INDENT][/INDENT][INDENT][/INDENT][I found an icon using this Google search]("http://images.google.com /images?q=matlab%20icon%20png&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wi").  I used "sudo cp..." to copy the icon to the MATLAB directory
[INDENT][/INDENT][INDENT][/INDENT]Right click on the "Applications" menu and select "Edit Menu".  Browse to where you want the launcher and click new item.
[INDENT][/INDENT][INDENT][/INDENT]command: matlab -desktop -r cd\ directory

And you are done.

A note on the last line:
the command to run MATLAB from a launcher is matlab -desktop.  The -r cd\ directory changes the start directory of matlab.  It defaults to /home/usr

Hope this helps.

---

