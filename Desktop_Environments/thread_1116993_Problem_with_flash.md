---
title: "Problem with flash"
date: 2009-04-05
forum: Desktop Environments
---

### Post by grimm08 on 2009-04-05
I have not been able to play flash videos since installation.  I get a big Play sign in the space were the video is supposed to play and sometimes the video loads other time not.  Most of the time video make firefox lock up.  I know flash is loaded on my Ubuntu 8.10 system, and I know this is not a problem with hardware or the site because the video loads find in XP on the same computer if anyone has any ideas please let me know because this is driving me nuts, thanks.

---

### Post by taurus on 2009-04-05
Which version of flash plugin did you install?  Heard there are some minor problems with version 9 so you might want to upgrade to version 10.

---

### Post by Moop on 2009-04-05
Make sure that you don't have multiple versions of a flash player installed. You can search Synaptic for flash and see what's installed. 

Are you using 32bit or 64bit Ubuntu?

---

### Post by andrea000 on 2009-04-05
I had the same problem and tackled it for two days then i installed the tar ball and finely fixed it.It was the only way i had found to get it up and running but it still gives me the arrow but i click on it and it plays.Flash was made for windows the autorun and all of that.Linux deals with stuff like it should and not like windows.

---

### Post by grimm08 on 2009-04-06
This is a 32 bit version of Ubuntu, I have heard about the Synaptic manager.  Not sure how to find or use it, also what do you mean by the tar ball (still learning)?  Is that the .tar.gz version?

---

### Post by James Willis on 2009-04-06
If you are running gnome, look under System, Administration to find the Synaptic Package Manager.

---

### Post by grimm08 on 2009-04-06
I'll try that thanks.

---

### Post by andrea000 on 2009-04-06
> **grimm08 said:**
> This is a 32 bit version of Ubuntu, I have heard about the Synaptic manager.  Not sure how to find or use it, also what do you mean by the tar ball (still learning)?  Is that the .tar.gz version?

Yes tarball.gz tarball is just the linux format the .deb 
is Debian installion package ubuntu uses .deb .gz or 
tarballs to install software.

---

### Post by grimm08 on 2009-04-06
The package manager did reveal two different versions of flash after removing and reinstalling flash I am still geting the same problem.  Using htop I found that firefox is maxing out the CPU, only when I play flash media.  Ads load with no problem this is looking more like a plugin problem then an version problem.

---

### Post by grimm08 on 2009-04-06
After some troubleshooting I found the flash plugin in firefox was causing firefox to max out the CPU.  For now I have installed Opera and flash media loads fine

---

