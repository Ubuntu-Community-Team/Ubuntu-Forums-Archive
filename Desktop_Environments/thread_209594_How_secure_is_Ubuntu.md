---
title: "How secure is Ubuntu?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-05
Hello!

Since I am not familiar with how to use Clamav and other types of antivirus and spyware applications for linux, Just how secure is ubuntu by itself?

  Is there an antivirus and spyware gui interface that can be used on ubuntu? Something fairly easy for a newb to use?

Thanks!

---

### Post by adwait on 2006-07-05
You don't really need an antivirus or anti spyware for linux because there are no viruses for linux!

---

### Post by givré on 2006-07-05
I think you don't really need one, spyware and virus for linux are not really common, and anyway, can't cause lot's of damage.
I use exclusivly linux since 1 year, and i never had the problems i had with windows (this ******* yahoo bar which appears like a flower in IE is the best exemple)

---

### Post by briguy on 2006-07-05
There are a couple of anti-virus programs such as clamav, but honestly they mostly only search for windows viruses.  Linux viruses do exist, but are generally nonexistant in the "wild".  Not to say that they won't emerge, but for now it's not a big worry.

As far as spyware is concerned, there isn't a lot outside of tracking cookies etc.  Use some common sense and install the basic security plugins for firefox (noscript, stealther, adblock if you want) and you're good to go.  Without an administrator password (the primary user in Ubuntu) nothing dangerous should be able to be installed.

As far as I know there is no good gui-based anti-spyware for Linux, but I could be mistaken.  I use chkrootkit from terminal to ensure that no-one has managed to connect to my computer and get administrator rights.  You can get it by doing:

```
sudo apt-get install chkrootkit
``` 
and run it with 

```
sudo chkrootkit
``` 
and it should tell you if your computer has been compromised by checking log files etc.  Some recommend that you install it to a usb or some other external drive (maybe find a live security cd like phlak which may have it) to ensure that a hacker hasn't installed a rootkit and modified the chkrootkit program, I haven't bothered yet.

---

### Post by Brynster on 2006-07-05
on the whole Linux is very secure.

There are instances of virii for Linux but mostly they exist as proofs of concept and not int he wild. Because of the structure of Linux being as it is ie nithing can make changes to the root directory without knowing the root passwords makes it so, plus also the million and 1 differing ways of setting up linux means that your install of ubuntu would and could be hugely different to mine, this also works in its favour since there is no 100% gauranteed way of projecting a virus into linux. Imagine if you will opening a dodgey attachment to be meat with the message "linuxvirus101.lib depends on radmonfile2.lib, you have randomfile1.lib, linuxvirus101 will not be installed". It would be a very effective virus.

That said windows virii you recieve you can pass on to other windows users whom may not have protection.

Spy/malware

This is a different matter, whilst no (to the best of my knowledge) exists at this time, with the growth in popularity of Linux i have no doubt in the no to distant future some scally wag will figure a way of doing it.

---

### Post by randell6564 on 2006-07-05
Great Answers!   JUST what I wanted to see!

Thank You Very Much Folks!  

I knew that I heard somewhere that there is no viruses that can find thier way into a linux box.

Makes perfect sense!  How could you create a virus that could attack an operating system that is never the same on anyones pc at any one time?

I LOVE It!   Thanks again!

---

### Post by aysiu on 2006-07-05
I think viruses should be your last concern.

If you open up ports on your Ubuntu, then you should be most worried about crackers and people brute-forcing their way into your box. You should also watch out for rootkits.

These are real dangers.

If there were really a virus for Linux, you'd hear about it well before you got infected, and it would be very difficult to spread widely to other users.

---

### Post by randell6564 on 2006-07-05
[QUOTE=aysiu]I think viruses should be your last concern.

If you open up ports on your Ubuntu, then you should be most worried about crackers and people brute-forcing their way into your box. You should also watch out for rootkits.

These are real dangers.

If there were really a virus for Linux, you'd hear about it well before you got infected, and it would be very difficult to spread widely to other users.[/QUOTE]

Hey aysiu!  Hope life is treating you well!  Unless ubuntu comes with a default firewall, then i dont have one except the one that is built into my Router.

I wouldnt know how to open "ports" in linux.  (wouldnt know how to CLOSE them if they were open either! lol!)

I have not messed with any security settings in ubuntu since I do not know how to use them.  So I am just flying blind on linux, hoping that all is well with just installing and useing!

I dont worry too much because I do not store any important information on my box anyway.  (that kind of info is stored on a drive that has no internet connection and cant be accessed)  unless I get hijacked while on the net, I think i'm pretty safe.

---

### Post by aysiu on 2006-07-05
Well, Ubuntu defaults to not listening on any ports, so if you're going with the default, you should be okay.

Sometimes people install Firestarter, which allows you to see what kind of traffic is going on.

---

### Post by randell6564 on 2006-07-05
Yeah, I had firestarter once on another box, but I'm not familiar with all the 'lingo' so I really could not understand what was happening.  (if ya dont know how to use it then it wont do much good)

I ABSOLUTELY HATE Microsoft,  but I can say that the gui interface is nice. And it tells you in laymens terms whats going on.

BTW, If ubuntu default is NOT to listen on any ports then how come I have no problem interacting with gtk-Gnutella? Or FrostWire?

Ya know something...  You just might have given me an idea!  I can download music with no problem useing these applications.  But I never see that anyone is UPLOADING files that I have configured to share!

That must be the "default not listening on ANY ports" that you mention!  

So I can DOWLOAD files, but no one can get into my shared folders to UPLOAD files!  HA!  Thanks Man!  (now i just gotta figure out how to open a port)

---

### Post by tturrisi on 2006-07-05
Unless running a www server there's no real need for security apps like av in Linux, and if have a router w/ nat, there's no need for a firewall either.  They just waste energy.  However, there could be a need to block Web site tracking cookies.  This is a royal pain in the arse to one by one add to Firefox's blocked sites list.

What I did was export my XP Restricted Sites Zone registry key & values and then edited it into the format used by Firefox to block Web sites.  The file Firefox uses to allow or block sites is called hostperm.1 and it's stored in /home/your-user-name/mozilla/firefox/your-profile/.

Here's a copy of it if anyone wants to use it.  Presently it contains 3,659 sites that are know to use tracking cookies, install windows malware or use annoying popup windows w/more ads.  To use it, remove the .TXT extension & place in the appropriate dir: [HOSTPERM.1]("http://members.cox.net/aturrisi/hostperm.1.txt")

---

### Post by randell6564 on 2006-07-06
Thanks tturrisi!

---

