---
title: "Runescape with 10.04 live cd no longer works :("
date: 2010-05-03
forum: Gaming &amp; Leisure
---

### Post by AdiG2 on 2010-05-03
Runescape no longer works with the new Ubuntu 10.04 live cd (desktop i386)
 ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

seems that java has been dumped completely from this one and openjdk doesn't work either. I tried installing openjdk from the package manager, install works ok but the JRE is useless.
I even tried the partners apt repository for the sun java debs, but that is not working either. Firefox keeps saying there's no usable java runtime available.


Any idea what to do to have a bootable live cd with a useable java runtime? 

It worked great in 9.04 and i think i'm stuck using that until i find a solution for this problem.



edit: oh, i see there's another thread for this: [http://ubuntuforums.org/showthread.php?t=1456650](http://ubuntuforums.org/showthread.php?t=1456650)

edit2: but that thread covers hdd-based installs... i need a list of short instructions of what to do for a **[COLOR=Red]LIVE CD EACH TIME it's booted.[/COLOR]** I must not touch the hdd on the system i'm running it and sometimes i'm even using systems without a hdd.

---

### Post by ELD on 2010-05-03
The only way you can do this is to use a live-usb where you can actually save the changes. A big advantage to it is that you could use it anywhere with any changes you make.

A live cd is exactly that a cd you cannot keep any changes made as nothing is written.

---

### Post by D3mon_Spawn on 2010-05-03
why would you want to play runescape through a live cd?

---

### Post by AdiG2 on 2010-05-03
> **D3mon_Spawn said:**
> why would you want to play runescape through a live cd?

sometimes i use it on a system without any hdd installed or when i visit someone and i use their pc i prefer to boot into an operating system i can trust and not worry about what trojans & other malware they have on their pc. In this case i usually leave them the cd, maybe they switch to linux after they see it in action :D


Also, usb flash is not an easy option for me... if i were to give away usb  sticks the way i sometimes give ubuntu CDs, my wallet would be thinner  than a dry onion peel. 

What I need are some simple instructions that can be printed on the cd  cover.
A good scenario would be to create a shell script hosted somewhere and  create an easy to remember tinyurl to it and just print some  instructions on the cd cover ...

1. start a terminal

2. wget tinyurl_link_to_the_java_patch_script
3. sudo ./java_patch_script

4. close terminal
5. start firefox

the best case scenario would be a functional re-spin of the ubuntu iso  like 10.05 or 10.04.1 so that there's no need for a hosted script.


Anyway, Fedora 13 is scheduled to be released on May 18th, it's  currently in the final freeze state. Let's hope their openjdk can be  used for runescape.

---

### Post by Rokyking on 2010-05-03
You could download Live Magic for a Debian distribution and make your own live CD with defaults pre-installed. Then adding your own packages to the Live CD.

Ubuntu has a variant of this as well. I forget what it is called at the current moment in time. 
i'll check back when I get home.

---

### Post by ELD on 2010-05-03
As others have pointed out you can always do a re-spin.

Problem with cds is that if anything changes in the runescape world where you have to download patches you are back to the same problem, you will have to do that again on every reboot everytime it happens.

Get a cheap USB stick and slap it on there, problem solved.

"Let's hope their openjdk can be  used for runescape."

As for that, unless it's a MASSIVELY different version of openjdk, then you will have the same issues. And since 13 uses close to the same versions of everything as 10.04 Ubuntu common sense dictates that you will have the same issues.

So i shall say it one last time, slap it on a USB stick.

---

