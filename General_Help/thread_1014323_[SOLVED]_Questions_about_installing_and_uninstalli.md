---
title: "[SOLVED] Questions about installing and uninstalling programs etc..."
date: 2008-12-17
forum: General Help
---

### Post by hamofgrey on 2008-12-17
Hi,

I am a newbie to linux and I am not sure if this post should go under this section. I am currently readng a book called Quick Start Guide to Unix (3rd Ed) and I would like to know more about how Ubuntu works behind the scenes. 

I have many questions regarding the installation and uninstallation of programs and would be grateful for any replies. The book doesn't cover this very well. I made a list of these questions below, I thought it would be easier to answer this way.

Questions:

[LIST=1]
[*]The packages within the repoistories are not all up-to-date, how can you download the lastest release of a program using the synapic package manager?

[*]Or alternatively how can I update programs that are download using synapic package manager, for example how would I update postgreSQL from 8.2 to 8.3?

[*]If you download a program to a .deb file how can you make it install into the default location which the synapic package manager would of chosen? Or does this happen anyway?

[*]If you uninstall/delete a program using the synaptic package manager does this just completely delete the program? Additionally if a config file was changed by the program does uninstalling the program essentially make this file fallback to it's previous version/configration?

[*]If you install a program using without using synaptic package manager, the manager does not detect it's installation. How do you get the synaptic package manager to detect this?

[*]How do I update programs or utilities such as Java JDK SE and the JVM or is this handled automatically by the update manager?

[*]Do I have to clean up after installations/uninstallations like in Windows?
[/LIST]

I'm sorry for such a list, but I am very interesting in making sure that my system stays very clean, structured and streamlined.

Many Thanks for you answers!

---

### Post by Titan8990 on 2008-12-17
1. Most likely you will have to download the source code and compile yourself.

2. If there are available upgrades: sudo apt-get upgrade
That will upgrade all packages, new kernels will often be left behind.

3. Double click install, it will install where it should.

4. Uninstall does not remove config files. You have to select install and select purge or from the terminal:

sudo apt-get remove --purge PROGRAM

5. You don't

6. Java JDK is in the repositories and should upgrade along with everything else

7. Only when install from methods other than the synaptic package manager.

---

### Post by hamofgrey on 2008-12-17
Regarding Q5:

When you say you don't, is it impossible? Or do you mean it is a waste of time? What would happen if you were to select to install a program in synaptic which had already been installed?

Regarding Q7:

How sould you clean up after uninstalling a program? Do I have to find all the files it used or can you just delete the main directory?

Btw, cheers for the response.

---

### Post by The Cog on 2008-12-17
>    1. The packages within the repoistories are not all up-to-date, how can you download the lastest release of a program using the synapic package manager?
You can't. The nearest you can get is to enable the backports repository and see if someone has ported a later version. This is because when it is released, an Ubuntu versionis feature frozen and only security fixes or really serious bugs are fixed. >    2. Or alternatively how can I update programs that are download using synapic package manager, for example how would I update postgreSQL from 8.2 to 8.3?Hope for backports?>    3. If you download a program to a .deb file how can you make it install into the default location which the synapic package manager would of chosen? Or does this happen anyway?
A .deb file says where a program should be installed. So if you download the .deb file and install it manually, it will install to the same place.
>    4. If you uninstall/delete a program using the synaptic package manager does this just completely delete the program? Additionally if a config file was changed by the program does uninstalling the program essentially make this file fallback to it's previous version/configration?Uninstalling with synaptic leaves the config fiels there. "completely" uninstalling also removes the config files (or so I have read - haven't tested it).
>    5. If you install a program using without using synaptic package manager, the manager does not detect it's installation. How do you get the synaptic package manager to detect this?
If you install a .deb manually, the package manager will know it's there. If you install a different way like compiling from source, I don't think there's any way the package manager can ever know so there will always be a small risk of conflict.
>    6. How do I update programs or utilities such as Java JDK SE and the JVM or is this handled automatically by the update manager? Only for security fixes or updates in the backports repository. In general, an Ubuntu release is a frozen snapshot in time.
>    7. Do I have to clean up after installations/uninstallations like in Windows?
I don't think so. I never bother, but then I always do a fresh install every 6 months when the next Ubuntu release comes out, so I lose any accumulated cruft before it automatically.

---

### Post by hamofgrey on 2008-12-17
Out of interest if I were to install a program using a .bin or .rpm file does this work in the same was as a .deb file?

Will the synaptic detect the installation, like a .deb file?
If you wish to uninstall a program which had been installed using a .bin or .rpm (which I assume that synaptic won't detect) what is the best method of doing this?

---

### Post by oldos2er on 2008-12-17
> **hamofgrey said:**
> Out of interest if I were to install a program using a .bin or .rpm file does this work in the same was as a .deb file?

Will the synaptic detect the installation, like a .deb file?
If you wish to uninstall a program which had been installed using a .bin or .rpm (which I assume that synaptic won't detect) what is the best method of doing this?

 No, *.bin files aren't *debs (and RPMs are for Red Hat and its derivatives, so not applicable to Ubuntu). The package managers won't "see" anything installed from a *.bin. Most *.bin file installations that I've seen include an uninstall script.

---

### Post by jerome1232 on 2008-12-17
You can use alien to turn rpm's into debs but I would exhaust all resources on finding a real deb first. alien is avaible via synaptic.

---

### Post by albinootje on 2008-12-17
> **hamofgrey said:**
> 
[*]Or alternatively how can I update programs that are download using synapic package manager, for example how would I update postgreSQL from 8.2 to 8.3?

Which Ubuntu release are you using ?
PostgreSQL 8.3 is even available in feisty-backports ;-)
[http://packages.ubuntu.com/search?keywords=postgresql-8.3](http://packages.ubuntu.com/search?keywords=postgresql-8.3)

Try this in a terminal to see whether it's available from the repositories that you have enabled :
apt-cache search postgresql|grep 8

---

### Post by CatKiller on 2008-12-17
> **The Cog said:**
> If you install a different way like compiling from source, I don't think there's any way the package manager can ever know so there will always be a small risk of conflict.

You can combine compiling from source with the package management system, using **checkinstall**. You'd use this rather than the *make install* step. It then creates a .deb from the compiled source and installs it. That means that if an updated version of the program becomes available in the repositories, it's easy to update, and if you decide that you don't want the program any more, it's easy to uninstall.

---

### Post by hamofgrey on 2008-12-18
Wow thanks everyone for posting on this thread. It really has made it much clearer to me how the packaging system works.

Oh just for the record I am using Ubuntu 8.10 but used postgreSQL has a random example, I assume that this problem does not exist anymore.

Thanks for your replies

---

