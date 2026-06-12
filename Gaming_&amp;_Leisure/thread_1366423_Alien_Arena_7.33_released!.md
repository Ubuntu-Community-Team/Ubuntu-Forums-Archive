---
title: "Alien Arena 7.33 released!"
date: 2009-12-28
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2009-12-28
**V**ersion 7.33 of Alien Arena has been released today!

The new edition of this open sourced, freeware FPS has been updated with a variety of new features, as well as some important bugfixes and optimizations, and last but not least, a brand new level in which to get your frag on!

Some of the new features include: 

[list]
[*]In-game IRC client 
[*]Player rankings in server browser 
[*]Skill level matchmaker on server info 
[*]Vastly improved anti-lag code 
[*]Headshots 
[*]Optimizations and bugfixes 
[*]Various improved graphic effects 
[*]New level, dm-deathray
[/list]
Alien Arena 7.33

[[img]http://icculus.org/alienarena/rpa/mediathumbs/deathray1_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/deathray1.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/deathray2_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/deathray2.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_21_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_21.jpg)

For a complete changelog - [http://icculus.org/alienarena/changelogs/7.33.txt](http://icculus.org/alienarena/changelogs/7.33.txt)

For more information, new media, and to download the game visit [http://red.planetarena.org](http://red.planetarena.org)

---

### Post by J.K.Makowka on 2009-12-28
Doesn't start on my Ubuntu 9.10

Last console output is the following:

```

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy

```

---

### Post by Irritant on 2009-12-28
That's an OpenAL bug, to fix - 

In your home directory

create:

~/.alsoftrc

and add the entry:
[general] 
drivers = oss

---

### Post by Melcar on 2009-12-28
The download links still point me to the 7.32 release.

---

### Post by Irritant on 2009-12-28
> **Melcar said:**
> The download links still point me to the 7.32 release.

You sure?  I'm looking at [http://icculus.org/alienarena/rpa/aquire.html](http://icculus.org/alienarena/rpa/aquire.html) right now, it's definitely 7.33

---

### Post by Melcar on 2009-12-28
Got it now.  Digging the new level and music =D>.

---

### Post by what, what? on 2009-12-28
Can anybody tell me how to install this?

---

### Post by MaxIBoy on 2009-12-28
Just grab the dependencies. You are likely to have most of these already, and this includes some extra stuff in case you end up needing to compile it.
```
[SIZE=2][FONT=Courier New][SIZE=2]sudo apt-get install build-essential comerr-dev gettext html2text libaa1-dev libalut0 libasound2-dev libaudio-dev libaudio2 libaudiofile-dev libcaca-dev libcurl4-gnutls-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev libidn11-dev libjpeg62-dev libkadm55 libkrb5-dev libldap2-dev libopenal1\|openal-soft libopenal-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev sharutils tofrodos x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev libvorbis\|libvorbis0a libvorbis-dev xtrans-dev zlib1g-dev[/SIZE][/FONT][/SIZE]
``` 

You should then just be able to unzip the game and run the "crx" file directly. On 64 bit Linux you need to compile it first, and if you have any issues then compiling it can often help even on 32 bit.


Alternately, I think the PlayDeb people are pretty good about getting their stuff up-to-date, expect to see AA 7.33 in the PlayDeb repos soon.

---

### Post by Melcar on 2009-12-28
If you're running a 32bit system, just download the the zip file, uncompress it, and run the *crx* binary.  You may need to perform the openal workaround explained in this thread by Irritant.
If you're running a 64bit system, the best and easiest way is to recompile the game.  Install dependencies:

```
sudo apt-get install build-essential subversion libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl-mixer1.2-dev libcurl4-openssl-dev libxxf86dga-dev libxxf86vm-dev libopenal-dev

```

Go inside the source subdirectory inside the **Alien Arena** folder, open a terminal in that location, and make:

```
make
```

Once it's finished (with no errors) your new binaries will be inside the **release** subfolder (crx, crded, game.so).  Move *crx* and crded to the main **Alien Arena** folder (overwrite the originals) and *game.so* to the **arena** folder (overwrite the original).  Now you can just run the *crx* binary like normal.  Remember to perform the openal workaround as well.

---

### Post by MaxIBoy on 2009-12-28
You can do **make install** after **make** to move the binaries.

Also, you don't need subversion unless you're going to [checkout the game from SVN](http://alienarena.wikia.com/wiki/SVN) (perfectly valid way to obtain it.)

---

### Post by J.K.Makowka on 2009-12-28
> **what, what? said:**
> Can anybody tell me how to install this?

Simply unpack the game and start crx

@Irritant:
Thanks that fixed it, pretty nice update! Somehow it runs a lot slower if you enable normalmaps though :( (unusually high performance hit).

---

### Post by Irritant on 2009-12-28
> **J.K.Makowka said:**
> Thanks that fixed it, pretty nice update! Somehow it runs a lot slower if you enable normalmaps though :( (unusually high performance hit). Thanks! That'll depend alot on your GPU and how well your drivers support GLSL. It's gonna be a hit regardless though, it's like the difference between Q3 and Q4 as far as how it's rendering things.

---

### Post by what, what? on 2009-12-28
> **MaxIBoy said:**
> Just grab the dependencies. You are likely to have most of these already, and this includes some extra stuff in case you end up needing to compile it.
[code]


Alternately, I think the PlayDeb people are pretty good about getting their stuff up-to-date, expect to see AA 7.33 in the PlayDeb repos soon.

I checked playdeb, they mustve removed it and a few games for some reason.

---

### Post by what, what? on 2009-12-28
> **Melcar said:**
> If you're running a 32bit system, just download the the zip file, uncompress it, and run the *crx* binary.  You may need to perform the openal workaround explained in this thread by Irritant.
If you're running a 64bit system, the best and easiest way is to recompile the game.  Install dependencies:

```
sudo apt-get install build-essential subversion libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl-mixer1.2-dev libcurl4-openssl-dev libxxf86dga-dev libxxf86vm-dev libopenal-dev

```Go inside the source subdirectory inside the **Alien Arena** folder, open a terminal in that location, and make:

```
make
```Once it's finished (with no errors) your new binaries will be inside the **release** subfolder (crx, crded, game.so).  Move *crx* and crded to the main **Alien Arena** folder (overwrite the originals) and *game.so* to the **arena** folder (overwrite the original).  Now you can just run the *crx* binary like normal.  Remember to perform the openal workaround as well.

how do i run the crx and uncompress the zip? i'm afraid my simpleton mind cant comprehend that.

---

### Post by MaxIBoy on 2009-12-28
> **what, what? said:**
> how do i run the crx and uncompress the zip? i'm afraid my simpleton mind cant comprehend that.
Go to the download page of the game: [http://icculus.org/alienarena/rpa/aquire.html](http://icculus.org/alienarena/rpa/aquire.html)

Download the Linux version. It's a .zip file. Right click it, select "extract here" (assuming you use Ubuntu and not K/Xubuntu,) and it will create a folder. Move that folder directly to your home folder, go inside it, and run the "crx" file.

---

### Post by what, what? on 2009-12-28
> **MaxIBoy said:**
> Go to the download page of the game: [http://icculus.org/alienarena/rpa/aquire.html](http://icculus.org/alienarena/rpa/aquire.html)

Download the Linux version. It's a .zip file. Right click it, select "extract here" (assuming you use Ubuntu and not K/Xubuntu,) and it will create a folder. Move that folder directly to your home folder, go inside it, and run the "crx" file.

i tried to run it but it does nothing

---

### Post by MaxIBoy on 2009-12-28
You probably don't have all the dependencies installed.

Copy and paste the following command into a terminal, hit enter, and type in your password when prompted for it:
```
sudo apt-get install build-essential comerr-dev gettext html2text libaa1-dev libalut0 libasound2-dev libaudio-dev libaudio2 libaudiofile-dev libcaca-dev libcurl4-gnutls-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev libidn11-dev libjpeg62-dev libkadm55 libkrb5-dev libldap2-dev libopenal1\|openal-soft libopenal-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev sharutils tofrodos x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev libvorbis\|libvorbis0a libvorbis-dev xtrans-dev zlib1g-dev
```
It's normal if nothing shows up as you type your password. This command will automatically fetch and install all the [dependencies](http://en.wikipedia.org/wiki/Dependency_%28computer_science%29) which are required in order for the game to run.

Also, you should right click the CRX file. Select "Properties." Go to the "Permissions" tab. Make sure "Allow executing this file as a program" is selected. It should look like this:
[img]http://library.gnome.org/misc/release-notes/2.16/figures/rnusability-permissions.png.sv[/img]

---

### Post by what, what? on 2009-12-28
> **MaxIBoy said:**
> You probably don't have all the dependencies installed.

Copy and paste the following command into a terminal, hit enter, and type in your password when prompted for it:
```
sudo apt-get install build-essential comerr-dev gettext html2text libaa1-dev libalut0 libasound2-dev libaudio-dev libaudio2 libaudiofile-dev libcaca-dev libcurl4-gnutls-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev libidn11-dev libjpeg62-dev libkadm55 libkrb5-dev libldap2-dev libopenal1\|openal-soft libopenal-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev sharutils tofrodos x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev libvorbis\|libvorbis0a libvorbis-dev xtrans-dev zlib1g-dev
```It's normal if nothing shows up as you type your password. This command will automatically fetch and install all the [dependencies]("http://en.wikipedia.org/wiki/Dependency_%28computer_science%29") which are required in order for the game to run.

Also, you should right click the CRX file. Select "Properties." Go to the "Permissions" tab. Make sure "Allow executing this file as a program" is selected. It should look like this:
[IMG]http://library.gnome.org/misc/release-notes/2.16/figures/rnusability-permissions.png.sv[/IMG]

I installed all the stuff and made sure it was executable and yet i try to run it but nothing happens. AmI missing something?

---

### Post by J.K.Makowka on 2009-12-28
Try executing it from a terminal, then it should show the error output.

Most likely you have the same OpenAl error that was mentioned before though, if other games run fine on your system. Just do what Irritant has explained above (create an empty text file in your home directory, add the two lines and rename it to the hidden filename mentioned above).

@Irritant: I am aware that normalmaps cause a significant slowdown, but it seems like that are especially bad in AlienArena. For example Nexuiz runs fine with all sorts of effects (including normalmaps) enabled on my system, while AlienArena drops from something like 80fps to 30fps when I enable them.

---

### Post by donniezazen on 2009-12-28
Has anybody tried it on Lucid?

I am getting following error.

> Package libkadm55 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libkdb5-4 libkadm5srv6 libkadm5clnt6 libgssrpc4
E: Package libkadm55 has no installation candidate

Thanks,
SK

---

### Post by Irritant on 2009-12-28
> **J.K.Makowka said:**
> @Irritant: I am aware that normalmaps cause a significant slowdown, but it seems like that are especially bad in AlienArena. For example Nexuiz runs fine with all sorts of effects (including normalmaps) enabled on my system, while AlienArena drops from something like 80fps to 30fps when I enable them.

Nexuiz doesn't have the detailed environments that Alien Arena has, so it's a hard comparison to make.

---

### Post by MaxIBoy on 2009-12-28
> **soham_1207 said:**
> Has anybody tried it on Lucid?

I am getting following error.



Thanks,
SK
That is a known issue apparantly, to fix it you install a package from the Jaunty repos instead of the Karmic/Lucid ones. See this post:
[http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2#42688](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2#42688)
[quote=farna][SIZE=2]There was a broken dependency -- libkrb53 -- that is a "known issue" in Debian Karmic that all derivatives naturally inherited. I installed the lib from the "Jaunty" repository.[/quote]
Hope that helps!
[/SIZE]

---

### Post by donniezazen on 2009-12-28
> **MaxIBoy said:**
> That is a known issue apparantly, to fix it you install a package from the Jaunty repos instead of the Karmic/Lucid ones. See this post:
[http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2#42688](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2#42688)

Hope that helps!
[/SIZE]

> **Irritant said:**
> That's an OpenAL bug, to fix - 

In your home directory

create:

~/.alsoftrc

and add the entry:
[general] 
drivers = oss

> **Melcar said:**
> If you're running a 32bit system, just download the the zip file, uncompress it, and run the *crx* binary.  You may need to perform the openal workaround explained in this thread by Irritant.
If you're running a 64bit system, the best and easiest way is to recompile the game.  Install dependencies:

```
sudo apt-get install build-essential subversion libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl-mixer1.2-dev libcurl4-openssl-dev libxxf86dga-dev libxxf86vm-dev libopenal-dev

```

Go inside the source subdirectory inside the **Alien Arena** folder, open a terminal in that location, and make:

```
make
```

Once it's finished (with no errors) your new binaries will be inside the **release** subfolder (crx, crded, game.so).  Move *crx* and crded to the main **Alien Arena** folder (overwrite the originals) and *game.so* to the **arena** folder (overwrite the original).  Now you can just run the *crx* binary like normal.  Remember to perform the openal workaround as well.

Thank you all of you.

Another problem is i am not getting full screen and their is no option to get 1200X800 or full screen resolution.

Thanks,
SK.

---

### Post by Melcar on 2009-12-29
Under the resolution options there is a box for fullscreen mode.  You can also select "custom" mode in the resolution entry and simply input your custom values in the boxes below.

---

### Post by donniezazen on 2009-12-29
> **Melcar said:**
> Under the resolution options there is a box for fullscreen mode.  You can also select "custom" mode in the resolution entry and simply input your custom values in the boxes below.

Sorry didn't see it first time.

---

### Post by what, what? on 2009-12-29
> **what, what? said:**
> I installed all the stuff and made sure it was executable and yet i try to run it but nothing happens. AmI missing something?

So what Am I to do?

---

### Post by accLinux on 2009-12-29
Any way to skip around on SP? Do you have to go through the default map rotation? For example, could you start with the new map?

---

### Post by accLinux on 2009-12-29
> **what, what? said:**
> So what Am I to do?

Run it in a terminal, then post your output.

---

### Post by Irritant on 2009-12-29
> **accLinux said:**
> Any way to skip around on SP? Do you have to go through the default map rotation? For example, could you start with the new map?

Sure, go to "host server", then just select the map you want to play.  You can set the public option to "no" if you don't want others to join in.

---

### Post by what, what? on 2009-12-29
> **accLinux said:**
> Run it in a terminal, then post your output.
how?

---

### Post by accLinux on 2009-12-29
> **what, what? said:**
> how?

Well, change to the folder you have it in.

Examble:
(**cd /home/name/alienarena-7.33**)

Then run the program **./crx**

It should then display any error codes, etc

---

### Post by accLinux on 2009-12-29
> **Irritant said:**
> Sure, go to "host server", then just select the map you want to play.  You can set the public option to "no" if you don't want others to join in.

Thanks man.:) Any way to change the default map rotation in SP?

---

### Post by donniezazen on 2009-12-29
How can i setup a link in menu?

---

### Post by accLinux on 2009-12-29
> **soham_1207 said:**
> How can i setup a link in menu?

[http://ubuntuforums.org/showthread.php?t=1186559](http://ubuntuforums.org/showthread.php?t=1186559)

---

### Post by Irritant on 2009-12-29
> **accLinux said:**
> Thanks man.:) Any way to change the default map rotation in SP?

You'd have to manually edit the maps.lst file in the "arena" folder.

One feature we are going to add next release, is to be able to create a map list in the menu.

---

### Post by donniezazen on 2009-12-29
> **accLinux said:**
> [http://ubuntuforums.org/showthread.php?t=1186559](http://ubuntuforums.org/showthread.php?t=1186559)

Yeah i know how to do this but nothing is happening. I am browsing to crx in /opt folder. I have tried both type - Application and Application in Terminal. Also crx and ./crx . Nothing is happening  but when i go to folder and double click on the icon, the game runs perfectly.

---

### Post by accLinux on 2009-12-29
> **soham_1207 said:**
> Yeah i know how to do this but nothing is happening. I am browsing to crx in /opt folder. I have tried both type - Application and Application in Terminal. Also crx and ./crx . Nothing is happening  but when i go to folder and double click on the icon, the game runs perfectly.

Yeah, I have that same Problem. Its kinda weird. I've made shortcuts for Urban Terror, Nexuiz, Saubraten, etc. But the Alien Arena shortcut never works. I thought it might be permissions, or possibly Ubuntu. But I've tried editing the permissions and I've recently switched to Arch, however, it still doesn't work. 

(Anyone that knows what the problem is would be greatly appreciated.)

---

### Post by dondiego2 on 2009-12-29
Here is the error I get

./crx
./crx: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory


Carl

---

### Post by MaxIBoy on 2009-12-29
> **dondiego2 said:**
> Here is the error I get

./crx
./crx: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory


Carl
```
sudo apt-get install libcurl3-gnutls
```

---

### Post by dondiego2 on 2009-12-29
sudo apt-get install libcurl3-gnutls
Reading package lists... Done
Building dependency tree
Reading state information... Done
libcurl3-gnutls is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I still get the original error when trying to run it in terminal.  I am using Kubuntu 9.10

Carl

---

### Post by MaxIBoy on 2009-12-29
OK, wow, I didn't know about this, never would have occured to me, but this MIGHT solve the libcurl problem:
[http://ubuntuforums.org/showpost.php?p=5274720&postcount=5](http://ubuntuforums.org/showpost.php?p=5274720&postcount=5)

---

### Post by dondiego2 on 2009-12-29
That didn't work for me. I already had openssl installed.  I'm still getting that error

./crx
./crx: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory


I have libcurl.so.4 and openssl.

---

### Post by Melcar on 2009-12-29
You running 32bit?

---

### Post by Quinn3r on 2009-12-29
I am having this exact same problem, I am using 32 bit aswell btw. But I can't even get the version that auto downloads working. My screen will start to load it then it shuts off. If I reload it then the screen won't refresh till everywhere I drag my mouse turns white.

Dell M1730 with 512mb Vid card, SLI not on, since my comp won't load if I turn it  on. Koala 9.10. My computer worked yesterday when 64bit was on but, Wine Games would install or when they would, run :/. So this sucks cuz I'm tired of reinstalling Ubuntu.

---

### Post by MaxIBoy on 2009-12-29
Okay, try this:
```
sudo apt-get install strace
strace ./crx 2> temporary_file  
grep "such file" temporary_file 
```That ought to give a list of all files which it can't find, the "fatal" one being toward the end.

---

### Post by what, what? on 2009-12-30
i got this when i tried the crx thingi n terminal:


```
using /home/jake/.codered/data1/ for writing
using /home/jake/.codered/arena/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

``` I think i didnt run it, but did something else, im clueless

---

### Post by MaxIBoy on 2009-12-30
I think you used crded instead of crx.

---

### Post by what, what? on 2009-12-30
> **MaxIBoy said:**
> I think you used crded instead of crx.

so what do i do

---

### Post by MaxIBoy on 2009-12-31
> **MaxIBoy said:**
> Okay, try this:
```
sudo apt-get install strace
strace ./crx 2>temporary_file
grep "such file" temporary_file 
```That ought to give a list of all files which it can't find, the "fatal" one being toward the end.
Try doing that.

It ought to tell you which files are missing.  (I corrected it slightly and re-edited my post.)

---

### Post by accLinux on 2009-12-31
> **what, what? said:**
> so what do i do

Make sure and run **crx**:)
**crded** is the server app. for running an alien arena server.

---

### Post by dondiego2 on 2009-12-31
> **MaxIBoy said:**
> Okay, try this:
```
sudo apt-get install strace
strace ./crx 2> temporary_file  
grep "such file" temporary_file 
```That ought to give a list of all files which it can't find, the "fatal" one being toward the end.


I am running 32 and here are the results for the above commands:

carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ strace ./crx 2> temporary_file
carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ grep "such file" temporary_file
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2", 0xbf8ff7f0)     = -1 ENOENT (No such file or directory)
open("/lib/tls/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/cmov", 0xbf8ff7f0)     = -1 ENOENT (No such file or directory)
open("/lib/tls/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2", 0xbf8ff7f0)    = -1 ENOENT (No such file or directory)
open("/lib/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2/cmov", 0xbf8ff7f0)    = -1 ENOENT (No such file or directory)
open("/lib/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2", 0xbf8ff7f0)         = -1 ENOENT (No such file or directory)
open("/lib/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/cmov", 0xbf8ff7f0)         = -1 ENOENT (No such file or directory)
open("/lib/libcurl.so.4", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/cmov", 0xbf8ff7f0)     = -1 ENOENT (No such file or directory)
open("/usr/lib/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/cmov", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libcurl.so.4", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu", 0xbf8ff7f0) = -1 ENOENT (No such file or directory)
writev(2, [{"./crx", 5}, {": ", 2}, {"error while loading shared libra"..., 36}, {": ", 2}, {"libcurl.so.4", 12}, {": ", 2}, {"cannot open shared object file", 30}, {": ", 2}, {"No such file or directory", 25}, {"\n", 1}], 10./crx: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory
carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ strace ./crx 2> temporary_file
carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ grep "such file" temporary_file
bash: carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$: No such file or directory
carl@carl:~/Documents/alienarena7_33-linux20091227/alienarena7_33$ access("/etc/ld.so.nohwcap",

---

### Post by dondiego2 on 2009-12-31
Do I have to somehow find the libcurl.so.4 file myself and put it in another directory?

---

### Post by MaxIBoy on 2010-01-01
Try this:
```
locate libcurl
```

---

### Post by what, what? on 2010-01-02
.

---

### Post by DasEi on 2010-01-04
On  both, karmic and lucid I had to replace

libkadmin55  by  libkadmin5srv6  in the pre-installs

after that , I created ~/.alsoftrc for the oss-entry,

now I get an error with glx on karmic :

Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - invalid mode


It did work on my lucid v-box , graphics-card is a "unsupported"
 radeon X 1650
strace              : [http://pastebin.com/f758dfb08](http://pastebin.com/f758dfb08)




any workarounds ?

---

### Post by DasEi on 2010-01-04
sudo apt-get install  xorg-driver-fglrx-dev libopengl-perl 

then restarted X   now throws : 

--------- [Loading Renderer] ---------
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  19

---

### Post by DasEi on 2010-01-09
switched to nvidia card, alien running flawlessly on karmic 64 bit now;)

---

### Post by what, what? on 2010-01-09
I download alien arena from playdeb.net and it wont play..

---

### Post by ViperScull on 2010-01-10
> **what, what? said:**
> I download alien arena from playdeb.net and it wont play..

Thats because there is a problem with OpenAl.

Solution:

Open with sudo privileges **/etc/openal/alsoft.conf**
Find the section **drivers**
Uncomment the following line: **#drivers = alsa,oss,solaris,dsound,winmm,port,pulse,wave**
Delete the module **pulse** of the previous line.

The line should look like this:
**drivers = alsa,oss,solaris,dsound,winmm,port,wave**

That's it!

Enjoy the game.

---

### Post by what, what? on 2010-01-10
> **ViperScull said:**
> Thats because there is a problem with OpenAl.

Solution:

Open with sudo privileges **/etc/openal/alsoft.conf**
Find the section **drivers**
Uncomment the following line: **#drivers = alsa,oss,solaris,dsound,winmm,port,pulse,wave**
Delete the module **pulse** of the previous line.

The line should look like this:
**drivers = alsa,oss,solaris,dsound,winmm,port,wave**

That's it!

Enjoy the game.

sudo privileges?

---

### Post by Perfect Storm on 2010-01-11
Like

sudo nano /etc/openal/alsoft.conf


sudo = superuser do

---

### Post by what, what? on 2010-01-11
> **Artificial Intelligence said:**
> Like

sudo nano /etc/openal/alsoft.conf


sudo = superuser do


how do i save it?

---

### Post by what, what? on 2010-01-11
please?

---

### Post by ViperScull on 2010-01-11
When it is modified: Ctrl + O

But if you want to make it easier, edit the file with gedit.

sudo gedit /etc/openal/alsoft.conf

then you just have to click on Save.

---

### Post by what, what? on 2010-01-11
> **ViperScull said:**
> When it is modified: Ctrl + O

But if you want to make it easier, edit the file with gedit.

sudo gedit /etc/openal/alsoft.conf

then you just have to click on Save.

ok but the game still doesnt open

---

### Post by ViperScull on 2010-01-12
> **what, what? said:**
> ok but the game still doesnt open

Have you done all i said?

Uncomment the line, delete the word pulse, save the file and reboot the system?

---

### Post by hero1900 on 2010-01-12
so cool diffrent and for sure best graphics for open source game
so so good i like it but sound not good i mean shooting sound and music not so cool
if they change sound it will rock

---

### Post by what, what? on 2010-01-12
> **ViperScull said:**
> Have you done all i said?

Uncomment the line, delete the word pulse, save the file and reboot the system?

I deleted the word pulse, and uncomment the line? what is that? I thought you just had to delete pulse

---

### Post by what, what? on 2010-01-12
> **what, what? said:**
> I deleted the word pulse, and uncomment the line? what is that? I thought you just had to delete pulse

Ok i got the game to open, one problem though, it says its on fullscreen but its not... its in windowed

---

### Post by what, what? on 2010-01-12
> **what, what? said:**
> Ok i got the game to open, one problem though, it says its on fullscreen but its not... its in windowed
Shown here, and i cant get to video options to change the size and reinstalling the game didnt help with that

[IMG]http://img696.imageshack.us/img696/4999/screenshot2fa.png[/IMG]

---

### Post by Irritant on 2010-01-12
What is your desktop res?

Try bringing down the conole, type gl_mode 1, then vid_restart.  That'll put it on a low resolution at least so you should be able to see the entire menu.

---

### Post by what, what? on 2010-01-12
> **Irritant said:**
> What is your desktop res?

Try bringing down the conole, type gl_mode 1, then vid_restart.  That'll put it on a low resolution at least so you should be able to see the entire menu.

Thank you!

---

### Post by 5dolla on 2010-01-13
ok i got the game running with the above openal fix but now i have scratchy sound 
and I think it makes the game lag out. what should i do next.

---

### Post by MaxIBoy on 2010-01-13
Try editing (or creating) the file .alsoftrc (with a dot in the beginning) in your home folder, and editing it so it looks like this:
```
general
drivers=alsa
```
Or if that doesn't help, try this:
```
general
drivers=oss
```
When using the alsa or oss drivers, only one program can access the sound card at a time, so turn off all music you might have playing, etc.

---

### Post by 5dolla on 2010-01-13
ok ill try this thanks

---

### Post by 5dolla on 2010-01-13
ok thanks for the help that solved my problem!

---

### Post by Tim Mangrum on 2010-01-26
Need help installing...
team@team-desktop:/usr/local/src/alienarena7_33$ ls
Aa1.ico  aa.png  arena  botinfo  crded  crx  data1  docs  source  Tools
team@team-desktop:/usr/local/src/alienarena7_33$ ./crx
using /home/team/.codered/data1/ for writing
using /home/team/.codered/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.


Please help

---

### Post by MaxIBoy on 2010-01-27
Is that the entire output, Tim? Or is there anything after that? Does it just lock up and freeze? Are you sure you used "crx" instead of "crded?" Does any window pop up?

---

### Post by Tim Mangrum on 2010-01-29
No Pop up widows, it just stops. 


team@team-desktop:/usr/local/src$ cd alienarena7_33/
team@team-desktop:/usr/local/src/alienarena7_33$ sudo ./crx
[sudo] password for team: 
using /home/team/.codered/data1/ for writing
using /home/team/.codered/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------

---

### Post by amissot on 2010-02-20
I've installed Alien arena 7.33 but currently can only look, i'm quite inexperienced so may not understand some stuff but i would appreciate your help thanks.

---

### Post by amissot on 2010-02-20
i meant only look up sorry

---

