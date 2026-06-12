---
title: "Help with broken source.list file plzy."
date: 2005-12-18
forum: General Help
---

### Post by cramlow on 2005-12-18
Greetings and lo-haz, 

Me did bad one people.  I went to the help area where it told me this kind of stuff -
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list



So I did and now I get this - 

cramlow@ubuntu:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package w32codecs
cramlow@ubuntu:~$


It messed up my apt-get so now when I go to apt-get something or add a new app via the applcation adder it cannot retrieve all the files.   When I went to install kaffinee I got this -

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)


Pleasy helpy

:p

---

### Post by aysiu on 2005-12-18
See the first link of my sig.

---

### Post by cramlow on 2005-12-18
Thank you.  I learned a lot form your website.  Can you help me get w32codecs installed on my ppc version of the latest ubuntu?  It seems there isnt one available through the apt install way of installing things.

Some one else pointed me to this - But i have little idea what to do :( 


Extract it and have a look at the README file. Try copying to codecs to the directories mentioned there. They are outside of your home directory so you need to use this command in terminal
Code:

sudo nautilus


They are for mplayer so you might need to use that (not sure). Search synaptic for mplayer.

Thank you

---

