---
title: "GNOME desktop on Ubuntu server"
date: 2007-07-07
forum: Desktop Environments
---

### Post by dwilliams07 on 2007-07-07
Hello, I installed the GNOME desktop on my Ubuntu server version 6.06.1.  I did this because I wanted to hurry up and get going on Ubuntu, but I do understand that it was designed to run without a GUI.  I noticed after installing GNOME that I have a lot of programs (OpenOffice, Games, etc).  I would like to remove the unnecessary programs since it will in fact function as a server. When I attempted remove OpenOffice and Games the screen displayed that the Gnome Desktop would also be removed.  Is this true?  Can I not uninstall the programs that come with a default GNOME desktop installation?  If not, it sounds like I'm going to have to go back to the orginal CLI install if I want a true server.  Any help you can give is greatly appreciated.  Thanks

---

### Post by orb9220 on 2007-07-07
> If not, it sounds like I'm going to have to go back to the orginal CLI install if I want a true server. 

What is a true server? Just it not having or having a gui does not make it any more or less a server.

If it is bothering you that they are in the menu you can go to Systems>Preferences>Main Menu and deselect them from showing in the menu.  I mean it is not like they are using any cpu or ram being there in the menu.

And yes you can unistall them and then there is a command you can run to reinstall gnome-desktop I just can't remember at the moment due to low Caffeine levels need more java.

---

### Post by dwilliams07 on 2007-07-07
Thanks!  I had always heard that one of the strengths of Linux server was that it did not inlcude a lot of unnecessary programs and other "stuff" that would require keeping up with updates.  You are right though...I could just make those programs not appear in the menus.  I'm new and still learning about Linux.  Thanks for your help.

---

### Post by Warp-The Doctor on 2007-07-07
Actually, gnome-desktop is a meta-package which is "pulling" all the necesary packages for a complete gnome desktop system for typical usage, therefore if you remove something which was "pulled" by the gnome-desktop,it will remove gnome-desktop either,because it depends on the removed package..so you can remove it without any hesitation, it won't remove actually anything=)

---

