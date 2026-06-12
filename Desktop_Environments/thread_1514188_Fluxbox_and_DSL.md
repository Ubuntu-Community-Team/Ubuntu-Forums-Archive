---
title: "Fluxbox and DSL"
date: 2010-06-20
forum: Desktop Environments
---

### Post by BrownPanda on 2010-06-20
I recently installed DSL on a Pentium II and I was wondering if I could instal fluxbox on it.
If so how do I have to do that, and make it the default environment ?

---

### Post by ronnielsen1 on 2010-06-20
DSL hasn't been maintained for a while. No telling what you'll end up with. You could do it. It might break. I'd go with one setup with the latest repos. AntiX is a good one

[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

> antiX is a fast, lightweight and easy to install linux live CD distribution based on [MEPIS]("http://www.mepis.org/") and [Debian Testing]("http://www.debian.org/devel/testing") for Intel-AMD x86 compatible systems. antiX offers users the "Magic of Mepis" in an environment suitable for old computers. So don't throw away that old computer yet! The goal of antiX is to provide a light, but fully functional and flexible free operating system for both newcomers and experienced users of Linux. It should run on most computers, ranging from 64MB old PII 266 systems with pre-configured 128MB swap to the latest powerful boxes. 128MB RAM is recommended minimum for antiX. The installer needs minimum 1.2GB hard disk size. antiX can also be used as a fast-booting rescue cd. 
At the moment antiX-M8.5 comes as a full distro (c480MB) and as a base distro (c260MB) for 486 and 686 kernels. For those who wish to have control over the install, use antiX-base. 

But if you're wanting to experiment, you could type in sudo apt-get install fluxbox in a terminal and choose fluxbox at the login screen. (Assuming DSL uses sudo - if not su)

---

### Post by BrownPanda on 2010-06-21
Thanks that helped ^^
should i take the 486 or 686 ?
I think its the 486 , since my pentium II is a 586

---

### Post by ronnielsen1 on 2010-06-21
> should i take the 486 or 686 ?

the 686

> [IMG]http://ubuntuforums.org/images/rank_3.png[/IMG]
 			  			  			 				 
				Join Date: Dec 2005
 				Location: Germany
 				 	  					Beans: 179 				
 			       Ubuntu 9.10 Karmic Koala  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Centrino Duo-- 386, 486, 686?** 			
 			 			 		   		 		 		Hi,

Centrino Duo processors are also called "Pentium M" and they are 686 .

486 the old boxes from 10 years ago, which had between 33 and 100 MHz -  good old times. And 386 where the first real 32bit processors by Intel  even more years ago.

Today, all Intel processors of type Pentium 4/III/II + the cheap version  of them are 686. Even the Pentium Pro is 686.

[http://ubuntuforums.org/showthread.php?t=222159](http://ubuntuforums.org/showthread.php?t=222159)

> Very old processors like Pentium I and AMD K5 and K6 are an older  architecture than i686, which was introduced with Pentium Pro. They need  a kernel compatible for them, the 486.  All other CPU's can use the 686.
For  more modern CPUs (AMD x64 and Some Pentium IV and beyond) there's the  amd64 compatible kernel (not in antiX). Any CPU can use a kernel built  for an earlier architecture but not for a newer.
[http://antix.freeforums.org/486-vs-686-t2394.html](http://antix.freeforums.org/486-vs-686-t2394.html)

---

