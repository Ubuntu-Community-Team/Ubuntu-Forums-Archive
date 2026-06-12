---
title: "How to 're-master' ubuntu 10.04"
date: 2010-10-07
forum: Desktop Environments
---

### Post by lukaswrites on 2010-10-07
Hi guys, 

I am new guy here, and I've got something to ask. I have one PC with Ubuntu 10.04 LTS installed, and so far I've configured it and installed it with so many packages and settings. Now, that I want to install the same Ubuntu version on my Notebook. The question is : Can I 're-master' my Ubuntu on my PC with all of the packages, settings and drivers installed? so I will have an ISO file complete with all of those packages and I just install it to my notebook without having to re-installing the packages? thanks

---

### Post by tsinelas30 on 2010-10-07
What do you mean "re-master" is it cloning?

We need to wait for ubuntu masters to reply, me too needs to know how to clone ubuntu.

---

### Post by lukaswrites on 2010-10-08
> **tsinelas30 said:**
> What do you mean "re-master" is it cloning?

We need to wait for ubuntu masters to reply, me too needs to know how to clone ubuntu.

not exactly as cloning, but a ISO file which contains all the installed packages and drivers

---

### Post by ankspo71 on 2010-10-08
Hi,
There are a few tools out there, but I think the easier one would be remastersys [http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html) Be sure to read the Home, Ubuntu and Information pages for more details.

If all you want to do is create a cd of your installation (Ubuntu plus your packages and updates) then using remastersys is relatively easy.

However, if you want to use the same desktop settings and application settings, you will need to copy parts of your home directory to /etc/skel then change their permissions to root. This part I haven't actually tried myself, but this step is explained on the Information page in the link above. See the part that says: "COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS". That section contains sample commands to use.

Don't forget that it is important to remove your application's passwords, for just in case you decide to share your creation.

The newly created iso will be located in its own home folder, located at /home/remastersys/...*.iso

Hope this helps.

---

### Post by LinksPatrocinados on 2010-10-08
You need a complete remaster or just put the most common drivers ?

---

### Post by Dustin2128 on 2010-10-08
you may be interested in [linux mint]("http://www.linuxmint.com"); its an ubuntu spin-off that comes with almost everything you'd need out of the box.

---

### Post by lukaswrites on 2010-10-08
> **ankspo71 said:**
> Hi,
There are a few tools out there, but I think the easier one would be remastersys [http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html) Be sure to read the Home, Ubuntu and Information pages for more details.

If all you want to do is create a cd of your installation (Ubuntu plus your packages and updates) then using remastersys is relatively easy.

However, if you want to use the same desktop settings and application settings, you will need to copy parts of your home directory to /etc/skel then change their permissions to root. This part I haven't actually tried myself, but this step is explained on the Information page in the link above. See the part that says: "COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS". That section contains sample commands to use.

Don't forget that it is important to remove your application's passwords, for just in case you decide to share your creation.

The newly created iso will be located in its own home folder, located at /home/remastersys/...*.iso

Hope this helps.

I've used remastersys , but why the cdfs size is too large? it exceeds 20gb? and when the process is nearly over, it informs me that it can't build the iso due to the overlapping size

---

### Post by ankspo71 on 2010-10-08
> **lukaswrites said:**
> I've used remastersys , but why the cdfs size is too large? it exceeds 20gb? and when the process is nearly over, it informs me that it can't build the iso due to the overlapping size

Installing and running the system cleaner called bleachbit can clean up a few GB's or more on some systems. 

Some games can take up alot of room, so you might want to remove some of the larger ones.

If you are someone who compiles their own packages, removing the no longer needed *-dev packages and any extra source codes etc would probably clear up alot of space too. 

Also, to be on the safe side, unmount any partitions that do not belong to the Ubuntu filesystem. This will help ensure that the files from those partitions will not get added to the ISO. 

Hope this helps.

---

### Post by tsinelas30 on 2010-10-09
Newbie here.

Can you teach me how to do remaster?

I need to learn that, it will helps me a lot.

Thanks

---

### Post by ankspo71 on 2010-10-09
Hi,
Here is a tutorial to install and use remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Technical details can be found on this page:
[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html)

Hope this helps.

---

### Post by ankspo71 on 2010-10-09
Well, I tried remastering my Kubuntu Maverick RC installation, but the live cd it created for me crashes with authentication failure. The last time I used remastersys was probably back around Ubuntu Jaunty, and it worked well for me back then.

Anyways, I'll post additional links for anyone who still needs to remaster their Ubuntu.

Reconstructor: 
[https://reconstructor.apphosted.com/](https://reconstructor.apphosted.com/)
[https://projects.lumentica.com/projects/reconstructor/wiki/](https://projects.lumentica.com/projects/reconstructor/wiki/)
[http://www.makeuseof.com/tag/create-custom-ubuntu-cds-easily-reconstructor-linux/](http://www.makeuseof.com/tag/create-custom-ubuntu-cds-easily-reconstructor-linux/)
[http://lifehacker.com/5588211/how-to-create-your-own-customized-ubuntu-live-cd](http://lifehacker.com/5588211/how-to-create-your-own-customized-ubuntu-live-cd)

UCK - Ubuntu Customization Kit:
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[https://launchpad.net/~uck-team/+archive/uck-stable](https://launchpad.net/~uck-team/+archive/uck-stable)
[http://sproutinggeek.blogspot.com/2010/07/tutorial-for-creating-customized.html](http://sproutinggeek.blogspot.com/2010/07/tutorial-for-creating-customized.html)

Novo Builder:
[http://maketecheasier.com/build-your-own-ubuntu-based-distro-with-novo-builder/2010/07/02](http://maketecheasier.com/build-your-own-ubuntu-based-distro-with-novo-builder/2010/07/02)
[http://www.omgubuntu.co.uk/2010/06/make-your-own-custom-livecddistro-easily-using-novo-builder/](http://www.omgubuntu.co.uk/2010/06/make-your-own-custom-livecddistro-easily-using-novo-builder/)

Ubuntu "remastering" documentation:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Other:
[http://en.wikipedia.org/wiki/List_of_remastering_software](http://en.wikipedia.org/wiki/List_of_remastering_software)

---

### Post by MattBD on 2010-10-09
I've used the Live CD Customization guide at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) before to make my own Ubuntu respins and it's always worked well for me. It's not all that hard and it's a great learning experience.

---

### Post by tsinelas30 on 2010-10-10
> **ankspo71 said:**
> Hi,
Here is a tutorial to install and use remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Technical details can be found on this page:
[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html)

Hope this helps.


thanks a lot sir.. will try to read this later.

---

### Post by tsinelas30 on 2010-10-10
Guys need your help.

Im trying to follow this [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) on how to remaster.

Im almost done.

but when im on this part i dont see any .iso file on my remastersys folder.


[IMG]http://www.psychocats.net/ubuntu/images/originalremastersysthumb31.png[/IMG]
[SIZE=4] [/SIZE]

---

### Post by tsinelas30 on 2010-10-11
Got it.

But when i tried to install the iso file

there is an error:

could not find ramdisk image: /casper/initrd/gz



please help.

---

### Post by gpwil1 on 2010-11-17
Hi all,

my recommendation is to use Novo - Uck failed on me a few times, remastersys etc didn't work on multiboot iso, but Novo did the trick.

I'm in the process now of trying it out on a 10.10 distro, but theoretically shouldn't be an issue.

my 2c.

edit - forget my last post - just discovered UCK now supports 10.10, so I am using it again (v2.4), since I tried uding novo for 10.10 and it didnt like it.

---

### Post by naidra on 2010-12-08
I use the reconstructor, when they want to activate the visual effects, then look for a suitable driver ...... but appears notification error ..... anyone can help?

---

### Post by amjjawad on 2011-01-10
Remastersys failed in my first try to create my own iso. Didn't go go deeper in details to find out what's really wrong.
I tried that with Ubuntu 10.04. The size of my iso was 960MB or so.

I might do that later because I'm totally exhausted now or perhaps it's better to try the other tools mentioned here.

SliTaz has a built-in tool to create your own iso. It's great indeed except the lack of packages, etc. My ISO was less than 110MB.

---

