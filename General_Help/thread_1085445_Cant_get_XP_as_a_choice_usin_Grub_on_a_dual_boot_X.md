---
title: "Cant get XP as a choice usin Grub on a dual boot XP/Ubu8.04"
date: 2009-03-03
forum: General Help
---

### Post by mungvvii on 2009-03-03
Hi all

Im a novice ubu head, i addad Lilo boot installer when doing the 8.04 install.

Im on a dual boot XP / Ubu 8.04 PC, and it doesnt give an option to start XP, it just loads Ubuntu.

Can i revert to using Grub or is there an option to allow dual boot choices?

Thanks:guitar:

REMEMBER :- Newby alert!! my first time

---

### Post by azmo35 on 2009-03-03
Hi, i'm not very sure why you choose lilo but maybe this will help [here]("http://www.debianhelp.co.uk/lilo.htm").

---

### Post by mungvvii on 2009-03-03
thanks mate

it wont let me change the kernal-img.conf file, dont have permissions.

how do i get permission?

---

### Post by aquavitae on 2009-03-03
You need to use sudo (or the graphical version, gksu) to get root permissions, e.g. ```
gksu gedit /etc/kernel-img.conf
```
You'll also need root permission for the grub-install command.

---

### Post by mungvvii on 2009-03-03
everytime i try to do any sort of system prefs, it asks for a P/W. I put it in and it says "failed to open, etc" or "you dont have permish, see admin".

I have tried both the 2 P/W's that i set up during install, [1 x root, 1 x user] and niether have any effect. Im working in Ubu desktop, should i be doing this on the startup screen?. im lost with these P/W's and i was extremely careful when entering them [in both the install phase and when required in Ubu desktop. HEEEELLLLLPPP!!!

---

### Post by aquavitae on 2009-03-03
Can you log into a terminal as root: ```
sudo -i
``` or ```
su
```

---

### Post by mungvvii on 2009-03-03
thanks mate, im trying a re-install, i'll try to log as root as soon as i get it back up and working, hopefully nil problems this time. This is the 3rd install, the first 2 did the same with the P/W's on both installs.

its ubuntu studio 8.04 alternate i386 [1.2Gb] I want it for the multimedia aspect [home recording/songwriting, video production] and it seems quite good for that purpose, i just cant get the P/W's figured out!

---

### Post by aquavitae on 2009-03-04
I'm not sure why you're having problems with the passwords, and if its done it twice its probably something you're not doing quite right rather than something wrong with the system.

I don't know ubuntu studio, but in ubuntu the root user is actually disabled and you don't give it a password.  I would assume that this is the case in ubuntu studio?  Then your normal user will use the sudo command (or gksu if you like a gui frontend) to run root-only commands.  In order to do this though, your user needs to be in the wheel group.

---

### Post by mungvvii on 2009-03-04
Thanks A,

I reinstalled and its working OK now, dont know what i did, but it wouldnt take those darn P/Ws. 

The only thing i done different this time, was to not select the ....*wiat for it!! * "Expert User" [Oh Mung, you fool!!] feature [F6 option on the install screen]. Same CD, from the same ISO. 

Anyways, thanks for your help, its appreciated all. Sure i be pestering you'se again with more NewB drivvle!!

---

### Post by aquavitae on 2009-03-05
Hmm, I sometimes think expert mode should be renamed to "psychotically insane settings designed specifically to break your system if you so much as look at them".  Actually that did happen to me once - I clicked on "Expert settings", closed it again, and it messed up my grub install.  Can't remember which distro though.

---

### Post by mungvvii on 2009-03-07
jeez, sound like i was doomed from the outset!!](*,) 

> Hmm, I sometimes think expert mode should be renamed to "psychotically insane settings designed specifically to break your system if you so much as look at them".

i thought that only happened on "Winblows" OS's:D

---

### Post by mungvvii on 2009-03-07
an interesting thing happened on the way to the forum :D

this is just rantings, but once again, im mythed.

I have XP on my HDD, so i used XP dick to partit'n it for Ubu. 1 x 10Gb for UbuStudio8.04, 1 x 10Gb part'n for Ubu8.04 and 2 x 750Mb swap areas. I installed UbuStud from the DVD, sans "expert mode", but Free software only was selected] and it booted fine, login worked and sys changes were cool. I downloaded the sys updates and installed, with nil problemo's.

Then i pushed the envelope and used the Wubi installer for Ubuntu 8.04 from inside XP, no probs, sys boots, logs in and changes settings, BUT #-o:shock:

here are pics of my grup screen now, the maths dont add up and if XP is chosen, it gives another Ubuntu choice, WTF??

Any suggestions whats happened? or is this normal?

---

### Post by aquavitae on 2009-03-09
IIRC, a wubi install uses the windows boot loader.  I normal install will install grub, so what you've got is a grub boot loader in the MBR (i.e. the "main" boot loader).  If you select windows, is goes to the windows boot loader, which normally contains only one entry (windows) and doesn't actually show.  Since you installed via wubi, it now contains an ubuntu entry too.  So if you want to boot up UbuntuStudio, select ubuntu from the grub screen.  If you want to boot Ubuntu, select windows from the grub screen, and then ubuntu from the windows boot screen.  Does that help?

---

