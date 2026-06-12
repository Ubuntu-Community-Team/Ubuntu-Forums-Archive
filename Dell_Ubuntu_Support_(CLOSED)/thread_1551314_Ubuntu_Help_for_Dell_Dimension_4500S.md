---
title: "Ubuntu Help for Dell Dimension 4500S"
date: 2010-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by retrovirus-007@juno.com on 2010-08-12
Hello Everybody,

I have this Dell Dimension 4500S computer machine with just 125 RAM (default). What Ubuntu version should I stick with for old machines like these? 

If anyone is willing to help with finding the most latest stable release for my machine (under the constraints of 125 RAM), I have the link to the releases and will display the PC specifications upon request. 

Old releases (4 - 6):
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

New releases (6 - 10):
[http://releases.ubuntu.com/releases/]("http://releases.ubuntu.com/releases/")

I read that the Dell company had some conflicts with the Linux distributions and trying to replace the Windows OS with Ubuntu may not be successful. I still try though because this machine hasn't given up its lifetime yet so I do not think that I should waste its uses. Anyways, I'll wait for some response (I hope there is a solution) :popcorn: .

---

### Post by mörgæs on 2010-08-12
Old releases are unsupported and thus a security threat. The new ones are to heavy.

A minimal Ubuntu is the way to go, if you want the Ubuntu family: 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
The tutorial is long, but it is not complicated.


If you want to try another Linux, Puppy or Slitaz are good options.

---

### Post by mörgæs on 2010-08-12
By the way, I guess that Dell is quite a bit better than for example Toshiba. Don't give up the faith :-)

---

### Post by retrovirus-007@juno.com on 2010-08-12
mörgæs, thank you for your help. Now with the 125 RAM problem out of the way, I do have one question (probably asked before). This question serves as an retrospect for my Ubuntu experience.

Question:
What is the most stable (minimal/normal) Ubuntu release? I read in the forums that 8.04 is quite stable (if not the most stable).

Sources/Citation:
[Ubuntu Disappoints, again - Suggestion too]("http://ubuntuforums.org/showthread.php?t=1502389&highlight=most+stable+release")

[Grrr Ubuntu 10.04 - What a shocker]("http://ubuntuforums.org/showthread.php?t=1496732&highlight=most+stable+release")

---

### Post by mörgæs on 2010-08-12
These reviews are very negative. There are always some problems with a new release, and 10.04 was no exception, but it is four months old now and getting stable. I would go for this one - in fact I am experimenting with a minimal 10.04 tonight.

---

### Post by mörgæs on 2010-08-12
It worked fine. After installation from the CD I followed more or less the instructions here:
[http://ubuntuforums.org/showpost.php?p=9287016&postcount=223](http://ubuntuforums.org/showpost.php?p=9287016&postcount=223)

After this is done, all the other installations can be done through the menus. 

With 128 MB memory the installation itself will take quite some time, but the final system will work all right.

---

### Post by retrovirus-007@juno.com on 2010-08-15
mörgæs, that is good news to hear. 
It seems as if the recent releases are becoming more adept in adapting to (older) system hardware specifications. I would just wait out for a bit for more stable releases.

Question:
Can anybody confirm if the full 10.04 can take on 125 RAM? If not, then I know that the minimal 10.04 would be the product for a PC of 125 RAM. Also, does the minimal CD dual-boot installs on OS? Do the instructions at [http://ubuntuforums.org/showpost.php?p=9287016&postcount=223]("http://ubuntuforums.org/showpost.php?p=9287016&postcount=223") really serve to get the Ubuntu essentials/minimal? It sounds like installation of some components.

At this time, I am experimenting a (non-minimal) dual-boot Ubuntu 8.04.1 OS configuration on my cousin's (Compaq w/ AMD Sempron CPU/processor) PC desktop (something's got to be done when Windows don't let you use computer applications. It took quite a while (nearly half a day since yeserday) to get the system software to PC functionality, but it worked. I even wrote down the methods to install this Ubuntu release (I forgotten the RAM size of this PC).

I will get back to the Dell of 125 RAM problem (with later [minimal] Ubuntu releases) after experimenting with the Ubuntu and WineHQ. In a further scope, I will address Ubuntu installation on laptops/netbooks. 

Question:
Speaking of laptops/netbooks, does anyone knows the difference between the two PC model design other than the size? Laptops and netbooks are basically the same, right?

---

### Post by russnae on 2010-08-15
I used wubi to use ubuntu 10.4 in xp on a dell 6000 inspiron with 256 ram and it works perfectly with no problems. read the wubi instructs carefully. it insalls ubuntu like it was a program for windows.

---

### Post by mörgæs on 2010-08-16
> **retrovirus-007@juno.com said:**
> 
Can anybody confirm if the full 10.04 can take on 125 RAM? 


No, on the contrary I can confirm that a full 10.04 does not run here. You can take a look at 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> **retrovirus-007@juno.com said:**
> 
Do the instructions at [http://ubuntuforums.org/showpost.php?p=9287016&postcount=223](http://ubuntuforums.org/showpost.php?p=9287016&postcount=223) really serve to get the Ubuntu essentials/minimal? It sounds like installation of some components.


Ubuntu _is_ a collection of components (packages). It is just a matter of selecting the right ones. Another script, which might be helpful, is [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689) . I have not tried myself, though.


The minimal Ubuntus have been around for a long time. They are well-tested, and in my opinion there is no need for waiting for more stable releases.

---

### Post by snowpine on 2010-08-16
Hi Retrovirus, a quick Google search suggests your computer can hold up to 1gb of RAM. A RAM upgrade is an inexpensive way to ensure you can run the full version of Ubuntu no problem. 

According to the [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"), 128mb is the bare minimum for a text-only server install (no GUI). 1gb "should allow even an inexperienced user to easily install a usable system with enough room to be comfortable."

---

### Post by mörgæs on 2010-08-16
I know that we are close to the absolute minimum, but on many of my installations I have seen that **free -m** indicates less than 100 MB used for an installation with GUI during normal light use. Heavy multitasking would of course draw much more memory.

Well, let's see what original poster experiences. Would be interesting with a report, whatever the result.

---

### Post by retrovirus-007@juno.com on 2010-08-17
I have no luck with the minimal CDs yet. Are these CDs the alternate version of Ubuntu? 

I was able to get a working installer for my 125/128 RAM Dell PC.
After fiddling around the search engine, I found a link to the wubi installer.
[http://sourceforge.net/projects/wubi/files/]("http://sourceforge.net/projects/wubi/files/")

The installer version was Ubuntu Wubi 7.04.1 or 7.04.4
This installer requires some internet access or Ubuntu (alternate) CD to work. The really big problem for me is that the base system installation had stop loading at 75% or more. It appears that I would have to wait for a while before anything really works (blast my inpatience).

This morning, I had finally got the Ubuntu installation kicking (CD-boot into recovery mode?) and will have to wait again in hopes for a real working Ubuntu (even if it is alternate) on my 125/128 RAM Dell PC. The "Running local boot scripts (/etc/rc.local" is taking a while for a first-time OS boot.

If anyone wants to give this a try despite the risk of time, you can attempt a alternate Ubuntu installation with the wubi and CD. I think getting more RAM might be a easier option.
Wubi Installer of alternate Ubuntu 7.04 (for 128 RAM):
[http://sourceforge.net/projects/wubi/files/Wubi/Wubi-7.04.04/Wubi-7.04.04.exe/download]("http://sourceforge.net/projects/wubi/files/Wubi/Wubi-7.04.04/Wubi-7.04.04.exe/download")

CD iso of alternate Ubuntu 7.04 (for 128 RAM):
[http://old-releases.ubuntu.com/releases/7.04/ubuntu-7.04-alternate-i386.iso]("http://old-releases.ubuntu.com/releases/7.04/ubuntu-7.04-alternate-i386.iso")

---

### Post by snowpine on 2010-08-17
> **retrovirus-007@juno.com said:**
> I think getting more RAM might be a easier option.

I agree. :) Older Ubuntu releases (8.10 and anything before 8.04) have reached their "end of life" and are completely unsupported.

---

### Post by retrovirus-007@juno.com on 2010-08-17
I am going to try out the "minimal" Ubuntu 9.04 installation with the wubi 9.04 installer. I wonder if the wubi accepts the minimal releases?

I will also retry installing the Ubuntu-Wubi 7.04 before taking a leap onto the RAM shopping cart.

---

### Post by blob dob 11 on 2010-08-17
It doesn't have to be Ubuntu, there are many linux distributions for old computers. Maybe try DamnSmallLinux? [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by snowpine on 2010-08-17
> **blob dob 11 said:**
> It doesn't have to be Ubuntu, there are many linux distributions for old computers. Maybe try DamnSmallLinux? [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

DamnSmall is also end of life and unsupported. :(

Puppy, SliTaz, and TinyCore are the most popular of the currently active projects in this niche.

But I am not sure why anyone would run TinyCore on a computer capable of holding 1gb RAM. ;)

---

### Post by mörgæs on 2010-08-17
The alternate (=text-based) installer is only lighter during the installation. The system being installed is still the full Ubuntu.

A minimal ISO is 10-15 MB of size, and the alternate around 700.

I have never tried Wubi, but I would not expect it to be a good choice for a low-memory system. First Windows takes its share of memory, and then Wubi must live with what's left. 

Besides this: I guess your Windows installation is pretty old. Is it worth keeping, or is it better to wipe the hard disk entirely?

---

### Post by retrovirus-007@juno.com on 2010-08-18
I could not believe that the alternate Ubuntu 7.04.4 actually dual-boots on my Dell PC of 125/128 RAM! It actually works!

The only real complaint is that the CD-boot installation took QUITE a while to finish. Another problem is that the installation took a toll on my Dell's disk space (2 GB free). I think I need a RAM adjustment (I might have over-distribute the space). mörgæs, I know you are right about the dual-boot being a cost to disk space. I have to keep the Windows OS around because I am still getting familiar with Ubuntu.

The good idea about the Ubuntu installation is that I can access the Windows OS partition because I install the two OS into the same C:\ drive.

As for the wubi installer, I consider it as a convenience for more powerful PCs. I believe that the wubi installer was not instrumental in the alternate Ubuntu 7.04 *prepares to dump wubi documentation*

I would like to thank you all beforehand ("mörgæs", "russnae", "snowpine", and "blob dob 11") for your assistance in my Ubuntu installation on a 125/128 RAM Dell PC.

The only thing left is to figure out what number would be a suitable disk space for a (dual-booted and single-booted) PC? Also, if anyone wants to install an alternate Ubuntu with 128 RAM, here is the link to the .iso (CD-boot may take several tries and keyboard inputs): [http://old-releases.ubuntu.com/releases/7.04/ubuntu-7.04-alternate-i386.iso]("http://old-releases.ubuntu.com/releases/7.04/ubuntu-7.04-alternate-i386.iso")

---

### Post by mörgæs on 2010-08-18
Congratulations. Somehow it is more fun to get some old hardware running...

Just be aware that support (that is, bug fixes) for 7.04 ended in 2008. Don't use this machine for your web bank :-)

It is not easy giving advice on hard disk space. You can probably answer the question best: How much space do you need for music and film?

---

### Post by retrovirus-007@juno.com on 2010-08-19
I was thinking was would be the minimum and maximum disk space requirement for Ubuntu (7.04). I want full Ubuntu capabilities, but I also want the least disk space for my future files (music, video, documents, images, applications, updates, and etc).

From my other desktop, I was given the choice to have either 4 gigabytes (minimum) or 8 gigabytes (comfortable). I was thinking to reinstall the Ubuntu on my Dell PC with just 1 gigabyte. I figure that since I am dual-booting, I should go with the smallest possible size. My assumption is that I would be using the WineHQ third-party application for my Windows applications.

edit (08/19/2010, 10:23PM):
I have found this site ("[http://ubuntulinuxhelp.com/how-to-install-the-perfect-ubuntu-based-computer-introduction/]("http://ubuntulinuxhelp.com/how-to-install-the-perfect-ubuntu-based-computer-introduction/")") that quoted:
> For the installation, I will be using the Ubuntu 7.04 (Feisty Fawn), x86 CD. (x86 just means it's for most standard computers like PentiumTM, CeleronTM, AthlonTM, SempronTM.)

The recommended minimum install requirements (for the standard CD) are:
500 MHz x86 processor, 192 MB RAM, At least 8 GB of disk space (for full installation and swap space), VGA graphics card capable of 1024x768 resolution, CDROM drive, Sound Card, Network Card/Connection.

I think would reinstall with 8 GB of disk space for the Ubuntu on my Dell Dimension 4500S. It sounds fair enough.

---

### Post by retrovirus-007@juno.com on 2010-09-06
The thread is basically over, but I came back for some final words... (for the summary, read my last paragraph)

(:|) While I succeeded in making a PC of 128 RAM use an Ubuntu 7.04.#, I also tested the same release on a later PC machine (my cousin's [Compaq w/ AMD Sempron CPU/processor] PC desktop). The Ubuntu 7.04.# installation on the later machine was successful. The operating system's performance turn out very well (especially on its lower RAM requirements), but I found out that the Ubuntu update servers are not supporting this release anymore. Since the support is discontinued, I am not able to retain the Wine application. I reach the conclusion of whether I use a higher RAM-requiring release or refrain from using Wine.

Another story is my installation of an Ubuntu 8.04.1 on my laptop. The installation is a success, but with a flaw. The flaw turns out to be trouble with the wireless network adapter. Maybe I should have used the netbook edition, but I doubt that would make a difference. I am at the same conclusion of not using Wine, but this time, it's an ironic irony to try update the driver of the wireless network adapter in offline mode.

To sum it all up, I think that there are issues with compatibile support for releases and drivers. For these reasons, I am putting off the Ubuntu usage for now. Ubuntu does have its high points in its release archive, where other Linux distributions ignore the diversity of PC specifications. I have run out of comments for this post, so I end this paragraph with thanks to the users in this thread and will look forward to future developments of this operating system software.

---

### Post by nutznboltz on 2010-09-06
I have a feeling that by 10.04.2 a lot of issues will be cleared up.

But for now I succeeded in installing Debian GNU/kFreeBSD on a DELL Dimension 4500s.

After Lucid failed I tried a number of boot options including nopat and iommu=soft and others but nothing worked.

I flipped though some other OS CD installers and they all seemed to point to "we hate your system's IDE".  Some were able to format the disk and then died during installation which is what Lucid was doing.

This is what worked for me to get a working OS:

[http://glibc-bsd.alioth.debian.org/doc/installing.html](http://glibc-bsd.alioth.debian.org/doc/installing.html)

I set the BIOS setup for the IDE to "acoustic mode bypass" and "UDMA on" using BIOS version A03.

---

### Post by nutznboltz on 2010-09-06
I have a feeling that by 10.04.2 a lot of issues will be cleared up.

But for now I succeeded in installing Debian GNU/kFreeBSD on a DELL Dimension 4500s.

After Lucid failed I tried a number of boot options including nopat and iommu=soft and others but nothing worked.

I flipped though some other OS CD installers and they all seemed to point to "we hate your system's IDE".  Some were able to format the disk and then died during installation which is what Lucid was doing.

This is what worked for me to get a working OS:

[http://glibc-bsd.alioth.debian.org/doc/installing.html](http://glibc-bsd.alioth.debian.org/doc/installing.html)

I set the BIOS setup for the IDE to "acoustic mode bypass" and "UDMA on" using BIOS version A03.

I didn't to any of the post-install steps on the next screen.  I just got the networking up via ifconfig and then "apt-get update && apt-get upgrade && reboot" followed by "apt-get install aptitude && aptitude install gnome-desktop-environment"

---

### Post by nutznboltz on 2010-10-11
I just got an unbootable DELL Dimension 4500S to work.

Can you please test and report if this works?

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

Thanks

If you don't know how to set BootOptions read

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also this thread is very important to anyone looking at this bug

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html)

---

### Post by retrovirus-007@juno.com on 2011-04-26
Sorry about the long delay in post nutznboltz, I thought you mentioned the main Linux Debian kernel and I did not know how to respond to such a requirement. Now I know that Debian_GNU/kFreeBSD-i386 is really a root off OS from Debian, GNU, and FreeBSD.

Debian_GNU/kFreeBSD OS might be a more recent development than Ubuntu 7.04.4, but that fact did not excuse the kernel from the chances of system reboots for CD-boot installation. In my second attempt of the CD-boot installation, I tried the expert mode and found out that my Dell Dimension 4500S PC machine (with installed Windows XP OS) went crazy reading on about errors. However, the Dell PC keeps on churning. Eventually I reached to a text interface requiring some elaborate list of Linux/GNU/FreeBSD commands/queries. I am no expert in such a configuration so I decided to try the default mode just to at least get the Debian_GNU/kFreeBSD OS running on the Dell PC machine.

On the default mode of the Debian_GNU/kFreeBSD installation, I read more messages about errors, failures, and funny stuff. I finally see a Windows-like familiarity and went on to the installation. The installation ended in disappointment for me as I perceive a requirement for internet connection (perhaps all the Linux/GNU/FreeBSD kernel need internet connection). I had not been using phone lines as a internet medium for quite a while so I had some trouble with network interface configuration.

After some irc consultation, I found out that I was using a netboot release. I am getting the full Debian_GNU/kFreeBSD at the moment. I will send in the report about the Debian_GNU/kFreeBSD installation for my Dell PC. :-|

---

### Post by retrovirus-007@juno.com on 2011-04-26
The progress with the (validated) Debian_GNU/kFreeBSD CD-boot OS installation sent fewer error messages. However, I ran into a problem with a failed swap space and followed up with a little surface research:
[http://en.wikipedia.org/wiki/Swap_space#Addressing_limits_on_32_bit_hardware](http://en.wikipedia.org/wiki/Swap_space#Addressing_limits_on_32_bit_hardware)

What I did with the x<32-bit==no_swap_space problem is to simply ignore swap space; ignoring the installation of swap space might make the wait time a really long test of patience, but I am not going to grow impatient. I am going to try to make as much use from the PC as possible.

During the software selection section, I was forced to remove the graphical desktop enviroment. The GUI peruses the GNOME design so I expected some heavy CPU computations.
The installation works, but I am left with a text console. I am not tech savvy enough to do console commands; nor are console commands my computing preference.

If anyone wants to try out the Debian_GNU/kFreeBSD for the Dell Dimension 4500S, expect to find a text console as your interface. 
Before you start, I recommend to get the "jigdo - Jigsaw Download" application first because downloading any .iso source from the Debian server might take sixty perent of twenty-four hours compared to the slightly faster download for .jigdo:
[http://atterer.org/jigdo/](http://atterer.org/jigdo/)

Once you have the jigdo application, you can download a .jigdo for the CD (requires multiple copies) or DVD (should be a single copy):
CD-jigdo [http://cdimage.debian.org/debian-cd/6.0.1a/kfreebsd-i386/jigdo-cd/debian-6.0.1a-kfreebsd-i386-CD-1.jigdo](http://cdimage.debian.org/debian-cd/6.0.1a/kfreebsd-i386/jigdo-cd/debian-6.0.1a-kfreebsd-i386-CD-1.jigdo) CD-jigdo
DVD-jigdo [http://cdimage.debian.org/debian-cd/6.0.1a/kfreebsd-i386/jigdo-dvd/debian-6.0.1a-kfreebsd-i386-DVD-1.jigdo](http://cdimage.debian.org/debian-cd/6.0.1a/kfreebsd-i386/jigdo-dvd/debian-6.0.1a-kfreebsd-i386-DVD-1.jigdo) DVD-jigdo

I also found a Wine support patch for the use of Windows applications in Debian_GNU/kFreeBSD:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=591837#15](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=591837#15)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=15;filename=kfreebsd.diff;att=1;bug=591837](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=15;filename=kfreebsd.diff;att=1;bug=591837)

I know that the Windows 2000 works on the Dell Dimension 4500S. With some sprucing, you can see the vacation .jpeg attachment in this post. :cool:

---

