---
title: "Can't OpenOffice 3.0 for Ubuntu 8.10"
date: 2009-04-19
forum: General Help
---

### Post by g35celicaz on 2009-04-19
I just installed ubuntu 8.10 on my laptop two days ago and I was unable to to install OpenOffice 3.0.

The command I put in the terminal window was this:

echo &#8216;deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main&#8217; >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update

But it gave me this:

bash: /etc/apt/sources.list.d/openoffice.sources.list: Permission denied


I got the command from this website:

[http://linuxchronicles.wordpress.com/2009/01/24/10-things-to-do-after-installing-ubuntu-810/](http://linuxchronicles.wordpress.com/2009/01/24/10-things-to-do-after-installing-ubuntu-810/)

Please Help

 - Thanks

---

### Post by cinematography on 2009-04-19
You can only modify your apt sources as a "super" or root user. Typing in 'sudo' before the command should do the trick. However, you might not need to add any additional sources for Open Office. It should already be included in the sources that you have. Try installing Open Office though Add/Remove before tinkering with your apt sources.

---

### Post by g35celicaz on 2009-04-20
I put sudo in front of 

echo ‘deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main’ >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update

But it gave me this:

g35celicaz@g35celicaz-laptop:~$ sudo echo ‘deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main’ >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update
bash: /etc/apt/sources.list.d/openoffice.sources.list: Permission denied
g35celicaz@g35celicaz-laptop:~$ 

What can I do?

---

