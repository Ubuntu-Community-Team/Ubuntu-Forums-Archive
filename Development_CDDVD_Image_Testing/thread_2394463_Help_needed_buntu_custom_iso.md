---
title: "Help needed *buntu custom iso"
date: 2018-06-16
forum: Development CD/DVD Image Testing
---

### Post by rhss6-20112 on 2018-06-16
_***PLEASE READ THE ENTIRE POST - I WILL IGNORE "STUPID" AND CONDESCENDING ANSWERS***_

Hello and good morning/afternoon/evening to whomever is reading this:

Little bit of background first, I am currently running Kali Linux ONLY on my laptop which is an Asus X335MA. I used to dabble in Shell/Bash scripting, and also started using zenity among many other projects. In other words, I'd appreciate it if I'm not treated as an utter NOOB, while at the same time realizing that I may/may not be as knowledgeable of Linux as whomever is reading this.
Also, I'M NOT TRYING TO CREATE A BACKUP of my system. I'm also not trying to download an iso image, and manually bit by bit modify it either.
In Kali Linux, there's a way to build a custom iso using a partial program already developed by Offensive Security to help in the process. I can use differend GUIs, and I can modify a config file that is basically read as an package installation list so the program reads said programs (i.e. gparted, synaptic, pluma etc.) which you can add to, and add to the programs on the iso "default programs" as long as you have the required repositories for them, and they'll be included into the iso image.

HOWEVER,** I do not wish to create a custom Kali ISO** - been there, done that. (obviously, this is the wrong Forum for that anyways)

Right now, I have a friend several thousand miles away in another state, who wants to get rid of Windows completely, and install linux. I wanted to make the beginning relatively easy for him, and decided I'd see about installing either LinuxMint, Linux Ubuntu* or perhaps even a customized  version of Linux to help him ease into it using Ubuntu with MATE as it is similar to GDM2 which was a pretty nice look to start off in when I filled installed Karmic Koala.

So, with this said,
I first looked into the Kali program that automates the vast majority of the process to make it easier, to see if I could modify it and use it as is. It's definitely modifiable, but I'm not entirely certain I want to mess with it since it's Kali-specific. I'm not even certain what kind of errors I'll get if I start adding Ubuntu repositories, removing default Kali programs etc. I have a feeling that I'll totally screw up the program designed for that task.

So, here's what I was looking for - after a fresh install of (more than likely) Ubuntu, I intend on attempting to add custom programs, such as qbittorrent, chromw-browser, opera, gparted, teamviewer, gdebi, and a few other knick knacks for my friend to start off on. (Teamviewer for long distance support when he needs help and I have the time to remotely access his computer and help guide him through it)...

**The question is**, ***is there any (kind of) simple way to do this*** - I have actively been trying to get Linux to become more mainstream with every person I meet who uses computers a lot, and I'm sure my friend will eventually want to help as well. I understand that between using chroot (which I'm assuming I'll have to use) and generating the iso image itself etc. it'll take a couple hours.
But if there's a relatively simple way I can create an iso image with custom applications, and possibly inject help files from an already installed system (without using an obsolete remastersys) I'm hoping I can create a shell/bash script, or a simple program similar to what Offensive Security made for other linux distributions such as Ubuntu, Mint, Debian, Fedora, etc.

I already spent a good couple of days in google, and everyone is talking about backing up their system, and files, or just creating a generic iso (why not just download it and modify the existing files after mounting the iso into a mount point) and other things that I'm not really that interested in, unless I really don't have a choice. If there's a simple, straightforward way to do this, without spending half a day on it, and you can point me in the right direction(s) that would be fantastic.

Thank you for your time, and your help,
RHSs6-2011

---

### Post by oldfred on 2018-06-17
I have an install script. Actually now two or more.
One links my /mnt/data partitions and updates some configuration files.
The other installs many applications.

I have multiple apt install lines, but you can just install from one text file. I have used my backup of installed apps from my older install when doing a clean install.

I started creating my newinstall.sh just by copying history lines from an install and editing out the sudo. Avoid using anyone else's install file unless you know exactly what it does.

These are now older, and many changes since, but only for reference anyway.
 Oldfred's install scripts
[https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662](https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662)

---

### Post by rhss6-20112 on 2018-06-17
OMG thank you,
This will seriously help! It's not EXACTLY what I was looking for, but pretty freaking close to it. Obviously the initial step was going to be all manual anyways, but I didn't expect there to be quite that much in it (I read the entire initial post). Regardless, thank you soo much I definitely have a good idea of how to get this done now.

---

