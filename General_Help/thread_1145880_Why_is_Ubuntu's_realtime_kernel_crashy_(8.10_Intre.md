---
title: "Why is Ubuntu's realtime kernel crashy? (8.10 Intrepid, 9.04 Jaunty)"
date: 2009-05-02
forum: General Help
---

### Post by interim descriptor on 2009-05-02
Hi.

I've tried using Ubuntu's realtime kernel in both Intrepid and Jaunty, but both times, my system became incredibly unstable, crashing usually 20 minutes after I log in.

As such, I've had to resort to compiling my own realtime kernel, which fixed things. This page in particular lead to a stable realtime kernel:

[http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/]("http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/")

My question: **Why is this?** I'm clearly not the only person experiencing this, so what's the issue that's preventing this from being fixed?

I develop music performance software (dj software, in fact), and I'd love to tell my users to just apt-get install linux-rt, so they can enjoy the necessary benefits of realtime priority for the audio output thread. But that's not possible, because the last two releases have unreliable realtime kernels. Ubuntu Studio didn't even ship with a realtime kernel in 8.10... For some reason, they're shipping with a realtime kernel in 9.04, but if it's the same one Ubuntu itself is distributing, then I wouldn't suggest my users install it.

Though some frustration doubtlessly is evident, I don't intend this post to be a flame. I honestly want to understand the problem with as much detail as possible.

My systems that have experienced the crashiness are both Dell XPS laptops. One is an m1710, the other is an m1730.

I've attached my .config file, for the realtime kernel I've compiled myself that doesn't crash.

---

### Post by adverb on 2009-05-07
Thanks for posting this.  I was pulling my hair out trying to figure out why my laptop was crashing.  I had installed 9.04 and did a manual upgrade to the Ubuntu Studio packages (with the linux-rt).  Unfortunately, I had upgraded my nVidia driver at the same time, so I was not sure if the problem was the video driver, or the kernel (or both).  Running the generic kernel, the system is stable indefinitely; the linux-rt kernel when booted, I'm lucky to get ten minutes.

I have the 'noapic' switch in the /boot/grub/menu.lst which I thought had helped, but it didn't.

The crazy part is, I can't even get JACK to run in real-time (even after doing the edits to the /etc/security/limits.conf) when I boot with the real-time kernel.

I'm going to try to use your config to redo the kernel. 

But yes, you were not the only one having this problem.

---

### Post by mrowth on 2009-05-07
Same here, things start crashing left and right after a while. Also, no suspend to RAM. 

I had a very similar problem once before after upgrading to a dual core CPU, but noapic fixed it. Not anymore. 

Strangely enough (? and I'd like some technically better-informed input on this!), I can and always could run Jack in rt mode with the generic kernel. Lower DSP load, lower latency, with fewer xruns... come to think of it, though, that might be why it used to crash on me a lot a while ago. 

This might become my first self-compiled kernel then... edit: ...or maybe not, if I can't even install the nvidia driver for the existing rt kernel. (Works for the generic kernel)

---

### Post by interim descriptor on 2009-05-08
> **adverb said:**
> The crazy part is, I can't even get JACK to run in real-time (even after doing the edits to the /etc/security/limits.conf) when I boot with the real-time kernel.

Oh, do NOT get me started on how broken realtime audio STILL is in Ubuntu.

You're entirely correct. /etc/security/limits.conf is for all purposes broken, if you're trying to do realtime audio.

I have to resort to running JACK as root, in order for realtime priority to kick in.

I'll stop for now, but that is another rant for another day.

---

### Post by interim descriptor on 2009-05-08
> **mrowth said:**
> This might become my first self-compiled kernel then... edit: ...or maybe not, if I can't even install the nvidia driver for the existing rt kernel. (Works for the generic kernel)

For reference, after compiling and booting with my realtime kernel, I installed the nvidia drivers by running the binary downloaded from nvidia's site, NOT by using Ubuntu's package.

Try that.

---

### Post by mrowth on 2009-05-08
I tried just that with the stock rt kernel from the repositories (after purging all nvidia packages), just to see if it'd work. It didn't. I had previously done the same for the generic kernel, where it did work. Does it work only for one kernel and the others go nvidia-less?

Why don't I have to run anything as root to get RT in JACK? All I did except edit limits.conf is this extra line in my fstab:
shm /dev/shm tmpfs nodev,nosuid,noexec 0 0

---

### Post by hortstu on 2009-05-20
is this in the process of being, or has this bug been fixed?

---

### Post by WestCoastSuccess on 2009-05-20
Probably not the solution you're looking for, but I can tell you that the real-time kernel is rock-solid in 8.04 - we aren't even considering moving our studio machines off the LTS release until the real-time issues are sorted out...

---

### Post by hortstu on 2009-05-20
funny seeing you reply to me here west coast considering I'm working with you on your site right now.

Can I move from intrepid to hardy w/o losing everything i have in intrepid?

---

### Post by vivichrist on 2009-05-24
I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) and
grabed the 2.6.29-4 source deb and applied the rt16 patch to it from
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/). then copied across
the /boot/config-2.6.28-12-generic to that kernel source root directory.
did "make gconfig" and opened that config changed to full pre-emtion and
timing to 1000 like Luke Macneil has done. "make-kpkg clean" then
"CONCURRENCY_LEVEL=2 fakeroot make-kpkg --initrd --append-to-
version=-custom kernel_image kernel_headers" installed the resulting
packages headers first. and hey presto. note. CONCURRENCY_LEVEL=2
because my cpu is duel core and this required installation of certain
dev packages. this is amd64 though. can point you to a few sites if you need more details.

---

### Post by RoboNuggie on 2009-05-24
> **WestCoastSuccess said:**
> Probably not the solution you're looking for, but I can tell you that the real-time kernel is rock-solid in 8.04 - we aren't even considering moving our studio machines off the LTS release until the real-time issues are sorted out...

I have to agree, on my 8.04 machine, it is solid as a rock, and fast too... couldn't be more pleased....

---

### Post by It-Alien on 2009-05-25
when I read on Ubuntu Studio site that realtime was finally back, I flashed to the downloads and made the upgrade.. well, this doesn't work on my AMD FX2, as you already noted. This problem has been around for.. hmm.. 9 months maybe?

---

### Post by elliottb on 2009-05-31
Hi, 

I want a real-time kernel for a small home studio and like other people the stock version will freeze after 10-20 minutes, although in the 10 minutes I had pretty good sound quality.  I'm running Ubuntu 8.10.  I've never compiled a kernel before, but wow, who knew what I was missing.  

I followed the instructions on:
[http://izanbardprince.wordpress.com/...g-hacks-ahead/](http://izanbardprince.wordpress.com/...g-hacks-ahead/)
which by the way were very useful.

This got me started and configured, but because I have a AMD processor I got the error:
```
Makefile:529: /usr/src/linux-2.6.29/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-2.6.29/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2
```I fixed this with the flag --arch=x86_64.  For example:

```
$ fakeroot make-kpkg --arch=x86_64 --initrd --append-to-version=-custom1 kernel_image kernel_headers
```I'm not totally there, my installer is not creating an initrd image, though I'm still not exactly sure what that is.  And my kernel is not in the /boot/grub/menu.lst file.

When I run dpkg I get:
```
$ sudo dpkg -i linux-xenu-2.6.29-custom1_2.6.29-custom1-10.00.Custom_amd64.deb
(Reading database ... 236436 files and directories currently installed.)
Preparing to replace linux-xenu-2.6.29-custom1 2.6.29-custom1-10.00.Custom (using linux-xenu-2.6.29-custom1_2.6.29-custom1-10.00.Custom_amd64.deb) ...
Unpacking replacement linux-xenu-2.6.29-custom1 ...
Setting up linux-xenu-2.6.29-custom1 (2.6.29-custom1-10.00.Custom) ...
Please manually create an initrd image
```I have searched on the internet and I've seen reference to this problem but no solutions.  I have mkinitramfs but I have no idea how to use it or even if I should.

Any help out there on this one??

Many thanks for all the on-line guides.  Never would have made it this far.

Thanks,

Elliott

---

### Post by vivichrist on 2009-06-08
have ye tried using one of the .deb vanilla kernel source packages I used 2.6.29-4 and associated rt patch. but if you have an amd/ati gpu ye might hit a bit of trouble. ubuntu (and seeming all other distro's) use there own custom initrd code.

---

### Post by theluddite on 2009-06-25
> **vivichrist said:**
> I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) and
grabed the 2.6.29-4 source deb and applied the rt16 patch to it from
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/). then copied across
the /boot/config-2.6.28-12-generic to that kernel source root directory.
did "make gconfig" and opened that config changed to full pre-emtion and
timing to 1000 like Luke Macneil has done. "make-kpkg clean" then
"CONCURRENCY_LEVEL=2 fakeroot make-kpkg --initrd --append-to-
version=-custom kernel_image kernel_headers" installed the resulting
packages headers first. and hey presto. note. CONCURRENCY_LEVEL=2
because my cpu is duel core and this required installation of certain
dev packages. this is amd64 though. can point you to a few sites if you need more details.

Vivchrist - I'm intrigued.  I found the Jaunty real time kernel to be unusable, and I just discovered that I can't use midi with the Intrepid real time kernel.  I'd like to install my own custom kernel but your instructions are a little too bare bones for me...  Can you walk me through your instructions or point me to the sites you mentioned?  For example, can I patch a .deb file or do I need to dpkg first then patch?

---

### Post by theluddite on 2009-06-30
Since I didn't get a response, I decided to strike out on my own and compile my own custom kernel, which wasn't nearly as bad as I thought.  I followed most of the instructions that the OP referenced at [http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/]("http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/") with a few exceptions to follow.

I downloaded the 2.6.29-5 kernel image and headers from [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.5.tar.bz2]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.5.tar.bz2") and the matching realtime patch for the kernel [http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.29.5-rt22.bz2]("http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.29.5-rt22.bz2").  After I unpacked the tarball, I patched the kernel with the command "bzip2 -dc /usr/src/patch-2.6.29.5-rt22.bz2 | patch -p1". The only things I configured for the kernel were:

    * Changed to full preemption in general setup
    * Changed timing to 1000
    * Disabled the Xen/paravirtualization stuff in Processor type and features (I found the kernel wouldn't compile otherwise)

Then I compiled with the command "CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-custom1 kernel_image kernel_headers" which was recommended at this thread: [https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod]("https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod"). I found by trial and error that I needed to install the headers first, then the image contrary to what it says in the last link.  I did NOT copy the text into the pcm_lib.c.  I realized (almost too late) that this instruction does not apply to any kernel after 2.6.29.  After that, I was able to boot into my kernel... but I had no sound.

Since I had to kill pulseaudio to get sound to work before I had compiled the new kernel, I figured that was the culprit. I was able to make pulse functional (apps wouldn't freeze when there was a sound event) using [http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+connection+refused]("http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+connection+refused"), but I still couldn't hear anything. Now this is where the magic happened: I updated to Jaunty from Intrepid and voila! Everything worked! I don't know what the problem was with the kernel before, but it's hummin' now. Zero xruns, jack, midi, no crashes (fingers crossed) and my sound works fine.

---

### Post by vivichrist on 2009-07-01
um yes I found that using the sources from kernel.org and patching and compiling. produced an unbootable kernel for me. there's no initrd and amd multicore cpu's have sync problems. and yes install the linux source.deb and you will find a linux source.bz2 in /usr/src/. extract that to ... say /home/myhome/ (then patch it) etc. is what I did. the .deb is not altogether vanilla, I think, and has ubuntu customised initrd code. restricted drivers and dkms caused problems with postinstall scripts in the produced debs. so had to uninstall restricted drivers and reinstall restricted drivers to allow the debs to finish install.

---

### Post by symon1980 on 2009-07-04
ARGHHHH! Im glad in a way that I found other people having the same problem! WHY HASN'T UBUNTU FIXED THIS PROBLEM YET!!!! soooo frustrating!
I can't record anything anymore in ubuntu!
ugh!
I just boot into Opensuse 11.1 kde 4.3 rc when it comes to having to record... no problems with realtime in Opensuse. 
Im getting really annoyed with ubuntu not fixing important bugs...........

---

### Post by asw20pilot on 2009-07-10
Add me to the chorus of frustrated users. Like others here, I have experienced rock solid rt kernels in 8.04 - to the point that I wondered why the rt kernel wasn't just the default Ubuntu kernel. Then one day an automatic update installed a totally useless kernel that would hang immediately upon starting JACK. I don't remember the version number. In 9.04 at least I can start up and play my keyboard for a while - sometimes for a long time - but then my machine just suddenly hangs completely without responding to any input. Only the power button will restart it.

Please, please, please someone fix this. I should never have upgraded and I will definitely be more careful trusting upgrades in the future. Assuming, that is, that I ever get a stable rt kernel again!

Best regards,
Mikkel

---

### Post by symon1980 on 2009-07-25
guys... i found a fix FINALLY!

(work around)
in limits.conf.... replace the @audio    parts with your username....   eg:    @username

mine looks like  

@kaddy - rtprio 99
@kaddy - memlock unlimited
@kaddy - nice -19
# End of file

save
logout, login
and wallah!
you can now use Realtime in qjack!!! :)

i might add... make sure you add permission to your audio group... 

sudo adduser "username" audio


im sure this will relieve ALOT of you :)

---

### Post by interim descriptor on 2009-07-25
> **symon1980 said:**
> guys... i found a fix FINALLY!

(work around)
in limits.conf.... replace the @audio    parts with your username....   eg:    @username


Very awesome that's working for you!

My limits.conf works with @audio, or any other group, just so long as my user is a member of that group. Starting JACK gives the process realtime priority.

Also, you probably understand this, but for reference, realtime priority only works as desired when you also have a functional realtime kernel. This is especially true for audio.



Very sad to see that this thread is still alive and kicking... Anybody want to guess whether this is fixed in 9.10...? :(

---

### Post by symon1980 on 2009-07-25
actually.... I've been recording music in linux for about 4 years, and i have NEVER installed a realtime kernel to get realtime working. All i've been doing is editing the limits.conf file and then realtime works in jack. therefore i never felt the need to install a realtime kernel. and the recording quality has been great!
its only since Ubuntu jaunty that realtime wouldn't work.... and its apparently a bug, I dunno... all i know is that it has worked for years and all of a sudden it didn't, but this little work around worked for me after months of frustration of not being able to use realtime with jaunty.

---

### Post by interim descriptor on 2009-07-25
> **symon1980 said:**
> i have NEVER installed a realtime kernel to get realtime working.

I've been writing music software on linux for the last 10 years, so please allow me to convey what I've learned about realtime audio, for the benefit of those reading this.

"Realtime" is actually a pair of distinct concepts:
[LIST=1]
[*]Process priority
[*]Kernel scheduling preemption
[/LIST]

Even in the absence of a realtime preemptable kernel, it's still possible for a process to have realtime priority. In this case, the kernel will do its best to ensure the process gets scheduled as frequently as possible. However, other processes that make expensive system calls might interfere with your realtime process's timely scheduling.

This is where a kernel with realtime preemption shines: Even if another process is in the middle of a system call, a realtime kernel will suspend this process's execution if a realtime process of higher priority desires to be executed. This *ensures* that realtime processes will have access to the CPU at their required interval.

It sounds like you've been successfully working with realtime process priority alone, which is great! You might be able to get even lower latency on your audio buffers if you were using a realtime preemptable kernel, if this interests you. It's quite possible that you're getting satisfactory performance already, in which case I'm certainly not suggesting you muck around with a realtime kernel, when you'd rather be working on music.

...and that concludes today's lesson! :D

---

### Post by bcschmerker on 2009-07-26
> **vivichrist said:**
> have ye tried using one of the .deb vanilla kernel source packages I used 2.6.29-4 and associated rt patch. but if you have an amd/ati gpu ye might hit a bit of trouble. ubuntu (and seeming all other distro's) use there own custom initrd code.Thanks for the heads up on the nature of the problems that I encountered after upgrading my Everex from an all-VIA rig (under a 1.5 GHz VIA C7-D) that ran Kernel 2.6.22-16-rt without problems through two chipsets under an Advance Micro Devices Athlon X2 5600+, neither of the last two handling 2.6.24-23-rt at all well; apparently the -rt flavors are optimized around all-Intel hardware and 100% compatibles such as the all-VIA rig mentioned above, meaning I could consistently run Karmic with a 2.6.30-xx-rt Kernel on a Core i7/X58 rig with minimal trouble.

My Everex, packing a Gigabyte MA78GM-S2HP 'board (Advanced Micro Devices Athlon X2 5600+ and 780G chipset), runs just fine on Kernel 2.6.24-24-generic but may need a custom compile and matching InitRD.img, including boot scripts, to run the real-time enhancements on AMD64 architecture using a possible Kernel 2.6.31-1-amd64rt for Ubuntu Lucid Lynx (testing starting November 2009 concurrent with the official release of 9.10 Karmic Koala).

---

### Post by symon1980 on 2009-07-26
...and that concludes today's lesson! :D[/QUOTE]


thanx for the indepth info, I certainly did learn something from that :)

what sort of music do you record? got a link to any samples?

heres my link     [www.myspace.com/kaddy080](www.myspace.com/kaddy080)


for anybody who is interested in Aussie Hiphop... probably not many but thats about the best quality I can achieve with the setup I have at the moment....

I also use LMMS when I create beats... eg "americanized" but i started to get lazy and pay for beats already made :)

---

### Post by trulan on 2009-08-15
> **bcschmerker said:**
> ..... to run the real-time enhancements on AMD64 architecture using a possible Kernel 2.6.31-1-amd64rt for Ubuntu Limber Lemur (anticipated testing starting October or November 2009 concurrent with the official release of 9.10 Karmic Koala).
Kernel 2.6.31-1-RT is now available for testing in Karmic.  So far, performance has been great.  But I have no trouble with the Jaunty RT kernel either on my desktop.  (AMD 64).  The real test for me will be when I attempt to load it on my laptop.  But I can't afford to break that ATM and will wait for a more stable release.

---

