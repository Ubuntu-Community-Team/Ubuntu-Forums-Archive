---
title: "Password on vmware image of Dapper Drake 6.06"
date: 2009-11-18
forum: Desktop Environments
---

### Post by mezhaka on 2009-11-18
Dear All,

In short: 
What's the sudo password for that ([http://isv-image.ubuntu.com/vmware/Ubuntu-6.06-desktop-i386.zip]("http://isv-image.ubuntu.com/vmware/Ubuntu-6.06-desktop-i386.zip")) image.

In detail:
I need to run the 6.06 version of ubuntu. The only desktop edition I've found so far was at the [http://isv-image.ubuntu.com/vmware/]("http://isv-image.ubuntu.com/vmware/") -- the vmware image (particularly I used [this one]("http://isv-image.ubuntu.com/vmware/Ubuntu-6.06-desktop-i386.zip")). I ran it with vmplayer, but now as I try to do sudo apt-get install g77 I get a password prompt. I don't know the password...
I've tried to set it doing sudo passwd

---

### Post by mezhaka on 2009-11-19
Haven't found a password, but figured out how to change root password. So I still can't do sudo, but I can do su and then install all the packages I need as a root.

Just select recovery mode, in the GRUB boot menu and it will log you in as a root. Then run passwd to change the password. Then boot as usual and in the terminal you can run su to become root.

---

