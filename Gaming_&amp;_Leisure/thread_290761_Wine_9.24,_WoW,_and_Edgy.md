---
title: "Wine 9.24, WoW, and Edgy"
date: 2006-11-01
forum: Gaming &amp; Leisure
---

### Post by reiki on 2006-11-01
Can I get someone to test this? I'm at work and can't do it here.
This is to get Wine 0.9.24 patched and running on Ubuntu 6.10 Edgy so that you can play WoW in openGL mode on a machine with an nVidia card. The procedure is outlined already on:
[https://help.ubuntu.com/community/BuildingWineFromSource](https://help.ubuntu.com/community/BuildingWineFromSource)
but I have changed the names appropriately for Edgy and given links to patches. 

Make sure you have these repositories:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

(and then apt-get update of course)

sudo apt-get build-dep wine 
(when I did that I think it fetched 178 packages... hehehe)
sudo apt-get install fakeroot

mkdir wine-0.9.21
cd wine-0.9.21
apt-get source wine

go into the directory with the sources:
cd wine-0.9.24~winehq0~ubuntu~6.10 (adjust the directory name if I don't have it right, but you know where you should be. IN the source directory!)

Apply the nvidia flicker patch (This assumes you have an nVidia graphics card!). 
You can get the patch by following the link from here (scroll down a little... you'll see the link to it):
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

patch -p0 <  wow_patch_nvidia_flicker_fix_0.9.24.diff

If you don't have an nVidia card, skip that step and continue...

My assumption here is that if we've done the apt-get build-dep wine, we should have whatever wine needs. I will also assume you know to apt-get install build-essentials if you haven't already done so.

ok now ...
dpkg-buildpackage -rfakeroot -uc -b

quoting from [https://help.ubuntu.com/community/BuildingWineFromSource](https://help.ubuntu.com/community/BuildingWineFromSource) :

The build will take a LONG time, even with a fast machine. An hour or so would be average on a 2 GHz CPU with 1 GB of Ram, so go have a sandwich.

The build process, once it's complete, will create a .deb in the parent directory. This is your new Wine package.

First remove the old Wine package if you have one installed.
sudo dpkg --purge wine

And now install your newly created package.
sudo dpkg -i wine_0.9.24~winehq0~ubuntu~6.10-1_i386.deb

I am NOT sure of the exact name of the package file because I am at work and have not done this yet. So why am I asking someone else to do it first? Well because first of all I think it's going to work! It's also easier (for some) that compiling and probably a little less scary. We are finding that the dpkg-buildpackage procedure AUTOMATICALLY sets certain flags. Some of which you may have already read about (like CFLAG="-fno-stack-protector"), but there's another one observed when running dpkg-buildpackage. For anyone interested it is:

CFLAG="-fno-stack-protector -O2" (that's a letter O not a number)

But using the dpkg-buildpackage you don't have to set any flags as it's all done. Try it please and let us know if it works and I'll check back here after I get home and have dinner

---

### Post by Garyu on 2006-11-01
Nice. I tried building this and it works great. Only thing is that sound is a bit sparky. I'll play around with SoundBufferSize option and see if anything changes. 

My hardware is:
Motherboard: MSI K9N NEO-F (nForce 550, AM2)
CPU: AMD Athlon 64 X2 4200+ 2.2 GHz socket AM2
Graphics: Gainward GeForce 7600GT 256MB 1.4ns DDR3 PCI-Express
RAM: Corsair Value S, PC5300 DDR2, 1024MB

I started the compile and went for a snack. Checked back 32 minutes later and everything was done, so all I know is it took less than half an hour to compile everything.

Installed the .deb and copied the WoW-files and ran the game with "wine WoW.exe" (if you edit the Config.wtf file and add **SET gxApi "OpenGL" **you don't have to use the "-opengl" switch when you start it).

Thank you for a good guide. If anyone want to download the .deb I compiled, you can find the adress below. 8) 
[http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz](http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz)

PS.
I followed [this HowTo]("http://www.ubuntuforums.org/showthread.php?t=243336") on a 64-bit install of Edgy (same system, different partition), and it worked very well too. There I never had any kind of sound issues with crackling/sparkle that I did now (probably easy to fix the sound issue though - I haven't even had time to try yet). But this is an older version of Wine. Still, if you don't want to compile, it is a very good HowTo.

---

### Post by reiki on 2006-11-01
OK I have additional information. :)
The steps I outlined above DO work and so does this:

Find someone who has compiled wine 0.9.24 with the nvidia patch (if you use nVidia graphics card) Or someone who has followed the above procedure to have apt build the package. ALL YOU NEED is one file from them.

/usr/lib/wine/winex11.drv.so

I installed using apt-get install wine from the winehq repository for edgy. That got me wine 0.9.24. Then I got just that one file ( winex11.drv.so ) from a patched and properly compiled wine. Swapped it out with mine and VOILA! I'm running WoW in Wine on Edgy. 

If you swap out the file and WoW still errors out, you might have to rename your .wine directory (in your /home/your-username ) and then run winecfg and let wine create a new .wine directory. Then copy JUST the contents of your old Program Files directory into the new .wine directory's drive_c/Program Files directory.

If you run winecfg and it complains about not being able to create mcop something or other, do this:

mkdir /tmp/ksocket-username (substitute your username on the machine in place of "username" in the example. no quotes, but the hyphen is necessary). Then rerun winecfg and make sure that under the audio tab, ALSA is checked.

Done deal
Start WoW

---

### Post by Ferrat on 2006-11-02
This sounds great, is there any preformance boost with this vs dapper and 0.9.23 if you've had that before, would be great to know.. ??

---

### Post by reiki on 2006-11-02
Ferrat-

In my Dapper install it's using wine version 0.9.17. This was a prepatched wine version that I found on the web when I was trying to get WoW working in wine originally many months ago. 

On my Edgy installation with wine 0.9.24 I'm not sure if there's a performance increase as I really haven't had time to thoroughly wring it out. I can tell you that I have All Shaders enable box checked in WoW with Death Effects off. But I have full screen glow on and many of teh graphics settings for textures and stuff set to High. I'm getting about 30 to 35 (ish) FPS but I think I can tweak that up a bit. I have a 512meg GeForce card and 2 gigs of ram in this machine so I expect a little better performance.

---

### Post by reiki on 2006-11-02
Update:
If you want wine-0.9.24, you can install using apt-get install wine with the winehq repositories as shown in my first post.

Then you can simply go to:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
where Nick Law has made the patched binary avaiable. One file, about a meg and a half I think ( winex11.drv.so ). It's properly compiled for Edgy and you can simply replace the original file with the patched one. You'll see the instructions. I'm trying to provide information only from reputable sources here which is why I am not offering any files myself. 

Many thanks to Nick Law, the maintainer at appdb.winehq for WoW under Wine and to AllanJ and Kevin Bridges. I simply helped with testing. These guys deserve the credit for getting it straightened out.

---

### Post by myname on 2006-11-03
Has anyone had any luck with ATI cards, WoW, Wine 0.9.24 and Edgy?

I have an ATI X1600 with 512 megs of RAM, and with a default install of Edgy, installed the ATI Drivers by following the information here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

Then installing Wine via Synaptec.  

WoW launches, but as soon as I go in, I start getting graphic anomolies and the system will lock up in about 10 seconds.

If anyone has any information on this, that would be great. If I am doing something wrong during the installation of one or all of the software above, please let me know.  

Thanx.

--Kevin

---

### Post by Zargoon on 2006-11-03
When I try to create the debian I get this:

usr/bin/ld: /usr/lib/libsicuuc.a(ubidi.ao): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libsicuuc.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
winegcc: x86_64-linux-gnu-gcc failed.
make[3]: *** [gdi32.dll.so] Error 2
make[3]: Leaving directory `/home/zargoon/Apps/Wine/wine-0.9.21/wine-0.9.24~winehq0~ubuntu~6.10/dlls/gdi32'
make[2]: *** [gdi32] Error 2
make[2]: Leaving directory `/home/zargoon/Apps/Wine/wine-0.9.21/wine-0.9.24~winehq0~ubuntu~6.10/dlls'
make[1]: *** [dlls] Error 2
make[1]: Leaving directory `/home/zargoon/Apps/Wine/wine-0.9.21/wine-0.9.24~winehq0~ubuntu~6.10'
make: *** [build-stamp] Error 2

Any ideas?

---

### Post by reiki on 2006-11-04
Ferrat-

You asked about performance.
Using same character for reference in the same location in game.

Dapper using Wine 0.9.17 and nvidia driver 8776
FPS 16 to 18 
in areas where you are not outside and things are closer, like in buildings or in cities, FPS up to about 30 - 32

Edgy using wine 0.9.24 and nvidia driver 8776
FPS 36 to 40
in areas where you are not outside and things are closer, like in buildings or in cities, FPS up to about 75 - 78

I also notice (and this is a bit subjective on my part) that the game LOOKS much better on Edgy. All in-game settings are the same between the 2 installations and the config.wtf is the same for both. Pretty amazing difference. I didn't expect it would be that different. Also both Dapper and Edgy are using smp-enabled linux images (Dapper using an i686 image and Edgy using generic)

---

### Post by Ferrat on 2006-11-04
> **reiki said:**
> Ferrat-

You asked about performance.
Using same character for reference in the same location in game.

Dapper using Wine 0.9.17 and nvidia driver 8776
FPS 16 to 18 
in areas where you are not outside and things are closer, like in buildings or in cities, FPS up to about 30 - 32

Edgy using wine 0.9.24 and nvidia driver 8776
FPS 36 to 40
in areas where you are not outside and things are closer, like in buildings or in cities, FPS up to about 75 - 78

I also notice (and this is a bit subjective on my part) that the game LOOKS much better on Edgy. All in-game settings are the same between the 2 installations and the config.wtf is the same for both. Pretty amazing difference. I didn't expect it would be that different. Also both Dapper and Edgy are using smp-enabled linux images (Dapper using an i686 image and Edgy using generic)

Yeah got it running on edgy aswell with 0.9.24 and my ATi card, I've gained some preformance aswell but as you said it looks better in someway and what I noticed is that the flow is better even when the FPS goes down, the choppyness that that can create is almost totalt gone..:KS

---

### Post by spydirweb on 2006-11-06
I used this, and set it up for opengl and ALSA like a few others mentioned.  Thank god, it runs great and gets me off transgaming's cedega!  The only problem I have is I use numlock to autorun, and the numpad 0/insert button to jump (left handed mouse user).  When I hit numlock it switches the function of the key, and for some reason numpad_0 just doesn't register with wine.  I've looked and it seems to be a general wine error...  I'm gonna keep looking for a fix.  until then I just switched my autorun key.  if i get used to it quick enough forget fixing it ;-)

---

### Post by kise on 2006-11-08
hmm i cant start the game..

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c500000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c500000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

what should i do..

---

### Post by myname on 2006-11-08
Did you do a winecfg before you started WoW?

What type of hardware are you running?

---

### Post by SadaraX on 2006-11-09
Hello. I am getting this compiler error. But I have gcc and g++ both installed. 

> 
gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)


> 
g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)


My system was Dapper before, but I did an apt-get upade && apt-get dist-upgrade today, and everything seems alright. Here is the console output. From what I can tell, it is trying to call gcc with the '-V' argument when it only accepts the '-v' argument. Can anyone help me?

```

User$: dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.24~winehq0~ubuntu~6.10-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/rayn/wine-0.9.21/wine-0.9.24~winehq0~ubuntu~6.10'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/rayn/wine-0.9.21/wine-0.9.24~winehq0~ubuntu~6.10'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2 -fno-stack-protector" ./configure --host=i486-linux-gnu --build=i486-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... i486-pc-linux-gnu
checking host system type... i486-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for i486-linux-gnu-gcc... i486-linux-gnu-gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77

```

---

### Post by alynx on 2006-11-09
Any thoughts on whats gonna happen with wow and wine when The burning crusade comes out ?

---

### Post by reiki on 2006-11-09
> **SadaraX said:**
> Hello. I am getting this compiler error. But I have gcc and g++ both installed. 

My system was Dapper before, but I did an apt-get upade && apt-get dist-upgrade today, and everything seems alright. Here is the console output. From what I can tell, it is trying to call gcc with the '-V' argument when it only accepts the '-v' argument. Can anyone help me?



If this is on Edgy, get gcc version 4.1. Then add winehq repositories so you can get wine 0.9.24. 

Then apt-get build-dep wine

Then try to build your package again.

---

### Post by reiki on 2006-11-09
> **alynx said:**
> Any thoughts on whats gonna happen with wow and wine when The burning crusade comes out ?

We shall PLAY it! :)

---

### Post by souled on 2006-11-09
> **Garyu said:**
> 
Installed the .deb and copied the WoW-files and ran the game with "wine WoW.exe" (if you edit the Config.wtf file and add **SET gxApi "OpenGL" **you don't have to use the "-opengl" switch when you start it).

Thank you for a good guide. If anyone want to download the .deb I compiled, you can find the adress below. 8) 
[http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz](http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz)



Thanks for the deb. I tried compiling it myself, but I got some error when I tried to run it with opengl.

One question, I'm running two displays with Twinview at 1440x900 each. When I try to change the resolution in Config.wtf to 1440x900, the resolution ends up being 2880x900, but it only runs in one screen. This causes the game to be "squished." How can I run it at 1440x900 on one screen or 2880x900 on two screens? Is it possible to run it over two screens in my situation?

---

### Post by ImaMadGoat on 2006-11-12
Anyone try this with the 9XXX drivers for Nvidia?

---

