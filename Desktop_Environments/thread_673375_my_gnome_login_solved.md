---
title: "my gnome login solved"
date: 2008-01-20
forum: Desktop Environments
---

### Post by trakie on 2008-01-20
Since I spent this whole weekend dealing with this problem I thought I would post here to let anyone who wants to know what I did to correct the problem(s)...

system config (its a beast):
intel quad core
4gb ram
3 hard drives: 
-80gb for os installs of:
    -windows: 50GB
    -Ubuntu 20GB 
    -the rest for swap
-500gb for /home
-500gb split as:
    -~200GB ext3
    -~300GB ntfs
nvidia 8800gt 

that was my configuration before, then one day (friday) i had a problem logging in to gnome, i would start fine and get to the login screen fine, then log in and it would go for about 2 seconds before it returned to the login screen.  ugh.  i tried deleting /home/$username$/.gnome .gnome2 .gconfd, to no avail, same problem.  i tried some other things and figured i might as well reinstall.  so i try to reinstall, for some reason my livecd doesnt work anymore, i burn 3 more and none of those work, ughhhh.  

i move on to trying fedora core 8, it installed fine, but i just didnt like it after ubuntu, especially whenever i looked online to do something the first 3 or 4 results were always for ubuntu, even thought i typed fedora in the search...

started from scratch with an alternative install cd, which worked!
unfortunately i had the same problem when logging into gnome, however this time after login it gave an error saying i was logged in for less than 10 seconds and to review some log, i took a look and there was a problem with .gnome2_private or something.  so i delete that with sudo rm -r .gnome2_private, and problem solved! (well sort of), my home directory was not my own again, so i had to CTRL-ALT-F1 and log in and do:  sudo chown -R /home  
which worked to my surprise, and then i logged in and it worked, well i had to install the nvidia driver but i found multiple sites explaining how to do that easily.

all in all, i wasted a few days installing and resizing partitions when all i really had to do was delete .gnome2_private in the first place, im still not sure what went wrong or why this fixed it, but i am posting this so if anyone else encounters similar problems, or if this happens to me again in the future i can find out what i did to solve the problems.  

also sorry if this already overlaps someone elses gnome login problem, but i looked at about 5 or 6 and none of them were for the same reason as my problem...

---

