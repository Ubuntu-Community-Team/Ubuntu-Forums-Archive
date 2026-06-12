---
title: "how to disable remote login screen at local site in ubuntu"
date: 2009-08-12
forum: Desktop Environments
---

### Post by anadeem.ch on 2009-08-12
Dears Hi 
I enabled remote login on my ubuntu machine. and restarted to check the affects. after restart, instead of going to the user name page , I got the page giving the information serving remote login and in the main area there is my(local machine) so I click connect after selecting the machine name. it then executes rc.local and asks for the user name and then password. I want to skip the screen of remote login. how can i do that( Actually I want to disable remote login but when i disable it. I get "no host is serving " and I cannot get login to the machine. for that i go to ctrl+Alt+F1 and start the X server on display 1( on 0 it is already running). and i get GUI of my login. I disable the remote login from command line
 gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
 to disable the remote login but when i open "gdmsetup" remote login is not disabled. it means these are two different tasks. So how will i get the local login screen directly( as we normally get)
 A.Nadeem

---

