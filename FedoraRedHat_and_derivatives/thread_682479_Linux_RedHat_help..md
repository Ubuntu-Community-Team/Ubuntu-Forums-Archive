---
title: "Linux RedHat help."
date: 2008-01-30
forum: Fedora/RedHat and derivatives
---

### Post by arscaptain45 on 2008-01-30
I need someone to please walk me through this and talk to me like im a 5 year old with this problem. I am the captain of a vol rescue squad and I screwed up our server.  While booting the server I get a Unexpected Inconsistency message.  

I get,
/usr:
duplicate or bad block in use!
/usr: duplicate blocks found... invoking duplicate block passes.
Pass 1B: Rescan for duplicate/bad blocks
/usr: duplicate/bad block(s) in inode 241:/usr:   0124/usr:
/usr: duplicate/bad block(s) in inode 92773:/usr:    9124/usr:
/usr: Pass 1C: Scan directories for Inodes with dup blocks.
/usr: Pass 1D: Reconciling duplicate blocks
/usr: (There are 2 inodes containing duplicate/bad blocks.)

/usr: File /share/doc/openjade-1.3/jadedoc/dsss12.htm (inode #92773, mod time Tue Nov 12 13:56:52 2002)
      has 1 duplicate block(s), shared with 1 file(s):
/usr:        /local  (inode #241, mod time tue nov 12 13:56:52 2002)
/usr:

/usr: UNEXPECTED INCONSISTENCY; Run fsck MANUALLY.
                (i.e., without -a or -p options)
                                                                        [FAILED]

***an error occurred during the file system check.
***Dropping you to a shell; the system will reboot
***when you leave the shell.
Give root password for maintenance
(or control-D for normal startup):

At first I didnt have the password so I used the rescue options and reset the password. I have run Fsck /dev/hda1 and it says 
/: recovering journal
/: clean, 23624/240960 files, 88254/481816 blocks
(Repair filesystem) 2 #
So I typed fsck /dev/hda2
and got back
fsck: fsck.swap: not found
fsck: error 2 while executing fsck.swap for ?dev?hda2

Also after entering root password I get
bash: id: command not found
bash: id: command not found
bash: id: command not found
[: too many arguments
(Repair filesystem) 1 #
Please someone take the time to help me out. Our site have been down for over 6 months now and it is very important that I get it back up and running asap. I am very new to Redhat but I am good with dos if that helps. Thank you for at least reading through my mess.

---

### Post by igknighted on 2008-01-30
looks like a hard drive died to me.  Replace the offending drive and try reinstalling (if it's RHEL, you probably have some service contract with Red Hat, yes?).  Use a raid array in the future so a drive lost like this doesn't bring the whole system down.

---

### Post by arscaptain45 on 2008-01-31
I installed a new copy of redhat on a new hard drive. I then tested the two old drives with a usb extenal hard drive adapter. I was able to veiw both drives without any problems. But I do have a new problem. I was playing with fsck last night and force checked the main drive now I am getting a whole new set of problems. I dont believe its the drives. I feel its a file problem.

Now I get

Warning: unable to open an initial console.
Kernel panic:  No init found.   Try passing init= option to kernel

As I said I am clueless when it comes to linux. Please someone help. And we do not have tech support. Its a free copy one of our past members set up a few years ago. Thanks again

---

### Post by arscaptain45 on 2008-01-31
Ok for now I have the new hard drive in the computer and it up and running. I have used the usb hard drive adapter and copied both of the old drives to folders on the desk top. I labled the hard disk backup 1 and 2.

 I have found our web site files and copied them from old disk 1 VAR/WWW/HTML to the same folder on the new drive. But know I need some help. I cant find any of the IP info for our site. As of now our site has been redirected to some other site. We are ArborRescue.org if anyone want to see what i mean about it being redirected somehow. we didnt do it. maybe because of our down time. I dont know.

Can someone please tell me what files to copy or were to look to find out the old systems ip info. I have no idea what the IP address should be. The past member that took care of all this has since been removed and kept no recordss. 

So at this point if someone can help me getting our site back up and running that would be great.

I also want to try to fix the first set up with the kernel panic problem as a way to learn linux hands on. I learn fast so a little help should go a long way.

---

### Post by lsmobrian on 2008-01-31
no idea if this will help

[http://www.whois.ws/whois-org/ip-address/arborrescue.org/](http://www.whois.ws/whois-org/ip-address/arborrescue.org/)

I havent ever messed with a live site before, but hopefully some of this info will get you on the right track.  If it just involves setting a static IP here is a howto.  You might also try contacting your domain registrar and see if they will help troubleshoot

[http://techteam.wordpress.com/2007/02/08/how-to-set-static-ip-address-on-red-hat/](http://techteam.wordpress.com/2007/02/08/how-to-set-static-ip-address-on-red-hat/)

---

### Post by Zack McCool on 2008-01-31
The registrant for your domain (arborrescue.org) and the redirected one (novass.net) is the same.  Do you know Erik McDonald?  If so, you may need to contact him.

Also, the domain is registered by [http://www.mydomain.com/](http://www.mydomain.com/) .  If you have the account information, you should be able to call them and have the site redirected to your proper IP address.

As to what that is, you'll have to know it.  Likely, you have an IP assigned by your ISP.  Probably a static address.  The addresses listed for the 2 web sites are the same, meaning that someone (likely Erik) has changed the information with the registrar.  Without the proper IP address of your server, you'll not be able to get it back.

---

### Post by arscaptain45 on 2008-02-01
Ok thank you. Eric set the site up way back when. He moved out of state years ago. I have been looking for a way to contact him for a few months for other reasons but have had no luck. As you can see I am much better at ems than web hosting or linux. 

Still playing with the old drives with no luck.

---

