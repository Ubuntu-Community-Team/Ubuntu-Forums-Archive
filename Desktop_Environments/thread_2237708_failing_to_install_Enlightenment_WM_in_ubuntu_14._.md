---
title: "failing to install Enlightenment WM in ubuntu 14.  help"
date: 2014-08-03
forum: Desktop Environments
---

### Post by John_Walcott on 2014-08-03
Hi guys,

     So I am having some issues with the installation of bodhi desktop in ubuntu 14.04.01 .  So my first issue was that i needed to install a packagekit to my system.  That I got cleared up and installed successfully.  But now I am getting the following error when I do the command:  sudo apt-get install bodhi-desktop

Unpacking e19 (20140729-1) ...
dpkg: error processing archive /var/cache/apt/archives/e19_20140729-1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/enlightenment/data/images/enlightenment.png', which is also in package e17-data 0.17.3-3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

so of course at the end of the install, I get this error

Errors were encountered while processing:
 /var/cache/apt/archives/e19_20140729-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help as to what I need to do would be greatly appreciated.

jwalcott

---

### Post by John_Walcott on 2014-08-03
This is probably in the wrong section, so I am gonna move the thread.

jwalcott

---

### Post by John_Walcott on 2014-08-03
[COLOR=#000000]Hi guys,[/COLOR]

[COLOR=#000000]So I am having some issues with the installation of bodhi desktop in ubuntu 14.04.01 . So my first issue was that i needed to install a packagekit to my system. That I got cleared up and installed successfully. But now I am getting the following error when I do the command: sudo apt-get install bodhi-desktop[/COLOR]

[COLOR=#000000]Unpacking e19 (20140729-1) ...[/COLOR]
[COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/e19_20140729-1_amd64.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/share/enlightenment/data/images/enlightenment.png', which is also in package e17-data 0.17.3-3[/COLOR]
[COLOR=#000000]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]

[COLOR=#000000]so of course at the end of the install, I get this error[/COLOR]

[COLOR=#000000]Errors were encountered while processing:[/COLOR]
[COLOR=#000000]/var/cache/apt/archives/e19_20140729-1_amd64.deb[/COLOR]
[COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

[COLOR=#000000]Any help as to what I need to do would be greatly appreciated.[/COLOR]

[COLOR=#000000]jwalcott[/COLOR]

---

### Post by QIII on 2014-08-03
Threads merged.

Please do not post multiple copies of the the same issue in different areas of the Forums.  It waters down the community's efforts to help by causing people to help in different areas and may cause you confusion.

If you would like a post moved, please ask the Staff to do so by using the "Report Post" button and asking us to move it.

Just FYI:  Enlightenment (which is used by Bodhi Linux) is a Window Manager and not a full-blown DE.  That is a good part of why it is so light.

People have had varying degrees of success in the past installing it.  I wish you all the best.  I use Bodhi on one of my machines and I really like it.


Thanks.

---

### Post by Frogs Hair on 2014-08-03
Some of the instructions for installing the Bodi repository were posted on various Blogs before 14.04 was even released and I see differences in instructions .  I would first make sure the source is current. If you installed E17 from the Ubuntu repository and then added the Bodhi repository you would have both source and package conflicts.

---

### Post by John_Walcott on 2014-08-03
Sorry about the post confusion.  

Ok, so I finally solved the problem, thank god.  And in truth, this should be added to the instructions for installation of the bodhi desktop in ubuntu.

First thing is to make sure that you have the repository universe enabled.  

sudo add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $(lsb_release -sc) universe"

you also need to add the bodhi resources to the list as well.

sudo nano /etc/apt/sources.list

then add the following line to the end

deb [http://packages.bodhilinux.com/bodhi](http://packages.bodhilinux.com/bodhi) trusty main

save the file and update the list

sudo apt-get update

finally, make sure that you install packagekit

sudo apt-get install packagekit

once you do that, you can now install the bodhi desktop with enlightenment

sudo apt-get install bodhi-desktop

A little work but so worth it

jwalcott

---

