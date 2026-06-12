---
title: "New Install Help, Root Acct, Screen Position, More"
date: 2006-01-03
forum: General Help
---

### Post by twokatmew on 2006-01-03
Hello, I have just installed Ubuntu 5.1.  I have used Unix/Linux here and there over the years, but I am an experienced Windows admin.  I have used CentOS and Fedora Core, but I tried Knoppix and really liked it, so I thought I'd check out Ubuntu.  Anyway, I installed it on my NForce2 system (1GB RAM, Geforce4 MX video, Dell 19" LCD monitor, and 120GB disk space.  I created three partitions on my drive (/, /home, and a tiny swap file).

Anyway, during installation, it said that there were problems installing some of the apps, and if I continued, some might be broken.  I continued, because I knew I had plenty of disk space (confirmed by running System Monitor), and this was a test install.  Anyway, upon first look, everything seems fine.  Ubuntu is on my second drive, and GRUB is on the MBR.  It picked up my Windows installation on drive 0, so I can boot into Windows when necessary.  As this is a second machine, my intent is to ultimately blow away Windows entirely and make this machine Linux only.  Any idea as to why I got the error that some apps might be broken?  I did the text install BTW, as I had trouble with the graphic installs of Fedora Core and CentOS.  (No problems on my other NForce2 box, but that system must remain Windows only for various reasons.)  Ubuntu's install routine said I could go back and select to install fewer packages, but I never got prompted on what type of installation I wanted.  (I used the DVD, which seemed to install everything.  This is fine by me, because my intent is to learn everything I can.)

Anyway ... during install, although I was prompted to create a user account for myself, I never got prompted to create a root password.  Consequently I can't log in as root...  That's problem 1.  Did I miss something, or how can I set a root password?

Next problem.  I was able to configure the proper settings for my monitor (1024x768, 60Hz refresh rate).  However, the screen image is shifted to the right.  Is there any utility I can use to properly center it?  I was hoping to get by without installing NForce2 drivers from NVidia.  But perhaps this is what I need to do?

And finally, I'd like to buy a book to help me with Ubuntu.  I've checked Bookpool and found nothing.  Should I buy a book on Debian?  Or can someone recommend something?  I've got a book on RedHat Linux 9, but I'd rather have something closer to the distro I'm using.  BTW, upon first look, Ubuntu looks like it might be just the distro for me.  My search may be over.  :)

Thanks!

---

### Post by nkoplm on 2006-01-03
i had the same proelms too. i have only been using ubuntu for a day, but i just uninstalled anything that was broken (7 packages), and my machine seems to be running fine so far.

the root password was confusing for me too. it is set to be the same as the first user password that was created durring installation. i think this i really dumb, and you should probably change it right away to something unique and secure.

---

### Post by carlosqueso on 2006-01-03
[QUOTE=twokatmew]
Anyway, during installation, it said that there were problems installing some of the apps, and if I continued, some might be broken.  I continued, because I knew I had plenty of disk space (confirmed by running System Monitor), and this was a test install. [/QUOTE] hmmm...I'd just remove what didn't work and reinstall the packages.  If it's not causing you any probems, don't worry.  There are only two options with Ubuntu, full and server, so I'd just not worry about the ones that don't work. 

[QUOTE=twokatmew]Anyway ... during install, although I was prompted to create a user account for myself, I never got prompted to create a root password.  Consequently I can't log in as root...  That's problem 1.  Did I miss something, or how can I set a root password?[/QUOTE]
This is how it's supposed to be.  In Ubuntu, you preface each command that requires root with "sudo" and you'll be prompted for your user password.  "sudo -i" will give you a root shell if you need it.  For more on this see: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29)

I can't help with the other two problems, as I haven't had trouble with my card.  As for learning, I've learned loads just hanging out on these forums, but I don't think there are any paper books out there.  Welcome to the world of Ubuntu.

---

### Post by twokatmew on 2006-01-03
Well I just tried logging in as root (using the same password as that of my user account), and oddly I get an authentication failure.  I've tried multiple times, so I know I'm not making typos.  Any ideas on this one?  I managed to find the video driver for my card and how to install it using the "sh" command, but I need to log in as root to install it.  But I can't log in......  :-(

Any and all help much appreciated!  :-)

---

### Post by twokatmew on 2006-01-03
OK, sudo -i did it.  Thanks for the pointer to the wiki, Carlosqueso!  :-)  Now I have another problem, however.  Once I had a root console open, I changed into the downloads dir I created in my user account's home directory, which is where I have the NVIDIA video driver stored.  I successfully ran the "sh <filename>" command to install it.  But I get an error that I either need to install "binutils" or make sure "ld" is in my path.  Now I know how to edit the path in DOS and Windows, but I've never edited a path in Linux....  I've already added some apps and used Synaptic to update the apps I do have installed, and I don't recall seeing binutils anywhere.  Help?

Thanks so much for the quick responses!  So far Ubuntu (and its user community) seems really great.  :-)

---

### Post by twokatmew on 2006-01-03
Double post deleted.... Sorry.  :-)

---

