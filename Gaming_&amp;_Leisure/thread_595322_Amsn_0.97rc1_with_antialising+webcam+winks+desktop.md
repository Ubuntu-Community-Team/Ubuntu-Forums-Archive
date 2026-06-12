---
title: "Amsn 0.97rc1 with antialising+webcam+winks+desktop integration installation script"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by gsiliceo on 2007-10-28
[SIZE="7"]PLEASE DO NOT USE THIS SCRIPT, THERE IS AN OFFICIAL PACKAGE IN THE AMSN WEBPAGE WITH THE LATEST STABLE VERSION.[/SIZE]

Hi everyone, i picked up this **script to install aMSN 0.97rc1 with winks, webcam, antialising and desktop integration**. in the spanish ubuntu forums and found it extremenly usefull. I translated it and added chameleon plugin support(for better desktop integration)

**It works in gutsy gibbon.**

*It's just a compilation of commands that you need to do to compile it, but makes it easy because you just have to input your password a few times and nothing else.*

You just need to download it to your user folder, give it executing privileges(right click on the **icon>properties>permisions/privileges>allow execution**) and then in the terminal do.

> ./aMSN_Installer.sh

Hope some of you find it useful.

You probably want to use these packages.

[http://ubuntuforums.org/showthread.php?t=649364](http://ubuntuforums.org/showthread.php?t=649364)

---

### Post by Crushyerbones on 2007-11-24
Works fine so far :D I'm yet to test winks and suck tough.

---

### Post by manbish on 2008-01-06
I have downloded the suggested file to desktop.  When I right click, it only gives me read and write permissions and not execute.  (Running xubuntu 7.10).  Cannot save to any of the system files as I have no permission as user.  Need to be root.  I am happy running scripts as root in terminal.
a.  Where does the download need to be saved?
b, Is there a terminal enrty I can make to put it in the correct place?
c. Do I need to have also downloaded other aMSN files before I run Install.sj?

Thank you?

---

### Post by patrickfromspain on 2008-01-07
why does everybody want a script when there are packages?

[http://ubuntuforums.org/showthread.php?t=649364](http://ubuntuforums.org/showthread.php?t=649364)

---

### Post by manbish on 2008-01-07
The packages are great, but (if you read my post above), if I cannot follow the instructions because the sstated options are not available, then I need another means of making things work.  You need to use terminal on a number of packages in order to correct errors, ie mcop error in ZSNES.

---

### Post by manbish on 2008-01-07
> **manbish said:**
> The packages are great, but (if you read my post above), if I cannot follow the instructions because the sstated options are not available, then I need another means of making things work.  You need to use terminal on a number of packages in order to correct errors, ie mcop error in ZSNES.

I should also add that I cannot run aMSN using the package option except by opening the terminal and logging in as root.  If I subsequently close the terminal, aMSN also closes.  Who needs script?  Me!

---

### Post by manbish on 2008-01-07
> **gsiliceo said:**
> Hi everyone, i picked up this **script to install aMSN 0.97rc1 with winks, webcam, antialising and desktop integration**. in the spanish ubuntu forums and found it extremenly usefull. I translated it and added chameleon plugin support(for better desktop integration)

**It works in gutsy gibbon.**

*It's just a compilation of commands that you need to do to compile it, but makes it easy because you just have to input your password a few times and nothing else.*

You just need to download it to your user folder, give it executing privileges(right click on the **icon>properties>permisions/privileges>allow execution**) and then in the terminal do.





Hope some of you find it useful.

You probably want to use these packages.

[http://ubuntuforums.org/showthread.php?t=649364](http://ubuntuforums.org/showthread.php?t=649364)

OK, thanks.  I see how this works now, but I am prompted to insert Xubuntu 7.10 installation CD-ROM.  I installed from a bootable USB which named itself deifferently from the installation CD.  I don't have an external CD-ROM, and the terminal script won't accept the USB.  Any ideas?  I'm using an EEE 701 PC (4G).

Thanks.

---

### Post by gsiliceo on 2008-01-07
OK, go to SYstem > Administration > Software origins(or sources?) > input your password > Unclick cdrom from the list > say yes when promted to update

---

### Post by manbish on 2008-01-07
Thank you, that works a treat and aMSN is installed with the script provided above.  I have used the aMSN help site to forward the ports (camera and files through the firewall).  Yet to test camera live!?!  I still need to login as root to run.  jax on [http://forum.eeeuser.com/viewtopic.php?id=8610](http://forum.eeeuser.com/viewtopic.php?id=8610) suggested I run sudo chmod 755 /usr/bin/amsn , which is the correct file location, but to no avail.  The file is not listed as 'executable', but 'linked to shell script' instead.

Does anyone know of any ways of getting the programme to launch directly from the desktop?  Properties are that the owner is root and that user has read, write permissions.  A further file property is that the aMSN file is 'ticked' to 'run as a programme' in the permissions tab.

Thanks

---

### Post by Aragorn_hun on 2008-01-08
Thanks, finally my aMsn is working fine

---

### Post by tatojo on 2008-07-11
Thanks, it ran smoothly. But can't configure sound. Amsn says snack is not installed, but it is! How can get it alive?

---

### Post by ELD on 2008-07-11
Guys this post is getting really old now, the official .71 has been out for a long time and has a package on their website, you should use that.

---

### Post by LaRoza on 2008-07-11
Closed by OP's request.

---

