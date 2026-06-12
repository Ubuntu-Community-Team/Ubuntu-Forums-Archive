---
title: "Any luck with gnome-dock in Edgy?"
date: 2006-11-16
forum: Desktop Environments
---

### Post by daou on 2006-11-16
Has anyone had any luck installing [gnome-dock]("http://www.gnome-dock.org/trac") in Edgy with Beryl? Or Dapper, I've tried both.

I have the dependencies installed (libcairo, libglitz1, libglitz-glx1). It requires a composite manager. I have Beryl/xgl.

Whenever I try to start it with "./cairo-dock" or "./cairo-dock --no-glitz" I get a "Floating point exception" error and it quits.

---

### Post by _SMD on 2006-12-04
It works for me. The only problem i can't get it running on startup.

---

### Post by jeyaganesh on 2007-02-13
Hi for start up-cairo dock, extract this file (in attachment) in where you have cairo-dock. I have it in /opt/cairo-dock. 
1. Download that file
2. open terminal
3. type code sudo mv gnomedock-start.tar.gz /opt/cairo-dock
4. cd /opt/cairo-dock
5. sudo tar -xzf gnomedock-start.tar.gz
Then it extract 'gnomedock-start.sh' file
7. go to System>Preference>Sessions>startup programs>press 'Add'
8. browse to /opt/cairo-dock and click 'gnomedock-start.sh' file to add
9. Close

When next time you switch on your computer you will see the dock. 
I am not expert, i am very new to linux. I just followed [http://ubuntuforums.org/showthread.php?t=302570](http://ubuntuforums.org/showthread.php?t=302570) and [http://www.macewan.org/2007/01/11/how-to-install-cairo-dock-on-ubuntu-edgy/](http://www.macewan.org/2007/01/11/how-to-install-cairo-dock-on-ubuntu-edgy/). Please refer those thread and website if  any problem in my post. 

Have fun :-({|=

---

### Post by Canes on 2007-02-23
I also had some problems with the startup. The startup method using sessions crashes the system.

Try this link : [http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/](http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/)

It explains how to reslove the startup problem.

---

### Post by jeyaganesh on 2007-02-27
I used above mentioned steps in my post and I have no problem with beryl start-up
:popcorn:

---

