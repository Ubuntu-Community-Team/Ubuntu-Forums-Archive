---
title: "new to kubuntu - Question re deb repositories"
date: 2005-07-10
forum: Desktop Environments
---

### Post by arjay1 on 2005-07-10
Hi - just installed kubuntu and all looks very promising.  The first of 3-4 distros I have tried that actually automatically found, mounted and created a desktop icon for my digi cameras.

Coupla quick questions:

1.  I am using kubuntu because I prefer KDE to Gnome.  Is it true that K is just U with KDE or are there other differences?  Another poster said "Kubuntu is markedly inferior to Ubuntu" (for example Kynaptic v Synaptic).  If there are other marked differences - would I not be better off installing ubuntu and then installing KDE on top (e.g. that way I would get Synaptic as well)?

2.  There are quite a few programs I want that are not in any of the ubuntu repos.  I am used to just hitting deb repos with apt-get and having all my dependencies met - awesome.  However now, for example with digikam, I have found a copy of the software that is in deb format but if I download that and run dpkg -i, I get a load of unmet dependencies.  I have tried finding the required libs etc but they, too, ask for yet more files.  I did try to go to a link for digikam from a post here but it was dead.

What is the best way to get software that is not in the ubuntu repos?  For example, any ideas on a couple of good deb repos I could safely add just to get these sorts of programs?

Cheers

---

### Post by dave9191 on 2005-07-10
Hey, 

Kubuntu is ubuntu with gnome removed and replaced with kde. Ive been runinng kubuntu since it came out, and I find that there are are in places some minor things that havent been sorted out yet. Like in some of the hibernation / suspend scripts issue commands to xscreensaver which has been revmoed in Kubuntu. As for kynaptic, it very simple and lacks features that you find with synaptic. You can just apt-get synaptic or kpackage, both better then kynaptic. 

My personal recommendation is to install ubuntu and then put what you want ontop of that. But thats because I prefer to compile kde / fluxbox myself and sort it out that way. And I am not too keen simplified look of kde thats been refined with the simple ubuntu style. But if you have kubuntu intsalled already, then stick with that. I cant say that there is anything that is seriously bothering me with kubuntu that makes me want to use something else. 

Have you added the extra repositories to the default list that comes with ubuntu. You can find out how to do that at ubuntuguide.com. You can also try debian ones, but i dont know any that i can recommend. And if its just one or two programs you could try to compile them from source. It might be a pain if youve never done that before, but once they are installed, thats that :) 

Dave

---

### Post by arjay1 on 2005-07-10
Thanks for the quick response.  Given your analysis, I think I'll stick with Kubuntu for now - only just got the iso and installed it!

As to the software - the main program I am really missing is digikam.  Very important for my wife who I am trying to shift from Win XP which has excellent photo organising software and Photoshop which is just a better product than the Gimp - though I think it is brilliant for a free program.

I'll look at the issue of compiling.  I have never done it before but will have a go if I can get the right source files.  I seem to remember when I last looked at compliing digikam even linux gurus were shaking their heads at it - it seemed to be a right pig!

I might post a more general question re obtaining and installing digikam.

Thanks again

---

### Post by SGC on 2005-07-10
digiKam is in the universe repository:
```

sudo apt-get install digikam digikamimageplugins digikamplugins

```

---

### Post by arjay1 on 2005-07-10
SGC

Thanks for your prompt and helpful reply.  At the moment I am on another computer on my network running simplymepis (I know - shame on me ;-) ) and can't see what repos I have covered at the moment in sources.list under kubuntu.  However, I did add a couple but even then apt-get reported no such file/s

It would be really helpful if someone like you who clearly knows what they are doing, would post the contents of their sources.list for newbies like me to see.  If not, at least the full link to the universal repo would be helpful.

Cheers

---

### Post by SGC on 2005-07-10
Here is my sources.list:

```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

#### universe
deb http://us.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe 

#### multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse 

#### backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted 

#### kubuntu.org
deb http://kubuntu.org/hoary-kde341/ hoary-updates main 
deb http://kubuntu.org/hoary-koffice14 hoary-updates main 


```

Make sure to do **sudo apt-get update** after modifying sources.list, to include the new packages

---

### Post by dave9191 on 2005-07-10
there you go, problem solved :)

---

### Post by arjay1 on 2005-07-11
Thanks to both of you - great help and quick too - can't ask any more than that.  Hopefully I'll be able to help someonelse one day :smile:

---

