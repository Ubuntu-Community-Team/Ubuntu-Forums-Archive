---
title: "difference in useage of 32bit and 64 bit"
date: 2011-02-18
forum: Desktop Environments
---

### Post by electroken on 2011-02-18
I have been told and have observed that my 32bit installation of Ubuntu will use all my installed ram in both sections of my slots and that both of the cores of the cpu will be used in running programs. I can see that it is true by using the system monitor on my desktop. It shows that both my cpu's of the dual core are being used by the system and it sees all my ram whereas in windows it would see only 1/2 my ram and only use one of the cpu's. So what exactly do I gain by installing the 64bit system files? I would not be able to use Adobe reader in the 64bit install of firefox etc I am told. So what advantage is there?

---

### Post by CJ_Hudson on 2011-02-18
I am not expert, but I think it is down to the speed the computer carries out processes.
With 64 bit it works faster and there are less delays when performing actions.
There are supposed to be 2 paradigms in the computing world, parallel processing and muti-core processing. It is because 64 bit takes a bigger "bite" at the data (i.e. in sections of 64 bits rather than 32 bits) that it is supposed to improve efficiency. When you think computers used to be only 8 bit, (and I don't know if you remember how slow they were in the old days,) this is progress and an improvement.
It is a new development for me to hear, as I did quite recently, that 64 bit can be installed on multi-core processer machines. I had always imagined it required a special design of specifically 64 processor, and thought previously the two paradigms of computing were separate and divergent.:popcorn:

---

### Post by mcduck on 2011-02-18
64-bit computing gives ability to handle larger numbers, or higher precision, which gives performance benefits on some specific tasks. For any normal home user, it really doesn't make much of a difference, as none of the normal desktop tasks like text processing, web browsing or games use such large numbers or require calculations with hight precision. Most people wouldn't ever see any difference apart from increased performance with some media-related tasks like audio & video encoding and processing (and even then only if the applications used for the task are coded in a way that allows them to benefit from the 64-bit computing capabilities).

Another, better known, benefit would be the ability to address larger amounts of RAM. Of course that brings up a question oh how much RAM you actually need to do whatever you sue your computer for.

On the other hand you really aren't loosing anything if you go for 63-bit version of Ubuntu, and most of the modern processors are 64-bit capable, so there's really not much reason to not use it. Perhaps you'll see better performance with some task you do, most of the time you wont. Or maybe you want to add more than 4GB of RAM to your computer which alone is good enough reason to use 64-bit OS (although in my opinion most people really don't need that much RAM at the moment).

Or perhaps you are like me, doing lots of multimedia work, editing sound & video, and rendering 3D graphics. In which case you should definitely use 64-bit OS, a CPU with as many cores as possible, and add as much RAM as your motherboard is able to handle. ;)

(edit: unlike what the above post suggests, 64-bit computing and multi-core processing aren't two opposite ways of working, most modern CPUs are 64-bit and multicore. Also, 64-bit computing doesn't calculate two 32-bit values at the same time. 32-bit calculations work just like with a 32-bit CPU, and the full 64 bits are used when doing calculations with 64-bit numbers.)

---

### Post by eentonig on 2011-02-18
32b Operating Systems can only use 3,5G of RAM, whereas the limits of 64b operating systems have yet to be reached by everyday computers. Usually, your HW limits the amount of RAM you can install.

Personally, unless you intend to use lots of memory intensive applications (high quality image processing, running multiple VM's, ...) I see no need to install a 64b OS.

I usually install 4G of RAM and use the 32b ubuntu. Hi never hit the point where my OS starts to use swap. and that's even while running a VM occasionally.

---

### Post by electroken on 2011-02-18
> **eentonig said:**
> 32b Operating Systems can only use 3,5G of RAM, whereas the limits of 64b operating systems have yet to be reached by everyday computers. Usually, your HW limits the amount of RAM you can install.

Personally, unless you intend to use lots of memory intensive applications (high quality image processing, running multiple VM's, ...) I see no need to install a 64b OS.

I usually install 4G of RAM and use the 32b ubuntu. Hi never hit the point where my OS starts to use swap. and that's even while running a VM occasionally.
I see that you are trying to tell me that you install only 4 gb ram in the computer because the system will only use 3.5gb ram if it is 32bit, but it appears to me that my system running 32bit is seeing all 7.9gb I have installed on the motherboard and does not seem limited the way you are saying it is. Perhaps you are correct but it seems that I have my 2 processors using ram to do the operations they are doing and maybe they can see all of it that way. I think that when the os gets to the point where the 64bit system has no issues with using Adobe that will be the time to change over; I cant seem to find a reason to do it so far. Thanks all for the contributions and replies.

---

### Post by Frogs Hair on 2011-02-18
One more bit here , I use 64 bit and 32 bit flash with the wrapper and have no problem with flash at all ; however , this is not the case for all users . I have also never had a program compatibility issue , that may be because I have never needed a program that only comes as 32 bit. .[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by cascade9 on 2011-02-18
@ Frogs Hair- gah, 32bit flash in a wrapper. For myself I found that 32bit flash in a wrapper to be awful. If it works for you, go ahead, but I dont know why you wouldnt use the 64bit native flash. 

> **eentonig said:**
> 32b Operating Systems can only use 3,5G of RAM, whereas the limits of 64b operating systems have yet to be reached by everyday computers. 

Wrong. With PAE you can see more than the 3.something GB RAM limit of 32bit- 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

> **electroken said:**
> I see that you are trying to tell me that you install only 4 gb ram in the computer because the system will only use 3.5gb ram if it is 32bit, but it appears to me that my system running 32bit is seeing all 7.9gb I have installed on the motherboard and does not seem limited the way you are saying it is. Perhaps you are correct but it seems that I have my 2 processors using ram to do the operations they are doing and maybe they can see all of it that way. I think that when the os gets to the point where the 64bit system has no issues with using Adobe that will be the time to change over; I cant seem to find a reason to do it so far. Thanks all for the contributions and replies.

Nice try, but no. 

Because you had 8GB when you installed, ubuntu did what it is meant to and installed the PAE kernel. So you can see all your RAM. 

When you use PAE, you can see all the RAM but every process is limited to 3/4GB max. 

I can see why mcduck says "most people wouldn't ever see any difference" but IMO since 64bit is faster, why not use it? Even if its only a few % faster (audio and video encoding will get much, much more than that). 

You might be able to install adobe reader on 64bit with the 'force architecture' option. I havent checked if there is a 64bit version now, there might be. I dont use adobe reader, I use envice, which has a 64bit native version that runs just fine.

---

### Post by DennyF on 2011-02-18
Now that we have all this settled, my Ubuntu installation was the 32-bit version running on an Intel Core 2 Duo Gateway Laptop w/3 gb. RAM. I couldn't be happier with the system, especially when you consider I've been running Windows since Ver. 1.0 and didn't realize that there was a better, viable alternative when I installed this new Linux system 4 weeks ago. Considering all that, I'm under the impression that my machine will run better/faster under the 64-bit Ubuntu installation.
Can I upgrade to 64-bit without losing my initial software installation? If so, how? What would be the most efficient way to go to 64-bit? I'd be anxious to do that since I run a lot of graphic intensive packages as well as CD/DVD authoring software. Obviously, when I do that, I can install more memory and 64-bit Ubuntu will take full advantage of it.

---

### Post by oldfred on 2011-02-18
You have to do a new install.

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.

When I converted from 32 to 64 a couple of years ago, I created a separate /home so my data would not get overwritten and exported a list of installed apps. I reviewed what systems wide changes I manually did in /etc and backed those up also. If not sure you can backup all of /etc, but do not just copy back as setting may be different.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

If you have separate /home or /data, then you only need 10 to 20GB for a system partition. You then can create a new partition if you have room and install and test separately. I have all my data in /data, keep /home with only hidden user settings and each new version of Ubuntu goes into a new system partition. I rotate old, current & beta around 3 partitions.

---

### Post by oldos2er on 2011-02-18
> **electroken said:**
>  I think that when the os gets to the point where the 64bit system has no issues with using Adobe that will be the time to change over; 

I haven't had a problem using Adobe Reader; although there isn't a 64-bit version yet (that I know of), acroread + nspluginwrapper works well enough.

---

### Post by electroken on 2011-02-18
> **cascade9 said:**
> @ Frogs Hair- gah, 32bit flash in a wrapper. For myself I found that 32bit flash in a wrapper to be awful. If it works for you, go ahead, but I dont know why you wouldnt use the 64bit native flash. 



Wrong. With PAE you can see more than the 3.something GB RAM limit of 32bit- 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)



Nice try, but no. 

Because you had 8GB when you installed, ubuntu did what it is meant to and installed the PAE kernel. So you can see all your RAM. 

When you use PAE, you can see all the RAM but every process is limited to 3/4GB max. 

I can see why mcduck says "most people wouldn't ever see any difference" but IMO since 64bit is faster, why not use it? Even if its only a few % faster (audio and video encoding will get much, much more than that). 

You might be able to install adobe reader on 64bit with the 'force architecture' option. I havent checked if there is a 64bit version now, there might be. I dont use adobe reader, I use envice, which has a 64bit native version that runs just fine.
I can understand a lot of what you are saying but I still can observe with my computer (intel dual core pentium 3.4ghz on a Abit IP35  Pro motherboard using 8gb pc6400 ram) that each cpu is running and doing tasks and the system sees the entire 8gb (7.9gb I think) of ram.
What gives with that? Do I have several 8 bit processes going on at the same time or only 2 at a time with the usual smoke and mirrors thing making it look like it is multitasking?
I would follow some of the directions above but I am really afraid I might goof up and not save a lot of my programs or data when trying to do it. I figure I will stay put where I am now and use Ubuntu 64bit on another computer in the future. I might also try Linux Mint but use the 64 bit version of it. 
Thanks for the information.

---

### Post by gordintoronto on 2011-02-18
"PAE" provides access to more than 4 GB of memory, with a 32-bit kernel. However, each program is limited to 2 GB of memory AFAIK.

I have been using 64-bit Ubuntu for almost two years, and have experienced zero issues with it. I use Acroread, the Adobe Reader. I try a lot of software.

---

### Post by Cracklepop on 2011-02-18
> **oldos2er said:**
> I haven't had a problem using Adobe Reader; although there isn't a 64-bit version yet (that I know of), acroread + nspluginwrapper works well enough.

I can't understand why anyone would use Adobe Reader in the first place! ;)  It really is a gigantic piece of bloatware, and there are so many alternatives available... 

> **electroken said:**
> I can understand a lot of what you are saying but I still can observe with my computer (intel dual core pentium 3.4ghz on a Abit IP35  Pro motherboard using 8gb pc6400 ram) that each cpu is running and doing tasks and the system sees the entire 8gb (7.9gb I think) of ram.
What gives with that? Do I have several 8 bit processes going on at the same time or only 2 at a time with the usual smoke and mirrors thing making it look like it is multitasking?
I would follow some of the directions above but I am really afraid I might goof up and not save a lot of my programs or data when trying to do it. I figure I will stay put where I am now and use Ubuntu 64bit on another computer in the future. I might also try Linux Mint but use the 64 bit version of it. 
Thanks for the information.

Your 32 bit OS is using more that 3.5GB thanks to the PAE extension.  PAE works, but it means an extra layer of lookups to access memory, so performance-wise 64 bit is a much better option.  Besides more RAM the longer and greater number of registers in 64 bit hardware that also contribute to the performance increase you will see in games, encryption, video transcoding etc, are only usable if you've got a 64 bit OS.

---

### Post by electroken on 2011-02-18
Hey Cracklepop
I see now what you are saying to me. My 32 bit OS is using both cores of the processor and the system sees all 8gb of ram but it is doing it in a fairly crippled way where it would be much faster if I were to use a 64bit OS. So it does work the way I thought it did but at a much slower pace to run the programs I am using. This makes sense to me and is the best description of what is going on in my opinion. Thanks for the explanation. When I get more familiar with this OS I will probably reinstall it using the 64bit version and at this point once I do all the updates for the Ubuntu 10.04 I will have the equal of what I would get if I went to the 10.10 or 11.04 versions of the 64 bit OS as I understand things. I want to have it all correct in my head as to how I make the change and keep all my data and programs. I will see if I can understand what Oldfred said to do to make it happen. Thanks to all of you for the help.

---

### Post by Cracklepop on 2011-02-19
> **electroken said:**
> Hey Cracklepop
I see now what you are saying to me. My 32 bit OS is using both cores of the processor and the system sees all 8gb of ram but it is doing it in a fairly crippled way where it would be much faster if I were to use a 64bit OS. So it does work the way I thought it did but at a much slower pace to run the programs I am using. This makes sense to me and is the best description of what is going on in my opinion. Thanks for the explanation. ... Erm, no, that's not it.
It's nothing to do with how many cores you have. 1, 2, 12 cores - it makes no difference, completely unrelated.
The OS is seeing your RAM, and because your OS is using PAE, it isn't ignoring everything above 3.5GB.

---

### Post by wizard10000 on 2011-02-19
> **gordintoronto said:**
> "PAE" provides access to more than 4 GB of memory, with a 32-bit kernel. However, each program is limited to 2 GB of memory AFAIK.

Close.  3GB user space and 1GB kernel space.  

8)

---

### Post by wizard10000 on 2011-02-19
> **Cracklepop said:**
> I can't understand why anyone would use Adobe Reader in the first place! ;)  It really is a gigantic piece of bloatware, and there are so many alternatives available...

I use it because I haven't seen an alternative that works as well for me.  It is bloatware but for my needs it's still the best game in town.

---

