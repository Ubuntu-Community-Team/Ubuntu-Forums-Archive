---
title: "hda intel mic problem"
date: 2006-09-16
forum: Desktop Environments
---

### Post by corteze on 2006-09-16
I have a laptop HP dv5220us wjicj is using hda intel for sound. Everything works except microphone. Alsamizer sees microphone as capture device but it's not working.

Any ideas?

---

### Post by eitan on 2006-09-19
i have the same exact problem.  i just recently bought an hp dv2000t laptop.  it's got the intel hda audio controller.  i've given up trying to get the mic to work.  this is really frustrating.  i can't skype!  (running dapper drake with all the updates)

here are the problems i've encountered:
  [a] can't get the built-in mic to work
  [b] can't get any mic i plug in to work
  [c] audio out no longer works after waking up computer from hibernate
  [d] when audio out works, and i plug in headphones, the speakers remain on
  [e] can't get built-in webcam to be recognized (so much for ekiga!)

my guess is that we might see an improvement possibly when edgy eft comes out assuming we'll have updated intel drivers.

while i'm on a roll, here's my rant on what ubuntu needs to keep on growing/succeeding, in order of importance:

 [a] support for automatic sync with projector
 [b] a strong presentation application (no, ooo does not qualify)
 [c] good hardware support
 [d] seamless multimedia support
 [e] getting sleep to work reliably (and getting it to actualy preserve battery consumption while sleeping!).

---

### Post by mexlinux on 2006-09-20
I have the same problem with mic  in HDA Intel in an Dell Inspiron 630m
I need my microphone!
Any one have a clue?
Thanks

---

### Post by effoff on 2006-09-20
...same problem on several laptops (Intel)....

---

### Post by odinfromvalhalla on 2006-09-20
i had the same problem and i have looked over forums here/alsa and after almost 2 weeks of trying i have decided to buy a 8$ CMI card which worked by default. i just pluged it in and it worked

---

### Post by rafael.angel on 2006-09-20
well... i have an LG LW20 laptop that uses Intel HDA audio too, with Dapper Drake installed.

I dont know how to solve the mic problem globally, but thats what i do to get it working in Skype:

Go to Tools menu, then Options, and select Sound Devices in the left menu and you will see that HDA Intel is selected. 

In Audio System select OSS, then in Calls and Ringing selec /dev/dsp

Now make a test call to see if your mic works.

---

### Post by mexlinux on 2006-09-21
There is already a bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42600]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42600")

---

### Post by mexlinux on 2006-10-30
Since edgy 6.10 comes with an old ALSA, this problem is still present

---

### Post by froggontherocks on 2006-11-16
I would like to throw in that it dosent work for me either

---

### Post by JayTee on 2006-11-16
I had this same problem and tried a few things but what worked for me was when I went into Alsamixer I noticed the MUX settings were set to 0 or off and increasing the MUX volume allowed my mic to work. Prior to this I could only hear my test recordings at a very low level. For some reason the MUX setting must be at 50% or higher to get usable volume for the microphone input. Hope this helps others here.

---

### Post by ulefr01 on 2006-11-30
the gnome-volume-control is showing me : Microphone - 100 %
But the microphone can not recording sounds.
the following combination is not working :
arecord /var/tmp/myvoice.wav 
	to record 
	ctrl+C to stop
play /var/tmp/myvoice.wav
	to play

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Can you help ?

---

### Post by vicnov on 2006-12-01
Recently, I have got my microphone working on hda intel (conexant 5047 codec), look:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

---

### Post by mikewhatever on 2006-12-20
> **vicnov said:**
> Recently, I have got my microphone working on hda intel (conexant 5047 codec), look:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

How about posting some instructions?

---

### Post by Oktan on 2006-12-20
Hmm. I had the same problem on my Fujitsu Siemens Amilo si 1520 after the new kernel update 2.6.17-10-generic. (using hda-intel chipset)
I got my internal mic up and running. by installing alsa-driver-1.0.13 alsa-lib-1.0.14rc1 alsa-utils-1.0.14 and alsa-oss1.0.12 from [http://www.alsa-project.org/](http://www.alsa-project.org/)
also my my line out is working flawless :) 
Still trying to get my line in mic to function. 
If anyone wants a HOWTO I be happe to post one tomorrow.
sorry for my bad english typing :(

---

### Post by ariel on 2006-12-20
Hi Oktan, if you can post a howto on how to upgrade Edgy's Alsa's to 1.0.13 that would be great. 

I have a Dell D820 which (I think) does not use the hda chipset, however it shows the exact same problem. I checked in Alsa's 1.0.13 changelog and apparently my problem is fixed there (related to stac92 support).

thanks
A

---

### Post by vicnov on 2006-12-21
**Updated:** new 2.6.20 kernels shipped with Ubuntu 7.04 (Feisty) work correctly, you do not need to follow these instructions if you have such kernel.

> **mikewhatever said:**
> How about posting some instructions?

OK, here are instructions for HP dv8000 notebooks (HDA Intel audio with Conexant 5047 codec).

0. backup your current driver
    tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
    (if something goes completely wrong, you will be able to extract previous drivers).

1. download and unpack latest alsa-driver, alsa-lib, alsa-util (I tried 1.0.14rc1):
    [http://www.alsa-project.org/alsa/ftp/driver/](http://www.alsa-project.org/alsa/ftp/driver/)
    [http://www.alsa-project.org/alsa/ftp/lib/](http://www.alsa-project.org/alsa/ftp/lib/)
    [http://www.alsa-project.org/alsa/ftp/utils/](http://www.alsa-project.org/alsa/ftp/utils/)

2. build and install alsa-driver:
  ./configure --with-cards=hda-intel
  make
  sudo make install

3. build and install alsa-lib:
  ./configure
  make
  sudo make install

4. build and install alsa-utils:
  ./configure
  make
  sudo make install

5. open /etc/modprobe.d/alsa-base, add to the end of file:
  options snd-hda-intel model=laptop

6. reboot Linux

7. run alsamixer, set sound levels; set INTERNAL mic, Capture and Mic Bypass to "capture" (by pressing Space)

Now EXTERNAL microphone should work.

P.S. My microphone is in fact external but it works when I turn on internal microphone...

One minor bug - alsamixer settings (sound level, etc.) are not saved after restart, so you need to run alsamixer every time after restart.

Last time when something serious was updated (kernel or initrd image) I was required to build and install alsa again (I have repeated all the steps above and it is working again).

---

### Post by vicnov on 2006-12-21
Maybe, if you have another model (not HP dv8000) or desktop PC you can try different settings for 'model' parameter in /etc/modprobe.d/alsa-base
All possible values are documented in alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt

After changing the 'model' values you should reload sound driver or restart Linux.

---

### Post by mikewhatever on 2006-12-21
THANKS Vicnov. Just saw your post and I will try the instructions. The laptop I have is HP DV5000. It should be similar to DV8000.

Update: The commands your posted give me 'no such directory' error. Obviously, a location is missing there, but I am too green in Linux to know that. I'll look around, still thanks.

---

### Post by vicnov on 2006-12-21
> **mikewhatever said:**
> 
The commands your posted give me 'no such directory' error.
No problem!

In the steps 2,3,4 above you should first go to the corresponding directory (where you have unpacked 'driver', then 'lib', and then 'utils' archives) and then execute the commands. This is because each directory (driver, lib, utils) has a file called 'configure' and also a make-file , Below are detailed steps 2,3,4: 

2.
cd /<full_path>/alsa-driver-<version>
./configure --with-cards=hda-intel
make
sudo make install

3. 
cd /<full_path>/alsa-lib-<version>
./configure
make
sudo make install

4.
cd /<full_path>/alsa-utils-<version>
./configure
make
sudo make install

(<full_path> is a path from the root of filesystem (/) to the directory where you have unpacked archives)

---

### Post by vicnov on 2006-12-21
mikewhatever,

you can check what sound card and codec are installed in your computer. Try these 2 commands:

```
lspci | grep -i audio
cat /proc/asound/card0/codec#0 | grep -i codec
```

For example, I see the following on my HP dv8000:
```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

$ cat /proc/asound/card0/codec#0 | grep -i codec
Codec: Conexant CXT5047
```

---

### Post by mikewhatever on 2006-12-21
Just followed that, but in step 4, got error message.
> 
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
none@hello:~/scr/alsa/alsa-utils-1.0.14rc1$ make
make: *** No targets specified and no makefile found.  Stop.
none@hello:~/scr/alsa/alsa-utils-1.0.14rc1$ sudo make
make: *** No targets specified and no makefile found.  Stop.
none@hello:~/scr/alsa/alsa-utils-1.0.14rc1$ sudo make install
make: *** No rule to make target `install'.  Stop.
none@hello:~/scr/alsa/alsa-utils-1.0.14rc1$ 


and the typing 'make' didn't work.

---

### Post by vicnov on 2006-12-21
> **mikewhatever said:**
> Just followed that, but in step 4, got error message.
and the typing 'make' didn't work.

Seems that you should install 'curses' library. Try the following command:
```
sudo apt-get install libncurses5 libncurses5-dev
```
If you get error "package(s) can not be found", you will need to configure your package repositories correctly, look here for details: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

After installing the libraries, repeat all steps to build alsa because your error was during 'configure' step (and NOT in 'make' step).

---

### Post by mikewhatever on 2006-12-21
There was not much more left to do, but reboot. It looks like the step with asla-utils failed. I still have sound, however, but no working mic. Some more controls appeared in the Volume Control, including extmic box.

Just saw the post above. Downloading the library now. Should I continue from step 4, or start all over?

---

### Post by vicnov on 2006-12-21
> **mikewhatever said:**
> Should I continue from step 4, or start all over?
Try starting from step 4. Alsa-utils is not critical for sound and microphone in fact. You can try without utils first.

Could you provide information about you sound card and codec (see one of my posts above with instructions)?

---

### Post by vicnov on 2006-12-21
mikewhatever,

note, that after installing the driver and rebooting Linux, you should start 'alsamixer' in terminal and set correct "check-boxes" and move up sound levels (everything is turned off by default).
Use space button to turn on Capture and External or Internal Mic (in alsamixer). Up/Down buttons to set volume level for Capture. Tab button may be used to switch views in alsamixer.
Make several attempts with different combinations, it may help.

---

### Post by vicnov on 2006-12-21
Here is how my alsamixer looks like:
[http://ubuntuforums.org/attachment.php?attachmentid=21455&stc=1&d=1166722616]("http://ubuntuforums.org/attachment.php?attachmentid=21455&stc=1&d=1166722616")

---

### Post by mikewhatever on 2006-12-21
[quote
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
$ cat /proc/asound/card0/codec#0 | grep -i codec
Codec: Conexant CXT5047
[/quote]

My alsamixer looks different in terminal. There are Master PCM and IEC958 controls. The last one is set to 0 and I can't move it. I can move the other two. Space key does nothing.

---

### Post by vicnov on 2006-12-21
> **mikewhatever said:**
> My alsamixer looks different
Press 'Tab' button several times in alsamixer, you will see other controls (including Capture, Internal Mic, External Mic).
You have exactly the same card and codec, so the same solution shoud help you.

---

### Post by mikewhatever on 2006-12-21
You'r right, it is the same. The tree, Micbypass, Capture and extmic are set to capture. I can only set one mic to capture there, internal or external.

---

### Post by mikewhatever on 2006-12-21
I just set intmic to capture and the external one works. Does not make much sense, especially because there is no intmic in this laptop. :-k  But it works, what do I care. Vicnov, THANKS ALOT.

---

### Post by vicnov on 2006-12-21
> **mikewhatever said:**
> I just set intmic to capture and the external one works. Does not make much sense, especially because there is no intmic in this laptop.

This is because Conexant codec is not officially supported yet... So it is something like a hack ;-) Thanks to Tobin Davis from ALSA team and other people who have made Conexant cards working!
Now the situation is changing - I read in mail archives that Conexant is ready to provide their specifications to ALSA team. You can see it here [http://news.gmane.org/gmane.linux.alsa.devel](http://news.gmane.org/gmane.linux.alsa.devel) (make search by 'conexant' word).

Good luck and welcome to Linux! :) 

P.S. You will need to run alsamixer and set correct values there every time after Linux restart (seems to be a bug).
P.P.S. Sometimes after serious updates (like kernel updates), maybe, you will need to repeat all the steps (build and install the driver). Also, if this occurs, I would recommend to download a newer alsa-driver and alsa-lib version.

---

### Post by ariel on 2006-12-21
Thanks Vic, 

   I couldn't wait for your instructions and went ahead and did the classical ./configure, make, sudo make install in all the source tarballs I downloaded from Alsa-project.

  Also before doing the make installs, I ensured that all tarballs passed the ./configure and make successfully.

  The only difference with your message below is that I didn't use the "--with-cards=hda-intel" 

  Maybe for that reason after installing all and rebooting the machine sound worked but selecting ALSA in System > Preferences > Sound > Devices didn't work at all. I fixed that doing:

           asoundconf reset-default-card

  After that, I did an alsaconf, then reboot, then selecting Alsa for all devices worked like a charm, including the MIC.  One caveat is that for the MIC to work, I had to open Volume Control > Alsa Mixer and for capture, select LINE, then select MIC again. Weird, but works.

Thanks,
Ariel

  

> **vicnov said:**
> No problem!

In the steps 2,3,4 above you should first go to the corresponding directory (where you have unpacked 'driver', then 'lib', and then 'utils' archives) and then execute the commands. This is because each directory (driver, lib, utils) has a file called 'configure' and also a make-file , Below are detailed steps 2,3,4: 

2.
cd /<full_path>/alsa-driver-<version>
./configure --with-cards=hda-intel
make
sudo make install

3. 
cd /<full_path>/alsa-lib-<version>
./configure
make
sudo make install

4.
cd /<full_path>/alsa-utils-<version>
./configure
make
sudo make install

(<full_path> is a path from the root of filesystem (/) to the directory where you have unpacked archives)

---

### Post by mikewhatever on 2006-12-27
> **vicnov said:**
> Good luck and welcome to Linux! :) 

P.S. You will need to run alsamixer and set correct values there every time after Linux restart (seems to be a bug).
P.P.S. Sometimes after serious updates (like kernel updates), maybe, you will need to repeat all the steps (build and install the driver). Also, if this occurs, I would recommend to download a newer alsa-driver and alsa-lib version.

Thanks again for help. I don't have to change anything after restart, it just works since the first time. Haven't yet had any kernel updates. :-D

---

### Post by otakuj462 on 2007-01-04
I'm running a new edgy eft install on my Dell Inspiron 1300.
This mic problem had been troubling me for months ever since I first installed Gentoo on this machine last July. I believe I just found a fix [here]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038").
From the report:
> 
Just fixed this on my machine - but I believe that the fix will work for anyone with this particular mic/input problem that has the SigmaTel STAC9200, 922x or 927x chipset for Intel HDA. Ok, here's what you do:

1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

options snd-hda-intel model=ref

Done.
Now reload your modules or reboot. Go into alsamixer. If everything went as expected, you should see some new options, eg - 'front mic' as an input source and IEC958 (S/PDIF) settings. Play with these freely later - they have nothing to do with the mic problem. Anyway, make sure the input is set to mic and nothing else. Turn your capture setting all the way up to 100%, capture playback at maybe 50%; tweak these to your tastes. Now, record something using your favorite audio recording utility.

eg - arecord -f cd TheSoundOfSuccess.wav

Play it back. Hopefully, everything is good and nice.


Audio recording now works for me, no further configuration required. :)

---

### Post by moptop on 2007-01-05
I've just found this thread, thanks so much!  My internal mic is now working on a dell d820 running edgy/feisty for the first time -- I didn't have to compile any of the new alsa packages, just upgraded those packages to the feisty versions.  so thanks!

The one thing I'm having difficulty with -- I would like to write a simple script using amixer to toggle the capture source a couple of times so I don't haveto worry about starting alsamixer etc.  but amixer doesn't seem to want to set the 'input source' -- the value never changes no matter what I write.  

so, on my machine, there are two input sources listed:  'mic' and 'front mic'.  'front mic' is the external mic input, 'mic' is the internal mic.  I try this:

$ amixer sset 'Input Source' 'Front Mic'
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'

see, nothing changes.  I have to go into alsamixer and change the value manually.  I'd rather not have to do that, esp. since I want my family to be able to just run skype without complaining about how lousy linux is etc.  So I want to write a script that sets the environment up for them...  anyway, any idea why the amixer command doesn't work here?

and a side note:  I (and I guess most people on this thread) have two capture controls, "Capture" and "Capture Mux".  What's the diff between them?  Do I need to know which is which for any reason?

Thanks much,
matt

---

### Post by shadowhywind on 2007-01-13
I am wondering if someone could help me, i have an hp dv6040, upgraded to the newest alsa version 1.0.14rc1. and i still can not get my mic to work. in alsaconfig i have Master, PCM, LineIn , Mix Bypass, IEC958, Capture and ExtMic. 
 At the moment i have MicBypass, Capture, and ExtMic all set for Capture and i still get nothing. Any ideas?

---

### Post by dvarsam on 2007-01-31
Hello!

I seem to have the same problem here...!!!

I followed all your steps.
But when I get in step 4, when I perform the "make" command, I get this"

[quote=dvarsam]elena@elena-desktop:~/Desktop/alsa-utils-1.0.14rc2$ make
make: *** No targets specified and no makefile found.  Stop.[/quote]

What do I do?

Note: All folders were extracted to Desktop & worked on them from there...
Is that ok?
Please help...

Thanks.

---

### Post by vicnov on 2007-02-01
dvarsam,

seems that you have got errors on the previous step (running './configure').
Please look at configure output (maybe warnings, errors).

---

### Post by dvarsam on 2007-02-02
[QUOTE=vicnov]dvarsam,
seems that you have got errors on the previous step (running './configure').
Please look at configure output (maybe warnings, errors).[/QUOTE]

Hello & thanks for your reply!

I am getting the following errors:
```

root@elena-desktop:/home/elena/Desktop/alsa-utils-1.0.14rc2# [color=blue]./configure
[/color]checking for a BSD-compatible install... /usr/bin/install -cchecking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
```

I followed the advice, looking for available curses libraries...
So, I went & installed the following libraries found:

1. libcurses-perl
2.libcurses-widgets-perl
3.libcurses-ui-perl
4.libcurses-ruby

But the error does NOT go away...
What package do I need to install?

Thanks.

---

### Post by dvarsam on 2007-02-02
I solved that part!

It was the package "[color=blue]libncurses5-dev[/color]" that was missing!

Now I am NOT sure regarding step 5:

[quote=vicnov]
5. Open the file "/etc/modprobe.d/alsa-base" & add to the end of file:
[color=blue]options snd-hda-intel model=[/color][color=red]laptop[/color]
[/quote]

The problem is with the above red part...
The other user had a laptop, so the above command was appropriate to setup his machine...
...and NOT mine...

So, I used the command "**aplay -l**" & got:

```
elena@elena-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Then I visited the file "home/elena/Desktop/alsa-driver-1.0.14rc2/alsa-kernel/Documentation/ALSA-Configuration.txt" & located my "[color=blue]ALC882[/color]" Device:

```
 ALC882/885
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          arima         Arima W820Di1
          macpro        MacPro support
          auto          auto-config reading BIOS (default)
```

So, should I try using the following option:

[color=blue]options snd-hda-intel model=[/color][color=red]auto[/color]

I also _noticed_ that my Desktop has 6 audio out jacks & an SPDIF I/O jack.
So, isn't it better to use the following command:

[color=blue]options snd-hda-intel model=[/color][color=red]6stack-dig[/color]

I am asking you because I am afraid.
I don't want to end up burning the "audio-out" jacks or caching some "fire"... :)

Thanks.

---

### Post by vicnov on 2007-02-02
Seems that you need the following libraries:

ncurses-base
ncurses-bin
libncurses5

I see that you are trying to build "alsa-utils" (not the driver itself). Even if you can not build "alsa-utils", you can skip this step - it does not prevent from installing the driver itself.

---

### Post by vicnov on 2007-02-02
**dvarsam**
Great that it works for you!

As for 'model' option - first try using 'model=auto'. If you do not see all necessary controls in alsamixer, then try 'model=6stack-dig'.
As I know, it is not dangerous, it just defines which controls are shown in alsamixer.

---

### Post by dvarsam on 2007-02-02
[QUOTE=dvarsam]So, should I try using the following option:

[color=blue]options snd-hda-intel model=[/color][color=red]auto[/color]

I also _noticed_ that my Desktop has 6 audio out jacks & an SPDIF I/O jack.
So, isn't it better to use the following command:

[color=blue]options snd-hda-intel model=[/color][color=red]6stack-dig[/color]
[/QUOTE]


I used the 2nd command from above.
I restarted the PC checked "alsamixer" - everything was activated...
Then I recorded something in the mic & listened to it!!!
Since everything was activated in "alsamixer" I wanted to closed unused channels...
So I opened "alsamixer" & set volume to zero & muted, channels I didn't want to be open...
Then I went to check on the mic...
It was NOT recording!!!
I thought that maybe I closed something I should NOT have...
So, I opened "alsamixer" & re-enabled everything!!!
I then visited the mic, recorded something & could NOT hear anything...
I played with the settings of "Applications\Sound & Video\Sound Recorder"...
... still not getting anything!
I decided to re-configure, re-make & re-install all packages...
And so I did!
Nothing changed...
I can't record anything...
What do I do now?

Thanks.

---

### Post by vicnov on 2007-02-02
Just no panic ;-)

I think you have set something incorrectly in alsamixer. Please attach a screenshot of you alsamixer settings. Try to turn ON all channels and set volume levels to maximum everywhere.

Also, as I remember, "Applications\Sound & Video\Sound Recorder" worked bad for me (not worked sometimes). More reliable way to test you microphone is 'arecord' and 'aplay' commands. Read manual for 'arecord' (type "man arecord").

---

### Post by dvarsam on 2007-02-02
[QUOTE=vicnov]Just no panic ;-)
I think you have set something incorrectly in alsamixer. Please attach a screenshot of you alsamixer settings. Try to turn ON all channels and set volume levels to maximum everywhere.

Also, as I remember, "Applications\Sound & Video\Sound Recorder" worked bad for me (not worked sometimes). More reliable way to test you microphone is 'arecord' and 'aplay' commands. Read manual for 'arecord' (type "man arecord").[/QUOTE]

Thank you for your reply!
I will do all that ASAP.

BTW: How do I restart the "alsa" drivers?
I would prefer to restart the driver than to have to shutdown & restart the whole PC...
I tried using "[color=blue]sudo /etc/init.d/[color=red]alsa[/color] restart[/color]" but I keep getting "**command not found**"...
I also tried using "[color=blue]sudo /etc/init.d/[color=red]alsamixer[/color] restart[/color]", but again I am getting "**command not found**"...
What is the correct syntax?

Thanks.

---

### Post by vicnov on 2007-02-02
> **dvarsam said:**
> I would prefer to restart the driver than to have to shutdown & restart the whole PC...

It's not so simple in fact, but you can do this as follows:

1) see a list of loaded sound modules:
lsmod | grep snd
This will show you sound modules with dependencies.

2) Stop modules in the correct order (to meet dependencies):
sudo rmmod module_name1
sudo rmmod module_name2
...

3) Start new driver (module):
sudo modprobe snd-hda-intel

Sometimes a simple command helps:
rmmod snd-hda-intel
But other times it say that you should stop other modules first...

So I would recommend just to reboot !

---

### Post by dvarsam on 2007-02-02
Thank you for your reply!

I managed to get my mic work on one PC.
But I tried the same on another PC & got into trouble...
Basically I have NO audio at all!

For example:

1. A command "[color=blue]lsmod | grep snd[/color]" gives me this:

```
root@dimitris-desktop:/etc/modprobe.d# lsmod | grep snd
root@dimitris-desktop:/etc/modprobe.d#
```

So, I guess that means nothing is running!

2. A command "[color=blue]aplay -l[/color]" gives me this:

```
root@dimitris-desktop:/etc/modprobe.d# aplay -l
aplay: device_list:204: no soundcards found...
```

I guess it could NOT be worse...

3. A command "[color=blue]lspci | grep -i audio[/color]" gives me this:

```
root@dimitris-desktop:/etc/modprobe.d# lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER ([color=blue]ICH5[/color]/ICH5R) [color=blue]AC'97[/color] Audio Controller (rev 02)
```

4. A command "[color=blue]cat /proc/asound/card0/codec#0 | grep -i codec[/color]" gives me this:

```
root@dimitris-desktop:/etc/modprobe.d# cat /proc/asound/card0/codec#0 | grep -i codec
cat: /proc/asound/card0/codec#0: No such file or directory
```

Based on the above #3 & on the following info I found inside the file ""home/dimitris/Desktop/alsa-driver-1.0.14rc2/[color=blue]alsa-kernel/Documentation/ALSA-Configuration.txt[/color]":

```
Module snd-intel8x0
  -------------------

    Module for [color=blue]AC'97[/color] motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				[color=blue]ICH5[/color], ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.
```

Based on the facts that [color=blue]ICH5[/color] & [color=blue]AC' 97[/color] are common in the above, I thought that I could use the same drivers for that Mobo too!
The only thing that did NOT seem to match is the Chipstet - mine is Intel's [color=blue]865[/color] Series [color=blue]Chipset[/color]...
So, I compiled, make & make install everything!
Then it was time to add that line inside the "[color=blue]/etc/modprobe.d/alsa-base[/color]" file.
So, I thought to add the line "[color=blue]options snd-intel8x0 model=ac97_clock[/color]".

I restarted my Ubuntu & realized that nothing is working...!
Even the Top Panel shows the "Volume Control" icon with a Red "X" icon placed on top of it...

I then decided to use the line "[color=blue]options snd-intel8x0 model=0[/color]".
I rebooted & nothing changed...

BTW the file "[color=blue]/etc/modprobe.d/alsa-base[/color]" used to contain:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modpro$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbi$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { $
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbi$

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
[color=blue]options snd-intel8x0[/color][color=red]m index=-2[/color]
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

```

I have added the above file because I want you to notice the "blue" line above...
It looks like the line I used - i.e. "[color=blue]options snd-intel8x0 [/color][color=red]model=0[/color]", except the "red" parts...

Finally, this is how the output of the command "[color=blue]aplay -l[/color]" looked like, before I mess things up:

```
dimitris@dimitris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So, where do I start from & what do I do?

Thanks.

---

### Post by vicnov on 2007-02-02
**dvarsam**
Not sure that I can give a good advise here because this is a different audio card (intel8x0 if I understand correctly). I have not used this card yet...

Just a proposition - maybe you have started './configure' with incorrect params? Seems that for intel8x0 you shoudl run it like this:
./configure --with-cards=intel8x0

Look at this link for more details:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0)

---

### Post by vicnov on 2007-02-02
**dvarsam**
Also, it is useful to look at kernel messages after loading modules (or after reboot), just type 'dmesg' command - maybe you will see some errors.

---

### Post by dvarsam on 2007-02-02
Dear user "vicnov",

Thanks for your reply!

[quote=vicnov]Just a proposition - maybe you have started './configure' with incorrect params? Seems that for intel8x0 you should run it like this:
./configure --with-cards=intel8x0

Look at this link for more details:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0)[/QUOTE]

I forgot to mention...
I did use that "--with-cards=intel8x0" parameter.
But I used that link you provided & got here:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix)

I think that the one I should be going for is "intel8x0m".
All that, based on the contents of the file "[color=blue]/etc/modprobe.d/alsa-base[/color]" I provided above...

So, I used the command "[color=blue]./configure --with-cards=intel8x0[color=red]m[/color] --with-sequencer=yes[/color]" for the alsa-driver.
However, I don't know what line to add to the "[color=blue]/etc/modprobe.d/alsa-base[/color]"... :confused:
So, without adding a line, I rebooted the PC...
But then again nothing happened...

I have NO clue on this...
Maybe I should re-format the Hard Drive...
Any ideas?

P.S.> I also checked the "dmesg" command, but didn't find anything interesting regarding the audio drivers.
Also, when typing "alsamixer" in the Terminal, I get "alsamixer: function snd_ctl_open failed for default: No such device".

---

### Post by vicnov on 2007-02-02
OK, let's try some reasonable steps (it's not time to reformat the disk; not yet ;-) ).

First, look into the following directory: /lib/modules/your_kernel/kernel/sound
Somewhere in it (or in subdirectories - maybe in pci/ac97) you should see your modules, especially snd-intel8x0.ko or snd-intel8x0m.ko

Then, let's modify your /etc/modprobe.d/alsa-base file. "Comment" (or remove) your previous line for running snd-intel8x0 and add the following line:
options snd-intel8x0 model=auto
OR
options snd-intel8x0m model=auto

Sorry, I do not understand the difference between intel8x0 and intel8x0m... Seems that 'm' means 'modem'?

After that, let's try to load the module manually and see what happens:
dmesg -c /dev/null    (this will clean kernel messages)
modprobe snd-intel8x0m
dmesg    (this will show new messages)

Is something changed after this?

---

### Post by vicnov on 2007-02-02
Also, after you have loaded the module, please check that it is loaded:
lsmod | grep snd  (the output should contain 'snd-intel8x0' or 'snd-intel8x0m')

---

### Post by dvarsam on 2007-02-02
Hello & thanks for your reply!

Sorry I was late...
I didn't see that you had replied...


[quote=vicnov]First, look into the following directory: /lib/modules/your_kernel/kernel/sound
Somewhere in it (or in subdirectories - maybe in pci/ac97) you should see your modules, especially snd-intel8x0.ko or snd-intel8x0m.ko[/quote]

This is what I found:

```
root@dimitris-desktop:/lib/modules/2.6.17-10-generic/kernel/sound/pci# ls
ac97     ca0106       echoaudio  ice1712   nm256    rme9652  ymfpci
ali5451  cs46xx       emu10k1    korg1212  pcxhr    trident
au88x0   cs5535audio  hda        mixart    riptide  vx222
```

BTW, the above folders "ac97" & "hda" are empty.
Not sure which folder you are interested in...

[quote=vicnov]Then, let's modify your /etc/modprobe.d/alsa-base file. "Comment" (or remove) your previous line for running snd-intel8x0 and add the following line:
options snd-intel8x0 model=auto
OR
options snd-intel8x0m model=auto[/quote]

OK, did this!

[quote=vicnov]Sorry, I do not understand the difference between intel8x0 and intel8x0m... Seems that 'm' means 'modem'?

After that, let's try to load the module manually and see what happens:
dmesg -c /dev/null    (this will clean kernel messages)
modprobe snd-intel8x0m
dmesg    (this will show new messages)

Is something changed after this?[/QUOTE]

I typed the "dmesg" command with the parameters you metioned.
And the command "modprobe snd-intel8x0m" gives the following output:

```
root@dimitris-desktop:/etc/modprobe.d# modprobe snd-intel8x0m
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ac97-bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/pci/snd-intel8x0m.ko': No such file or directory
```

I don't understand here...
Why can't it find the folders?
This was what I got before!
The same thing!!!

I am not sure what we are looking for...

And this is the output of the new "dmesg" command:

```
root@dimitris-desktop:/# dmesg
root@dimitris-desktop:/#
```

Basically... Nothing!!!

I have NO clue now...
Just "hit" me with the next step...

Output of the command "lsmod | grep snd":

```
root@dimitris-desktop:/# lsmod | grep snd
root@dimitris-desktop:/#
```

Nothing!
The module does NOT seem loaded?

Thanks.

---

### Post by vicnov on 2007-02-02
Hello and Welcome !

> **dvarsam said:**
> Nothing!
The module does NOT seem loaded?
Even more - your sound modules have not been installed! That's why modprobe says that it can not find *,ko files in lib/modules/.../sound directory.

So, my proposition is to get clean alsa-driver, alsa-lib, alsa-util sources and build them again. Untar alsa archives again or download them again if you have deleted them. Then repeat the usual steps (configure, make, make install), at each step look at program output - maybe there are some errors or warnings.
After 'make install' you should see /lib/modules/2.6.17-10-generic/kernel/sound/pci/snd-intel8x0m.ko file. If you do not see this file, this means that the compilation/build/installation has failed - in this case, there should have been error messages during configure/make/make install process.  

Then try again 'modprobe' manually (as I mentioned in the previous post) or try to reboot if it does not help. Again, look at 'modprobe' errors/warnings and 'lsmod | grep snd' output.

---

### Post by dvarsam on 2007-02-02
Thank you for your reply!

I made big improvement here!
I deleted previously extracted folders & re-extracted all packages from the start!
I bet that probably this was the error, because I noticed that "./configure" & "make" steps lasted longer compared to the previous attempts...
I did NOT get any errors or warnings, so that is good!
I then visited the path you suggested:

```
root@dimitris-desktop:/lib/modules/2.6.17-10-generic/kernel/sound/pci# ls
ac97     ca0106       echoaudio  ice1712   nm256    rme9652           vx222
ali5451  cs46xx       emu10k1    korg1212  pcxhr    [color=blue]snd-intel8x0m.ko[/color]  ymfpci
au88x0   cs5535audio  hda        mixart    riptide  trident
```

We have a successful result!
We have a "[color=blue]snd-intel8x0m.ko[/color]" file!!!

As you suggested, I then tried the "[color=blue]modprobe snd-intel8x0m[/color]" command to get this output:

```
root@dimitris-desktop:/lib/modules/2.6.17-10-generic/kernel/sound/pci# modprobe snd-intel8x0m
FATAL: Error inserting snd_intel8x0m (/lib/modules/2.6.17-10-generic/kernel/sound/pci/snd-intel8x0m.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I got a Fatal Error!
Should I restart instead the PC?

Thanks.

---

### Post by vicnov on 2007-02-02
> **dvarsam said:**
> I got a Fatal Error!
Should I restart instead the PC?
Yes, try to restart, it should help

---

### Post by dvarsam on 2007-02-02
I restarted the machine, but I can't see anything different...
On the Top Panel, the "Volume Control" has a Red "X" on Top of it.
During boot I didn't hear that Ubuntu boot audio coming out from the speakers.
BTW, inside the file "[color=blue]/etc/modprobe.d/alsa-base[/color]", I added/used the line "[color=blue]options snd-intel8x0m model=[/color][color=red]auto[/color]", as you suggested...
Shouldn't I use "[color=blue]model=[/color][color=red]ac97_clock[/color]" instead?
The parameter "auto" is NOT mentioned inside that "home/dimitris/Desktop/alsa-driver-1.0.14rc2/[color=blue]alsa-kernel/Documentation/ALSA-Configuration.txt[/color]" file...
What do you think?

Inside the above file, I also found this:
```
Module snd-intel8x0m
  --------------------

    Module for Intel ICH (i8x0) chipset MC97 modems.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7
			* SiS 7013 (SiS 735)
			* NVidia NForce, NForce2, NForce2s, NForce3
			* AMD AMD8111
			* ALi m5455

    [color=blue]ac97_clock[/color]	  - AC'97 codec clock base (0 = auto-detect)

    This module supports one card and autoprobe.

    Note: The default index value of this module is -2, i.e. the first
          slot is excluded.

    The power-management is supported.
```

Basically, the option "[color=blue]model=[/color][color=red]ac97_clock[/color]" is the only one offered...

Note: I just tried that - it did NOT help at all...

---

### Post by vicnov on 2007-02-02
As a last proposition,
try to configure alsa using 'alsaconf' program (run it from command-line), maybe it will find correct params.

But before this check that the module was loaded after the reboot:
lsmod | grep snd

If nothing helps, seems that a better way for you is to post to alsa-user mailing lists:
[http://www.alsa-project.org/mailing-lists.php](http://www.alsa-project.org/mailing-lists.php)

---

### Post by vicnov on 2007-02-02
Also, one more attempt - try to load the module with you previous settings:
options snd-intel8x0m index=-2

---

### Post by vicnov on 2007-02-02
**dvarsam**
Sorry for my helpless posts here - in fact, I have no experience with different sound cards...
I believe that somebody can help you, just wait a little or try to send to alsa-user mailing list,

Good luck! And do not kill your hard disk ;-)

---

### Post by dvarsam on 2007-02-02
[QUOTE=vicnov]
Sorry for my helpless posts here - in fact, I have no experience with different sound cards...
I believe that somebody can help you, just wait a little or try to send to alsa-user mailing list,
Good luck! And do not kill your hard disk ;-)[/QUOTE]

I want to thank you for all your help man!
You are a great man!
Listen, I do NOT want to "torture" anybody else, except myself...
I have already performed the Backup!
Everything is ready!
BTW - I have downloaded Feisty Fawn Herd 3!
Maybe this Format is worth it...
Besides, I will try the Feisty Herd 3 & tell you how it feels like.
I hope it is going to be a smooth install...

Again thank you all for the help you have provided!

P.S.> At least I got 1 of the 2 PCs worked out! ;)

---

### Post by vicnov on 2007-02-12
Currently, Tobin Davis (from ALSA Team) is working at the Conexant patch.
Good news: the patch is almost ready and (I hope) will be part of alsa-driver-1.0.14 (when it will be released).

As I know, Conexant has provided technical docs about their codecs. Codec names/models are now changed according to the Conexant documentation:

old name --> new name:

Conexant 5045 --> CX20549 (Venice)
Conexant 5047 --> Conexant CX20551 (Waikiki)

This new name will appear in the new driver version.

Currently the patch is being tested by volunteer testers. There are some problems with audio capture for "5045". For "5047" seems that everything is working now.

Until this release, use the instructions I posted earlier in this post. They work well for 5047 codec with 1.0.14 rc1/rc2 driver.

---

### Post by Jamie Lokier on 2007-02-15
This isn't a report about the mic, but it's related to the Conexant patch and 1.0.14 I think.

I'm running Ubuntu Feisty, and /proc/asound/version says 1.0.14rc1,
and I have a Conexant CXT5045 codec.  It's a laptop, Fujitsu-Siemens Amilo SI-1520.

With kernel 2.6.20-5, line-out works fine.  But since 2.6.20-6, it's stopped working.

I think that's about the time when the Conexant patches went in.

Output through the laptop speakers is fine, but when external speakers are plugged into line-out, sound switches to the external speakers for about 1/2 a second (the laptop speakers cut off), then both speakers are silent.  Unplugging the external speakers, and laptop speakers start playing sound again.

I can't say anything about the microphone; the internal one has never apparently worked, and I don't have an external one.

---

### Post by vicnov on 2007-02-16
**Jamie Lokier**
before the update to 2.6.20-6 (when the sound worked well), was it an "out-of-the-box" version of sound driver or a manually built from sources?

Is it possible to boot with the previous (2.6.20-5) kernel and check the sound?
Is "/proc/asound/version" the same for both kernels?

Seems that some Conexant patches were added in 1.0.14rc1, some will be added into the final 1.0.14.

---

### Post by Jamie Lokier on 2007-02-17
> **vicnov said:**
> 
before the update to 2.6.20-6 (when the sound worked well), was it an
"out-of-the-box" version of sound driver or a manually built from
sources?

It's the out-of-box version, whatever Synaptic/Apt installs with all the
Feisty repositories enabled.

> Is it possible to boot with the previous (2.6.20-5) kernel and
check the sound?
Is "/proc/asound/version" the same for both kernels?

Yes: /proc/asound/version reports 1.0.14rc1 with the 2.6.20-5 kernel,
the same as it reports with the 2.6.20-8 kernel.

Despite showing the same ALSA version in both kernels, the Conexant
support in 2.6.20-5 is different from the one in 2.6.20-8.

The controls shown in Gnome Volume Control are different, and the codec
name reported in /proc/asound/card0/codec#0 is different: "Conexant ID
5045" in 2.6.20-5, and "Conexant CXT5045" in 2.6.20-8.

Apart from line-out not working properly on my laptop, there's some
aesthetic weirdness too.  The Gnome Volume Control says there are two
sound devices, called "HDA Intel (ALSA Mixer)" and "Conexant ID 5045
(OSS Mixer)", which I find a little confusing, especially as the
latter's slider doesn't seem to have any effect.  The set of slider
controls shown for HDA Intel changed between kernels too.

The Gnome Sound Preferences offers these choices of sound device in
2.6.20-5: "Autodetect", "ALSA", "ESD" and "OSS", which makes sense.  But
in 2.6.20-8, it's "Autodetect", "Conexant Digital", "CONEXANT Analog",
(note different caps), "ALSA", "ESD", "OSS", which is confusing: Is ALSA
equivalent to one of the Conexant outputs, or both of them somehow?
Which should I use?  Will Autodetect (the Gnome default except for sound
capture) pick the best output?  Will it continue to use the best one if SPDIF is
plugged in or removed after Gnome starts?  For sound capture, Gnome's default is
ALSA not Autodetect; is that better than "CONEXANT Analog" somehow for
capture (there is no "Conexant Digital" for capture, naturally)?

> Seems that some Conexant patches were added in 1.0.14rc1, some
will be added into the final 1.0.14.

Seems that there are Conexant patches being changed without changing the
ALSA version in Ubuntu kernels.  I wouldn't mention it but the older one
works better than the newer one on my laptop, and the options which
appear in Gnome's apps seemed to make more sense with the older version.

Thanks for your attention.  Are you involved in reporting these bugs to ALSA upstream?

---

### Post by vicnov on 2007-02-18
**Jamie Lokier**
Seems that driver versions are different (despite that both show 1.0.14rc1, but codec name is different) - maybe some patches have been applied for the latest kernel. I would recommend to build the driver manually from 1.0.14rc1 (or rc2) sources from alsa-project.org.
Follow the instructions on the 2nd page of this post:
[http://ubuntuforums.org/showpost.php?p=1914583&postcount=16)](http://ubuntuforums.org/showpost.php?p=1914583&postcount=16))
but build and install alsa-driver only (do not download alsa-lib, alsa-utils; skip steps 3,4).
Also try different "model" values in the step 5 (this parameter defines which controls are available in alsamixer) - look at the documentation in
alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt
These instructions are for Conexant 5047, but the algorithm is the same for different cards/codecs, you just need to move around a little bit.

HDA Intel (ALSA Mixer) and Conexant ID 5045
(OSS Mixer).
This is not a problem, you have 2 options to work with audio devices - ALSA (new way) or OSS (old way, for compatibility with old applications). So just select HDA Intel (ALSA Mixer) in Gnome Volume Control.

Gnome Sound Preferences - I have never changed these settings. I also have a list of different choices as you, but all settings are defaults (Autodetect) excepting Capture (Conexant Analog in my case). I think you may use these defaults but if something does not work, you should check all posibilities, of course.

A better way is to test sound without gnome/kde at all - just use the following commands:
alsamixer (to set volume levels, turn on capture, etc)
arecord > ./myfile,wav (to capture sound)
aplay ./myfile.wav (to play sound).

So, to summarize what you can do:
1) backup your current sound drivers for 2.6.20-8
2) build and install alsa-driver from 1.0.14rc1 (or rc2)
3) play with different settings of "model"
4) play with different settings in alsamixer
5) post your feedback here about the results - as I mentioned several days ago, Conexant 5045 and 5047 drivers are being tested now, so this topic is actual!

---

### Post by vicnov on 2007-02-18
**Jamie Lokier**
I am not ALSA driver developer, but I take part in the testing (I have Conexant 5047 codec) together with other people. If you want to take part in this testing or ask questions directly to ALSA developers, just go to alsa-project.org mailing lists and find e-mail of Tobin Davis.

---

### Post by vicnov on 2007-02-18
I have selected ALSA in all Gnome Sound Preferences drop-down boxes, it works well as it worked with Autodetect.

---

### Post by Jamie Lokier on 2007-02-22
> **vicnov said:**
> **Jamie Lokier**
I would recommend to build the driver manually from 1.0.14rc1 (or rc2) sources from alsa-project.org.

1) backup your current sound drivers for 2.6.20-8
2) build and install alsa-driver from 1.0.14rc1 (or rc2)
3) play with different settings of "model"
4) play with different settings in alsamixer
5) post your feedback here about the results - as I mentioned several days ago, Conexant 5045 and 5047 drivers are being tested now, so this topic is actual!

Thanks.  I've done that now.  1.0.14rc1 doesn't compile with this kernel (2.6.20-8-generic), but 1.0.14rc2 does.  The problem is still present with ALSA's driver: no sound on external speakers, except for a brief moment.

"model=laptop" and no "model" option at all both do this.  "model=test" (for which I added a #define CONFIG_SND_DEBUG to patch_conexant.c) causes no sound to be heard on the laptop speakers either.

So ALSA's version 1.0.14rc2 is not working well on my laptop, while an older Ubuntu kernel does work.

---

### Post by Jamie Lokier on 2007-02-22
> **vicnov said:**
> I have selected ALSA in all Gnome Sound Preferences drop-down boxes, it works well as it worked with Autodetect.

Yeah, but what does it mean?  Did you try plugging in a digital cable and removing it while Gnome is running? :-)

---

### Post by vicnov on 2007-02-22
**Jamie Lokier**
I have not tried ALSA driver with kernels 2.6.20 (I have 2.6.17). As written in "alsa-driver-1.0.14rc2/SUPPORTED_KERNELS" file:
```
The alsa-drivers in this package are designed for the following kernels:

 - Vanilla 2.6.19 or earlier
 - Vanilla 2.4.31 or earlier
 - Vanilla 2.2.26 or earlier

It's not guaranteed that they work with any newer version than above
or modified kernels by distributors.
```

Do you have compilation errors (while building the alsa-driver)? Is there something like "unresolved symbols" or "can not resolve symbols" in "dmesg" output?

When you were building the driver, had you booted with 2.6.20 kernel or not? By default, the build script uses current (loaded) kernel. If necessary, you may change this behavior - look in "alsa-driver-1.0.14rc2/INSTALL" file.

Also, please check that your 2.6.20 kernel is built with snd-hda-intel as a module (and NOT inside kernel):
```
grep CONFIG_SND_HDA_INTEL /boot/config-`uname -r`
```
You should see:
```
CONFIG_SND_HDA_INTEL=m
```

One more idea for testing - you may download latest *daily snapshot* of alsa-driver and build/install it - maybe it supports your kernel. You can take a latest daily snapshot from here (or any mirror site):
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)

---

### Post by vicnov on 2007-02-22
> **Jamie Lokier said:**
> Yeah, but what does it mean?  Did you try plugging in a digital cable and removing it while Gnome is running? :-)

If you mean SPDIF cable - yes, the sound works with SPDIF cable while Gnome is running (I have connected the cable to my audio receiver with optical input, then removed the cable - the sound reappeared in the internal speaker).

---

### Post by Jamie Lokier on 2007-02-22
> **vicnov said:**
> If you mean SPDIF cable - yes, the sound works with SPDIF cable while Gnome is running (I have connected the cable to my audio receiver with optical input, then removed the cable - the sound reappeared in the internal speaker).

Even when you selected "CONEXANT Analog" in Gnome Sound Settings?  I was responding to your observation that those Conexant options seem to work the same as the "ALSA" option.  I don't have SPDIF to try it.

-- Jamie

---

### Post by Jamie Lokier on 2007-02-22
> **vicnov said:**
> **Jamie Lokier**
I have not tried ALSA driver with kernels 2.6.20 (I have 2.6.17). As written in "alsa-driver-1.0.14rc2/SUPPORTED_KERNELS" file:
```
The alsa-drivers in this package are designed for the following kernels:

 - Vanilla 2.6.19 or earlier
 - Vanilla 2.4.31 or earlier
 - Vanilla 2.2.26 or earlier

It's not guaranteed that they work with any newer version than above
or modified kernels by distributors.
```

Do you have compilation errors (while building the alsa-driver)? Is there something like "unresolved symbols" or "can not resolve symbols" in "dmesg" output?

I'm not sure why you think I had trouble compiling.  1.0.14rc2 compiled just fine with no errors, and installed and loaded fine too.  I checked the dates on the modules in /lib/modules/`uname -r`/kernel/sound to be sure I was loading the newly compiled modules.

> When you were building the driver, had you booted with 2.6.20 kernel or not? By default, the build script uses current (loaded) kernel. If necessary, you may change this behavior - look in "alsa-driver-1.0.14rc2/INSTALL" file.

That's right, I was running 2.6.20-8-generic when I compiled the modules.  They compiled and installed as expected in 2.6.20-8-generic's module directory.  Then I unloaded the modules which came with the kernel, and loaded the new ones.

> One more idea for testing - you may download latest *daily snapshot* of alsa-driver and build/install it - maybe it supports your kernel. You can take a latest daily snapshot from here (or any mirror site):
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)

Again, I'm not sure why you think I had trouble compiling it.  I compiled, installed and loaded the modules with no problem, except that the sound on external speaker didn't work, the same as the modules that came with the kernel.

I've now submitted a bug report to [email]alsa-users@lists.sourceforge.net[/email], and I hope someone will notice!  Thanks for your help.

---

### Post by pixeldotz on 2007-02-28
i have an hda intel with ctx5045.

i compiled alsa 1.0.14rc1 i think it was and the audio works fine, even when headphones are connected. mic still doesn't work so now i'm trying the newest snapshot from yesterday 2.27 and am getting this error from the console.


```
make[1]: *** [_module_/home/pixeldotz/alsa-driver-hg20070227] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [compile] Error 2
```


anyone understand what i'm doing wrong?

---

### Post by vicnov on 2007-02-28
**pixeldotz**,
seems that an error is somewhere before this message - try to redirect output to a file and see whether there is some error:

if you run make, try this:
```
make > output.txt 2>&1
```

---

### Post by pixeldotz on 2007-02-28
sorry for the long post :( but here are the contents from output.txt

thanks for the help. hopefully this won't all be for nothing and maybe this alsa will get my mic working.

```
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #8 succeeded at 535 with fuzz 2.
copying file alsa-kernel/core/pcm.c
patching file pcm.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #3 succeeded at 1601 (offset -7 lines).
Hunk #4 succeeded at 2835 (offset -7 lines).
Hunk #5 succeeded at 2855 (offset -7 lines).
Hunk #6 succeeded at 2885 (offset -7 lines).
Hunk #7 succeeded at 2912 (offset -7 lines).
Hunk #8 succeeded at 2928 (offset -7 lines).
Hunk #9 succeeded at 2958 (offset -7 lines).
Hunk #10 succeeded at 3044 (offset -7 lines).
Hunk #11 succeeded at 3063 (offset -7 lines).
Hunk #12 succeeded at 3082 (offset -7 lines).
Hunk #13 succeeded at 3115 (offset -7 lines).
Hunk #14 succeeded at 3148 (offset -7 lines).
Hunk #15 succeeded at 3181 (offset -7 lines).
Hunk #16 succeeded at 3210 (offset -7 lines).
Hunk #17 succeeded at 3231 (offset -7 lines).
Hunk #18 succeeded at 3249 (offset -7 lines).
Hunk #19 succeeded at 3269 (offset -7 lines).
Hunk #20 succeeded at 3281 (offset -7 lines).
Hunk #21 succeeded at 3313 (offset -7 lines).
Hunk #22 succeeded at 3379 (offset -7 lines).
Hunk #23 succeeded at 3408 (offset -7 lines).
Hunk #24 succeeded at 3449 (offset -7 lines).
Hunk #25 succeeded at 3599 (offset -7 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1389 (offset 172 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 307 (offset 4 lines).
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 229 (offset 6 lines).
Hunk #3 succeeded at 255 with fuzz 2 (offset 6 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1290 (offset 23 lines).
Hunk #2 succeeded at 1374 with fuzz 2 (offset 24 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #4 succeeded at 181 with fuzz 2.
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 986 with fuzz 1 (offset -9 lines).
Hunk #2 succeeded at 1895 (offset 104 lines).
Hunk #3 succeeded at 1940 with fuzz 2 (offset 95 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 604 (offset -5 lines).
Hunk #12 succeeded at 693 (offset -5 lines).
Hunk #13 succeeded at 708 (offset -5 lines).
Hunk #14 succeeded at 742 (offset -5 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore/ioctl32'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore/ioctl32'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #1 succeeded at 379 with fuzz 1 (offset 2 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2557 (offset 31 lines).
Hunk #2 succeeded at 2608 (offset 31 lines).
Hunk #3 succeeded at 2731 (offset 31 lines).
Hunk #4 succeeded at 2914 with fuzz 2 (offset 29 lines).
Hunk #5 succeeded at 3041 (offset 27 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore/oss'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #2 succeeded at 2206 (offset 65 lines).
Hunk #3 succeeded at 2554 with fuzz 2 (offset 85 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq/instr'
make[4]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq/instr'
make[4]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #1 succeeded at 189 (offset 3 lines).
Hunk #2 succeeded at 223 with fuzz 2 (offset 3 lines).
Hunk #3 succeeded at 326 (offset -8 lines).
make[4]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq/oss'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore/seq'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/acore'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/i2c'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/i2c/other'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/i2c/other'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/i2c'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #1 succeeded at 30 (offset 2 lines).
Hunk #2 FAILED at 46.
Hunk #3 FAILED at 64.
Hunk #4 FAILED at 149.
Hunk #5 succeeded at 300 (offset 53 lines).
3 out of 5 hunks FAILED -- saving rejects to file mpu401.c.rej
make[3]: *** [mpu401.c] Error 1
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/mpu401'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/opl3'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/opl4'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/opl4'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/pcsp'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/pcsp'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/vx'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers/vx'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/drivers'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/ad1816a'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/ad1816a'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/ad1848'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/ad1848'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/cs423x'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/cs423x'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/es1688'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/es1688'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/gus'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/gus'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/msnd'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/msnd'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/opti9xx'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/opti9xx'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #1 succeeded at 717 (offset -2 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/sb'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
Hunk #2 succeeded at 262 with fuzz 2 (offset -2 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa/wavefront'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/isa'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/synth'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/synth/emux'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/synth/emux'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/synth'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 817 (offset 7 lines).
Hunk #2 succeeded at 956 (offset 8 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #2 succeeded at 704 (offset 3 lines).
Hunk #3 succeeded at 715 (offset 3 lines).
Hunk #4 succeeded at 3072 (offset 61 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #1 succeeded at 2745 with fuzz 2 (offset -2 lines).
Hunk #2 succeeded at 2762 with fuzz 2 (offset -2 lines).
Hunk #3 succeeded at 2939 (offset -2 lines).
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ac97'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ali5451'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ali5451'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/asihpi'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/asihpi'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/au88x0'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/au88x0'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ca0106'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ca0106'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/cs46xx'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/cs46xx'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/cs5535audio'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/cs5535audio'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1924 (offset -2 lines).
Hunk #2 succeeded at 1987 (offset -2 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/echoaudio'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #2 succeeded at 649 (offset 37 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/emu10k1'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/hda'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ice1712'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ice1712'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #1 succeeded at 2340 with fuzz 1 (offset -2 lines).
Hunk #2 succeeded at 2506 (offset -2 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/korg1212'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/mixart'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/mixart'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/nm256'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/nm256'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/pcxhr'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/pcxhr'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/pdplus'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/pdplus'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1278 (offset 9 lines).
Hunk #2 succeeded at 2235 (offset 9 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/riptide'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/rme9652'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/rme9652'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/trident'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/trident'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/vx222'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/vx222'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2035 (offset 33 lines).
Hunk #3 succeeded at 2062 (offset 33 lines).
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci/ymfpci'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pci'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/codecs'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/codecs'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/core'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/core'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/fabrics'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/fabrics'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/soundbus'
make[4]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa/soundbus'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/aoa'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/soc'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/soc/at91'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/soc/at91'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/soc/codecs'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/soc/codecs'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/soc/pxa'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/soc/pxa'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/soc/s3c24xx'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/soc/s3c24xx'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/soc'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 660 with fuzz 2 (offset -9 lines).
Hunk #4 succeeded at 687 with fuzz 2 (offset -9 lines).
Hunk #5 succeeded at 768 (offset -9 lines).
Hunk #6 succeeded at 783 (offset -9 lines).
Hunk #7 succeeded at 1161 (offset -9 lines).
Hunk #8 succeeded at 2076 (offset -3 lines).
Hunk #9 succeeded at 2095 (offset -3 lines).
Hunk #10 succeeded at 2112 (offset -3 lines).
Hunk #11 succeeded at 2672 (offset 10 lines).
Hunk #12 succeeded at 2744 (offset 10 lines).
Hunk #13 succeeded at 3028 (offset 10 lines).
Hunk #14 succeeded at 3099 (offset 10 lines).
Hunk #15 succeeded at 3220 (offset 62 lines).
Hunk #16 succeeded at 3238 (offset 62 lines).
Hunk #17 succeeded at 3252 (offset 62 lines).
Hunk #18 succeeded at 3265 (offset 62 lines).
Hunk #19 succeeded at 3463 (offset 64 lines).
Hunk #20 succeeded at 3554 (offset 64 lines).
Hunk #21 succeeded at 3691 (offset 63 lines).
Hunk #22 succeeded at 3712 (offset 63 lines).
Hunk #23 succeeded at 3733 (offset 63 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #3 succeeded at 1725 (offset -1 lines).
Hunk #4 succeeded at 1774 (offset -1 lines).
Hunk #5 succeeded at 1795 (offset -1 lines).
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #3 succeeded at 63 with fuzz 2.
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/usb/usx2y'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/usb'
make[2]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia/vx'
make[3]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia/vx'
make[2]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227/pcmcia'
make[1]: Leaving directory `/home/pixeldotz/alsa-driver-hg20070227'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/pixeldotz/alsa-driver-hg20070227  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/memalloc.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/sgbuf.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/memory_wrapper.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm_native.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm_lib.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm_timer.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm_misc.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/pcm_memory.o
  CC [M]  /home/pixeldotz/alsa-driver-hg20070227/acore/rtctimer.o
In file included from /home/pixeldotz/alsa-driver-hg20070227/include/linux/log2.h:1,
                 from /home/pixeldotz/alsa-driver-hg20070227/acore/../alsa-kernel/core/rtctimer.c:27,
                 from /home/pixeldotz/alsa-driver-hg20070227/acore/rtctimer.c:1:
/home/pixeldotz/alsa-driver-hg20070227/include/log2_compat.h:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_power_of_2’
In file included from /home/pixeldotz/alsa-driver-hg20070227/acore/rtctimer.c:1:
/home/pixeldotz/alsa-driver-hg20070227/acore/../alsa-kernel/core/rtctimer.c: In function ‘rtctimer_init’:
/home/pixeldotz/alsa-driver-hg20070227/acore/../alsa-kernel/core/rtctimer.c:133: warning: implicit declaration of function ‘is_power_of_2’
make[3]: *** [/home/pixeldotz/alsa-driver-hg20070227/acore/rtctimer.o] Error 1
make[2]: *** [/home/pixeldotz/alsa-driver-hg20070227/acore] Error 2
make[1]: *** [_module_/home/pixeldotz/alsa-driver-hg20070227] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [compile] Error 2

```

---

### Post by vicnov on 2007-03-01
**pixeldotz**
not sure, but I think that something is wrong in this daily build because:
[LIST]
[*]I see errors during the patching of some source files ("Hunk failed" messages)
[*]compilation errors in the end (but this may be because of the patching errors)
[/LIST]

Have you applied some patches manually (using "patch' command) ? Maybe, this daily build already contains the patch your are trying to apply, or maybe your patch is incompatible with this new daily build.

Maybe, this is just a problem in the daily build itself - try a new daily build (today's version) and see whether it helps.

---

### Post by pixeldotz on 2007-03-01
i haven't applied any patches. i'll try todays build maybe i can get that working when i get home.

i'll post my results in a few hours :)

thanks for the help.

---

### Post by pixeldotz on 2007-03-01
stupid question....

every CVS folder on the ftps contain an empty tar file. how do i pull todays CVS?

---

### Post by vicnov on 2007-03-02
> **pixeldotz said:**
> every CVS folder on the ftps contain an empty tar file. how do i pull todays CVS?
Where do you get daily builds from?

---

### Post by pixeldotz on 2007-03-02
i got the 2.27.07 build from an ftp.suse site. i don't have the exact site address with me right now.

i thought i could get the cvs from the main alsa primary ftp.

[ftp://ftp.alsa-project.org/pub/](ftp://ftp.alsa-project.org/pub/)

but all the cvs folders are empty and i don't know the info (i use a cvs client usually) to pull the source and compile it myself.

particularly this one
2007-03-02.tar.bz2
which is todays cvs.

---

### Post by vicnov on 2007-03-02
Sorry, I am not an ALSA developer, so I do know nothing about their CVS and daily builds in fact ;-) But I built several times from daily builds taken on suse ftp.

Daily builds (and especially CVS sources) may contain errors - if you are developer, you know this.
I would recommend to wait for 1.0.14rc3 which will be publicly available in several day - next week maybe.

---

### Post by vicnov on 2007-03-02
**pixeldotz**
if you have time and ready to test a new driver - please look for Tobin Davis e-mail address in alsa-mailing lists and send him a letter. As I know he was going to work on Conexant 5045 sound cards this week-end.

---

### Post by pixeldotz on 2007-03-02
i have plenty of time :)

thanks for the suggestion though, i'll go and look for his e-mail. thanks for the help.

---

### Post by dejitarob on 2007-03-13
I recently got my microphone working on an Asus Z70v laptop with an Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller. I just had to change a few settings that were not really intuitive. See [http://ubuntuforums.org/showthread.php?p=1720522#post1720522]("http://ubuntuforums.org/showthread.php?p=1720522&highlight=Z70V#post1720522")

---

### Post by vignesh on 2007-04-22
Hi
    I use Feisty Fawn.. I have the foll audio card...

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
$ cat /proc/asound/card0/codec#2 | grep -i codec
Codec: SigmaTel STAC9227

Any idea how to get the mic working ?

---

### Post by mexlinux on 2007-04-22
Althought it was possible for me to solve this in Edgy, via sevearal workarounds (which now I have to found again).....
It's still present in Feisty!

---

### Post by jjalocha on 2007-04-22
I got a SigmaTel STAC92xx working simply with amixer. See this thread (with screenshots):
[http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)

---

### Post by Flavian on 2007-04-23
This is what I have:
flavian@octavius:~$ lspci | grep -i audio
**00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)**
flavian@octavius:~$ cat /proc/asound/card0/codec#0 | grep -i codec
**Codec: Generic 163c Si3054**

I tried compiling the codec like described but the weird thing is that it does not seem to work!
I rebooted and alsadriver is still the old 1.0.13 version that comes with feisty! How come?
I did everything like it was explained, only the last utils package did not work. Since that does not effect the drivers nor the mic I just left it.
But why did the alsa driver not update? Did I forget something?

Thanks in advance!
Flo

---

### Post by Flavian on 2007-04-29
Help, no one?

---

### Post by Flavian on 2007-05-03
:(

---

### Post by icechen1 on 2007-05-05
I have this probelm too(i have HDA Intel)

---

### Post by euchrid on 2007-06-07
Don't know if this helps, but I managed to successfully update my Alsa drivers and got everything working. I put all the information in this post: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

There seems to be a lot of people with similar problems. This needs fixing in the next update!

---

