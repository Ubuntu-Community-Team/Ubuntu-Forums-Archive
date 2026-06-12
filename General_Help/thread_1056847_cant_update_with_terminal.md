---
title: "cant update with terminal"
date: 2009-02-01
forum: General Help
---

### Post by death356 on 2009-02-01
hey ive been using fedora for a while and i decided to switch to ubuntu just today but when i finaly got it installed i couldnt download any packeges with apt-get. i can update fine but if i try to get xmms for example it says the file isnt ther and if i do a manual install it stops half way through please help. i may be a noob but im good at learning

---

### Post by yoyoned on 2009-02-01
be sure you are using sudo

paste the command you are using and it's output into the forum.

---

### Post by death356 on 2009-02-01
i used su - instead
i just tryed sudo and got this response
 sudo apt-get install xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidate

its the same as su -

---

### Post by fooman on 2009-02-01
i don't believe there is a package called just "xine".  maybe you are looking for xine-ui ?

try this:

```
sudo apt-get install xine-ui
```

---

### Post by death356 on 2009-02-01
i might be i havent used ubuntu in almost a year but the last time i used it i didnt have any problems... it may just be that im used to yum from fedor and red hat...
the code you gave me made no change i am looking at a guide on updating the repositories

---

### Post by sisco311 on 2009-02-01
Try to enable the extra repositories:
[uhelp]community/Repositories/Ubuntu[/uhelp]
and for xmms:
[uhelp]community/XMMS[/uhelp]

---

### Post by fooman on 2009-02-01
try using synaptic? ...system > administration > synaptic package manager

maybe the packages are named differently in ubuntu....use the search feature in synaptic to get the correct names of the packages your trying to install.

---

### Post by death356 on 2009-02-01
i used the package manager and was able to find xmms but not xine.
also i cant install the adobe flash player is ther any way to enable yum witch im more familiar with?

---

### Post by fooman on 2009-02-01
try this in a terminal and post back with the output:

```
sudo apt-get install xine-ui
```

---

### Post by death356 on 2009-02-01
in my above post about sudo i mentioned that i tryed it youre way for the same result the output is all ther

---

### Post by fooman on 2009-02-01
open synaptic,  in the toolbar,  click settings > repositories

when that opens,  click the ubuntu software tab and put check marks next to the first 4 choices (main - universe - restricted - multiverse).  close that box and you will see a warning that the repos have changed.  close that  box and click the "reload" button in the toolbar.

now search again for "xine-ui" and see if it is there.

---

### Post by Tomatz on 2009-02-01
Go to ***System, Administration, software sources*** and check that the repository's are enabled as sometimes they disable if you install with no configured network ;)

---

### Post by death356 on 2009-02-01
my biggest isue is flash player because i publish flash videos on the computer is ther an easy way to install it i tryed the adobe site and apt-get with a comand line i found and neither worked

---

### Post by fooman on 2009-02-01
installing the "ubuntu-restricted-extras" package will install flash.  could also install "flashplugin-nonfree"

---

### Post by death356 on 2009-02-01
i did what you said with synaptic and hers the output

 sudo apt-get install xine-ui
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by fooman on 2009-02-01
do you have synaptic open?

close it,  then try in a terminal again.

---

### Post by death356 on 2009-02-01
yeah i am installing ubuntu-restricted-extras now thanks for the tip this will make things alot easier but apt-get still wont work right

---

### Post by death356 on 2009-02-01
ill try that as soon as its done with the ubuntu-restricted-extras package

---

### Post by death356 on 2009-02-01
that did the trick thanks for the help

---

### Post by fooman on 2009-02-01
see the following page for info about adding the medibuntu repositories:

[U][https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


[/U]

---

