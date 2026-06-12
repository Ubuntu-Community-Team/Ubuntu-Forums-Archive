---
title: "Is the MKDistro Tool available for Ubuntu?"
date: 2006-05-15
forum: Debian
---

### Post by RAV TUX on 2006-05-15
I was just wondering if the MKDistro Tool found on Dreamlinux is availble for Ubuntu?

[[IMG]http://img76.imageshack.us/img76/8396/construa3wj.jpg[/IMG]](http://imageshack.us)

The exclusive MKDistro tool allows you to build your own Distro from the ground up easily, in a completely assited way.

[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

[http://www.dreamlinux.com.br/english/saiba-tutor.html](http://www.dreamlinux.com.br/english/saiba-tutor.html)

[[IMG]http://img76.imageshack.us/img76/1159/cabecalho5ef.jpg[/IMG]](http://imageshack.us)

MKDISTRO:
THE TOOL FOR BUILDING DISTROS
In order to turn the dream into reality, the MkDistro Tool was born. MkDistro has evolved to an excellent tool for building and remastering

modules and whole Distros . It is developed by one of our
co-founders, nelsongs (Nelson Gomes da Silveira), leveraging the Morphix approach of modules and his previous works on developing the HD remastering scripts for the Kurumin, Knoppix, Kanotix and Beatrix Live CD Distros .


MKDISTRO PHILOSOPHY

The philosophy of the Mkdistro process is very simple, logical and practical and, by correctly applying its rules, it achieves, as a final result, a winner process. Its basic idea comprises planning and building pieces of a system that will be, at the end, put together and configured as a whole, resulting in a harmonic set regarding his visual, performance and strength.

[[IMG]http://img76.imageshack.us/img76/3231/componentes8df.jpg[/IMG]](http://imageshack.us)

a) Mkdistro:  it' s the basic tool responsible for launching, through its auto explained menus and dialog boxes, all the processes regarding the build of Distros. It's easy and intuitive to manage. Actually MkDistro so far comprises a set of 04 ( four ) scripts, mkdistro.sh, mkdistro_main.sh, mkdistro_clean.sh and mkcd.sh, with the main one (mkdistro.sh) using the others in some specific phase of the work.

b) Base-Module (BM): it's a slimmed down knoppix-like image comprising a Morphix patched Linux kernel, kernel modules and the whole set of applications and scripts needed to detect, configure and initialize the system hardware found in the computer.

c) Base Main Module (BMM or Working Module): it's a complete debian file system made up via a debootstrap procedure and the addition of very basic and essential applications designed to serve as a baseline for the full development of the Distro's Main Module.

d) Distro Main Module (DMM): it's the final module of the Distro you developed. In other words, it's practically the whole Distro, made up on top of the Basic Main Module chosen . This module will be later combined with the Basic Module in order to become the final iso image of your Distro.

e) Iso Image: it's the resulting image from the union between the Basic Module and the Distro's Main Module . So, this image is your final operating system which, after burned onto a CD, will become your new Live CD Linux Distro, capable of not only be run directly from the CD (provided you have set up your Computer's bios) as well as be installed onto your computer's HD.

[[IMG]http://img76.imageshack.us/img76/821/processo1nq.jpg[/IMG]](http://imageshack.us)

  The Dreamlinux Team plan, build ad make available in the Dreamlinux repository ([www.dreamlinux.com.br/downloads](www.dreamlinux.com.br/downloads)) Base Modules, Basic Main Modules and the MkDistro tool necessary for building up a new Distro.

Using one Base Module image, one Basic Main Module file and the MkDistro script , anyone can build his/her own Distro according to his/her needs and preferences.

The MkDistro process basically flows following these steps:

1) Conect to the Internet.

2) Download the Mkdistro compacted file mkdistro2.0.tgz from our repository([www.dreamlinux.com.br/downloads/mkdistro/mkdistro2.0.tgz](www.dreamlinux.com.br/downloads/mkdistro/mkdistro2.0.tgz)) into a directory of your choice. After you have downloaded it, decompress it using this command: tar -xvzf mkdistro2.0.tgz.

Rmk: you can also download the script via wget (wget [http://www.dreamlinux.com.be/downloads/mkdistro/mkdistro2.0.tgz](http://www.dreamlinux.com.be/downloads/mkdistro/mkdistro2.0.tgz)) directly to the directory you are located in.

3) Open a terminal and go to the directory into which you have decompressed the mkdistro2.0.tar.gz and execute the mkdistro.sh script (./mkdistro.sh or sh mkdistro.sh).

Rmk: Some Distros, like Kanotix, don't allow you to execute an instance of a graphic application inside a terminal unless you have released the terminal for that. The message usually shown is somewhat like:

Xlib: connection to ":0.0" refused by server

Xlib: No protocol specified

Xdialog: Error initializing the GUI...

Do you run under X11 with GTK+ v1.2.0+ installed ?

root@KanotixBox:/media/sda13/mkDistro#

If that's your case, just run, as a regular user, not root, the following command: xhost +

Then, try it again.

4) Once MkDistro is up and running you'll find self-explained dialogs containing menus that will drive you through the several alternatives available, which are summarized below:

[[IMG]http://img76.imageshack.us/img76/8333/mkdistrotela19nv.th.jpg[/IMG]](http://img76.imageshack.us/my.php?image=mkdistrotela19nv.jpg)

A - New Distro:  his menu option will guide you through the whole process of building up a new Distro making use of a Base Module ([www.dreamlinux.com.br/downloads/bases](www.dreamlinux.com.br/downloads/bases)) and one selected Basic Main Modules build up by the Dreamlinux developers and available on our repository at [www.dreamlinux.com.br/downloads/baremain](www.dreamlinux.com.br/downloads/baremain) (old ones, soon to be deprecated) or [www.dreamlinux.com.br/downloads/basicmainmods](www.dreamlinux.com.br/downloads/basicmainmods) (the new and recommended ones).

B - New Distro, Remastering an existing mainmod:
this menu option will guide you to build up a new Distro by means of a remastering process over an existing main module image coming from a Dreamlinux Distro, Morphix Distro, or any other Morphix derivative Distro.

C - Remastering of an existing CD or ISO image Distro: like the previous option but using a Live CD or an ISO image containing a Morphix derivative Distro, like Dreamlinux itself.

D - Remastering your HD installed Distro:
this powerful option guides you through a remastering process over your HD installed Distro. With very few small adjustments (soon to be available on the next MkDistro release) you can even remaster a Knoppix derivative and have the choice to address its final iso image as a Morphix derivative or a Knoppix one.

E -Woks on the Main Module: this menu option offers you some functionalities you use to modify whatever you want on the Main Module of your Distro and regenerate it. With it you can even build up a new Basic Main Module of your own, from the scratch.

F - Works on the Base Module: this option is generally recommend only for the expert users since it make it possible to change the Base Module, the one responsible for the Distro start up.

G - Add Files and /or Directories into your Distro: this option is one of the most expressive functionalities Morphix has introduced and that MkDistro allows you to easily use. Files and Directories can be easily added into your current Distro, resulting in a new generated image including those files and directories. This is a very fast process and a very easy way of remastering.

H - Add scripts to be executed on Booting:
like the previous option, this one allows you to include one or more scripts of your own to be executed when the system boots. Also this is a very fast process and a very easy way of remastering.

I - Add .deb packages to be installed on booting: another exceptional functionality available to the user by MkDistro, thanks to the Morphix Project. Like the two previous options, deb packages can be included into the current Distro, generating a new one that will fetch and install the deb packages you put into the /deb directory. Again this is a very fast process and a very easy way of remastering

J - Add main modules: With this option you can add as many main modules as you want to generate a Distro with two or more main modules. This is a good option if you want to have, at the same image, two or more specialized Distros, provided you have enough space left on your CD or DVD.

K - Add mini modules: This option allow you to add complete applications as mini modules, which will be loaded by the main module and will behave as being part of it. This is an area of research that's being hardly worked by the Dreamlinux developers since there's shortage of information about it on the Morphix site and wiki.

L - Build the final ISO of your new Linux Distro: after have completed all the previous steps regarding the building and customization of your Distro it's time to build the Distro's final ISO image. This option will merge the contents of the different modules (Base, Main and Mini) and the files on the /copy, /deb, and /exec directories into a single ISO file which you can burn to a CD/CDRW using the option n of the main menu or using any other burner you like. Alternatively you can test this ISO image using Qemu through the command: qemu -cdrom <isofilename>.

M - Delete the Distro working infrastructure: MkDistro build the following working infrastructure to work on the Distro you're building, on the directory you chose:

/Backup

/Base

/Iso

/Main

/Mini

/Work

/hdremaster

With this option all of this structure is deleted, if you don't need it anymore.

N - Burning a CD/CDRW:
With this option you have a simple although efficient shell script CD burner to burn your Distro on a CD or CDRW. Support for burning on a DVD media is being added in the next release of MKDistro.

O - Utilities:
This option calls a secondary menu dialog in which you find options to mount/unmount a cloop image file, a squashfs image file, an iso image file, creates any module not related to the project, like generic minimodules, creates any iso images not related to the project you're working on.

X - Exit: Leaves the script.

---

### Post by briancurtin on 2006-05-15
wasnt there a how-to on how to build your own CDs of your current ubuntu install? i think the purpose was so that once you get your system setup as a base that you like, you could make CDs of it so that if you reinstall you have what you want

i know in arch, theres a wiki page on how to make your own arch isos out of your current install as well.

---

### Post by RAV TUX on 2006-05-15
[QUOTE=briancurtin]wasnt there a how-to on how to build your own CDs of your current ubuntu install? i think the purpose was so that once you get your system setup as a base that you like, you could make CDs of it so that if you reinstall you have what you want

i know in arch, theres a wiki page on how to make your own arch isos out of your current install as well.[/QUOTE]

This would be great to have a how-to guide on this for Ubuntu. It seems like with Dreamlinux's MKDistro tool you can use their live CD to utilize this tool to do this; much like I used Debian K11 hurd's partitioning tool to partition my hard drive.

---

### Post by GarethMB on 2006-05-16
[QUOTE=briancurtin]wasnt there a how-to on how to build your own CDs of your current ubuntu install? i think the purpose was so that once you get your system setup as a base that you like, you could make CDs of it so that if you reinstall you have what you want[/QUOTE]Anyone know where i can find how to do this? It would be super helpfull give how often i screw my install up messing around with what i don't understand.

---

### Post by nalmeth on 2006-05-16
I've been thinking about this for a while, without a whole lot of action.
There are other such utilities, such as linux live.

I am willing to do research and contribute to some sort of howto. Any other takers?

---

### Post by blakamin on 2006-05-18
[QUOTE=GarethMB]Anyone know where i can find how to do this? It would be super helpfull give how often i screw my install up messing around with what i don't understand.[/QUOTE]

Me too!!! Kubuntu has been installed 3 times in the last week... now I have it the way I want it, I want to keep it!

---

### Post by 1oki on 2006-08-31
Its ashame that this thread died with no resolution... :( I would like to know how to do this as well...

---

### Post by slimdog360 on 2006-08-31
Yozef can I ask if you are on the development team with dreamlinux (or maybe marketing). Dont get me wrong here Im not having a go at you or anything, I was just curious.
 
Its just in every second post you make you seem to reference dreamlinux; also on the dreamlinux page [here]("http://www.dreamlinux.com.br/english/saiba-quem.html") there is a picture of old einstien (DRJESTEVES) (remembering you had a profile picture of einstien for a while); and in this post you seem to have gone to all the trouble of hosting all those pretty little pictures on imageshack and not to mention the essay that goes with it.

If you are perhaps you should put some sort of disclaimer in your sig or something. Or maybe you have done something like this and I just didnt see it, if so sorry. 
Like I said before, Im not trying to offend you or anything I was just curious. I would never want to intenionally offend anyone, in particular a member of the forum staff.

[http://www.ubuntuforums.org/showthread.php?t=231242]("http://www.ubuntuforums.org/showthread.php?t=231242")
> **yozef said:**
> 
"Dreamlinux XFCE 2.0 WORKS Edition" is the beginning of a dream come true.

I always say "If you want to see the future of Linux try Dreamlinux today"....I would expand this to say "If you want to see the future of Operating Systems try Dreamlinux today".

---

### Post by peabody on 2006-08-31
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

Reconstructor baby!

It's a pygtk script.  It's pretty good.  You need the current iso of the latest Ubuntu live cd for your architecture and about 2-5 free gigs.  What this does is create a folder with the following structure:

initrd
remaster
root

You can try to just use the gui and see if it offers you enough customization.  However, if the gui doesn't suit your fancy, there is an advanced way to go about it:

Basically, once you run the gui, perform the customizations and apply them, you leave the gui running before going to the next step.  You can chroot int the "root" folder, mount proc (to get networking working) and run apt-get stuff and whatever else kind of system administration from the command line.  Some serious command line knowledge will go a long way here.  I successfully made my own Live CD with it.  I uninstalled OpenOffice, and installed flash, java, tor, privoxy and ghex.  Once the "root" folder is looking exactly the way you'd like to have things on the CD, umount /proc, exit the chroot and hit the refresh button in the gui and it'll tell you if what you have is gonna fit within 700 megs.  If it doesn't, you can use a DVD or chroot back in and keep tweakin'.  I forgot to delete the examples folder, which has like a video and a few other things which could have saved more space.  All in all, it can be very, very hard to fit everything you'd like within the 700 megs.

If all you want is a backup of the packages you have installed, if you've never done an apt-get clean, /var/cache/apt/archives/ should have all the deb files you ever installed on your system.  Just back that folder up to something.  Then those packages can be reinstalled from the backup media if you need to reinstall.

If you really, REALLY want your system exactly the way it was, use tar to backup absolutely everything, and then those tar archives can be restored from the command line from the live cd.

---

### Post by Holzster on 2006-09-26
Peabody

THANKS!!!

Holzster

---

### Post by Holzster on 2006-09-26
Peabody (or anyone)

I got it thanks - but one questions

Is it possible to save a file on the desktop so when the live cd is started it is on the desktop?

thanks

Holzster

---

### Post by peabody on 2006-09-26
> **Holzster said:**
> Peabody (or anyone)

I got it thanks - but one questions

Is it possible to save a file on the desktop so when the live cd is started it is on the desktop?

thanks

Holzster

Good question, I believe so, but I'm not sure if its under the $HOME/Desktop folder of the LiveCD user, or if that user is created during boot time and you instead need to put whatever you want under the /etc/skel directory.  I'll have to get back to you on that one.

---

### Post by RAV TUX on 2006-11-17
*moving to other os>debian forum*

---

