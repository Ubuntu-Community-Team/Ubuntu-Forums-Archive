---
title: "Removing GRUB"
date: 2009-05-13
forum: General Help
---

### Post by hvacmoose on 2009-05-13
I was trying to add ubuntu to a usb external drive using my work computer. somewhere along the way i screwed up and my work pc keeps trying to start up by loading grub.  I put in an iso disk and ran a live session. through this i discovered that all of my windows vista stuff is still there. cannot boot windows though. I prefer to not use vista, but i think my boss might be a little tiffed when he finds out that the software he bought and installed on my pc is not usable any more.

basically I have to remove GRUB and get this system fixed asap or i might get fired...

any advise welcome

---

### Post by namd3r on 2009-05-13
When I got rid of GRUB once to go back to using just Windows XP, I think there was a way to re-install the Windows boot loader with a recovery cd.

---

### Post by 123456789123456789123456 on 2009-05-13
Easy simple fix, start using the Vista DVD, go to repair Vista installation, it will find a problem with the MBR, inform Vista to repair MBR

this will reinstall Vista boot loader to the MBR, and remove GRUB.

The trick, is when installing Ubuntu anywhere, is to tell the installer, at the summery screen, go to the advanced options, and tell the installer to place GRUB to the disk where the main UBUNTU is being installed, and not to install in the MBR.

---

### Post by hvacmoose on 2009-05-13
Thanks for the advise...
But.. 
If you guys have bought a pc with wit vista on it recently you would discover that they don't come with a recovery cd
Just a recovery partition on the hard drive. not a big deal if you are smart enough to burn recovery cd when you get the system all set up the way you want it...
Unfortunately I am not smart enough to plan ahead...or not mess with the company pc

---

### Post by medicalystoned on 2009-05-14
> **hvacmoose said:**
> 
 
..
Unfortunately I am not smart enough to plan ahead...or not mess with the company pc

now that isn't true little brother, I know you will figure it out.

Come on everyone, help the dude out!!!!!

-----------------PEACE----------------

---

### Post by louieb on 2009-05-14
Lots of ways described here. Just need to replace the GRUB IPL code in the MBR.
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by hvacmoose on 2009-05-14
louieb:

Thanks...
I will use that first thing in the morning before anyone else makes it into the office.  You are a life saver.



"Use your Brain. Use Your resources. Let the idiots use their muscles."   Stevan Mussatti 2006

---

### Post by lindsay7 on 2009-05-14
Download this iso image and burn to a cd

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Put in you cd drive and it will boot up

Type "bootrec.exe and it will give you the command to run. I am going by memory but I think it would be 

bootrec.exe /fixboot at any rate it will give the options.

---

### Post by hvacmoose on 2009-05-14
**Re: Removing GRUB** 			
 			 			 		   		 		 		Lots of ways described here. Just need to replace the GRUB IPL code in the MBR.
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

This was the best answer i could have gotten.  using ms-sys to revome grub was eassier than ever.  I had my pc fixed about five minutes after my boss walked in.  thanx to all who replied you guys Rock.):P

now im gonna just go ahead and dual boot my office computer... I guess i will never learn my lesson.. :)

---

### Post by muteXe on 2009-05-14
google "super grub disk". I think you can fix it with this (i think)

---

