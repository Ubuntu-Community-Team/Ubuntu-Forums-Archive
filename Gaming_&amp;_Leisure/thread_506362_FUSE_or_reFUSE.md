---
title: "FUSE or reFUSE?"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by sulligogs on 2007-07-21
Hi

I've been using Ubuntu for the past 3 months now and I have to say it is a complete Godsend!  This is the best distro of Linux I've ever used and I hope to think that things can only get even better from this point.  Many thanks Ubuntu!

Anyway, I have a question about a Spectrum Emulator called FUSE (Free Unix Spectrum Emulator).  I can't locate it anywhere on the Synaptic Package Manager and the official website [http://fuse-emulator.sourceforge.net](http://fuse-emulator.sourceforge.net) gives links to download (Debian tarballs), but this is an area where I am still weak on when it comes to installation.

I downloaded the tarballs, both for the emulator and the spectrum libraries, but when I go to compile it, as sudo, I get this error message:-

configure: error: installation or configuration problem: C compiler cannot create executables.

But that's strange because I have GCC installed!

I just wish this emulator was available to download and install from the Synaptic Package Manager because I never have any problems with that.  As I said I'm still a newbie with command line stuff.

Many thanks for any help given

---

### Post by sulligogs on 2007-07-22
Hi again,

I've done a "sudo apt-get install build-essential" on the command line and some extra GCC stuff was installed along with some other stuff.  The installation went further this time.

The libspectrum tarballs have been successfully installed with the commands "./configure", "make" and "make install" with sudo.  No problem there.

But, the core FUSE installation can't get past "make install".  I get:-

make[1]: Entering directory `/home/xxx/Desktop/fuse-0.7.0/pokefinder'
make[2]: Entering directory `/home/xxx/Desktop/fuse-0.7.0/pokefinder'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/xxx/Desktop/fuse-0.7.0/pokefinder'
make[1]: Leaving directory `/home/xxx/Desktop/fuse-0.7.0/pokefinder'
Making install in roms
make[1]: Entering directory `/home/xxx/Desktop/fuse-0.7.0/roms'
make[1]: *** No rule to make target `128-0.rom', needed by `all-am'. Stop.
make[1]: Leaving directory `/home/xxx/Desktop/fuse-0.7.0/roms'
make: *** [install-recursive] Error 1

These are the last few lines when errors start appearing.  What does anybody make of it???

There's a good few spectrum emulators for Windows.  But, it just seems that with Linux they're a bit thin on the ground.  I've used but half the games it plays crashes after a bit.

This emulator seems to be promising, but without getting it to even install I feel dissapointed.  I just want to see what it's like whilst still having a full head of hair.

---

### Post by BigSilly on 2007-07-22
I'm in the same boat as you unfortunately. I've had the same problems trying to compile FUSE, and have thus far gotten nowhere. I gave up and tried out Spectemu in the repos. It's only good for 48k Speccy stuff, but it works. It took me a while to get it going, but I've figured it now and it's great fun.

Give it a go and let me know what you think.

---

### Post by sulligogs on 2007-07-22
Cheers for the response

I got Spectemu running last night.  It crashed a couple of games, but others ran nice.  Yet, it works and that's the main thing I supppose.

Would be nice to have 128k emulation.  Hearing that 3 channel sound smittens me arms flopped into my chair.  What an era!

Oh well, just best to wait around and see if anything pops up.

Thanks for the advice BigSilly :)

---

### Post by BigSilly on 2007-07-22
> **sulligogs said:**
> 
I got Spectemu running last night.  It crashed a couple of games, but others ran nice.  

Heh, wouldn't be a Spectrum if it didn't crash a couple of times! :D

I must say though that I've not had it crash on me yet. Which games bug it out? Do let me know so I can check them out. I agree it would be nice to have the full spectrum (!) of Spectrum emulation on Linux in the repos. I dunno why FUSE isn't in there really.

I was really surprised at the accuracy of the emu though. That you could actually load up a "tape" and listen to the 15 minute "bwwwwooooooooo beep, bwooooooooo bep, bep, bep" as it loads up really set the nostalgia juices flowing. The missus thinks I'm a nut playing the old 48k games on a modern PC!

I think the emu scene on Linux needs some serious love right across the board really. Hopefully now that Linux is really starting to penetrate the home we'll get to see some retro fun that's as good as the Windows variants.

---

### Post by sulligogs on 2007-07-22
I know BigSilly!

The best and easiest emulator out for the Spectrum right now has got to be ZX32 (Win32).  It hasn't been updated in years, but its interface is sound and like the tape loading thingy it sends me dreary eyed infront of the screen.

The first game it crashed on was BratAttack.  That came with Sinclair User some twenty years ago and was one of the first games I ever played.  It loads, but when you go to play the game it freezes and then exits with a message.

I think the second was BlobTheCop.  Another Sinclair User game.  Hmmm.  Strange connection!  Trying to tell me something about Sinclair User though I think Your Sinclair was better.

[ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BratAttack.tap.zip](ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BratAttack.tap.zip)
[ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BlobTheCop.tap.zip](ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BlobTheCop.tap.zip)

Man, I remember back then the hype about computers having a major role in everyday life.  Look at it all now!  Would be nice just to get away from it all - get back to reality and switch off.  I think commercialism has put a dagger into the heart of it all now.  Ain't cool to be geeky these days.

:)

---

### Post by BigSilly on 2007-07-22
When I get the chance I'll give those games a shot. I'm using Windows at the mo ( #-o) but when I pop back into Ubuntu I'll try them out. It's a pity that the emu doesn't give a "R Tape loading error". That would be classy emulation!

I know what you mean about commercialism. I'm lucky I suppose. Having a PC is just a toy to me. I can turn it off and not miss it. But it's worrying that economies and businesses rely on these things. 

It certainly is a far cry from the days of Crash! and Zzap 64. I couldn't go back to cassettes though, with all the anti-Microsoft will in the world!

---

### Post by BigSilly on 2007-07-23
> **sulligogs said:**
> 

[ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BratAttack.tap.zip](ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BratAttack.tap.zip)
[ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BlobTheCop.tap.zip](ftp://ftp.worldofspectrum.org/pub/sinclair/games/b/BlobTheCop.tap.zip)



Dunno if you're still around, but I gave those games you listed a try on Spectemu. Blob the Cop worked just fine. I can't say I had any problems at all playing that game. The other one, Brat Attack, loaded up fine, but when I went to play the game it closed down the emu window, and I got an error message "segmentation core fault - core dumped". I'll have a look around for another version of that game, because it could just be a bad version of it.

I'll let you know. :)

---

### Post by sulligogs on 2007-07-26
Hey there Big Silly

Yeah Brat Attack did the same to me.  I don't expect perfection so I wasn't worried.  I'll give Blob The Cop another go at some point.

It's just handy to have that emulator so if I am in Ubuntu and feel the need to go back a few years I can just run it immediately.

However, it would be so cool to have 128k emulation which is why I went mad on FUSE.  How do I go about suggesting it as a download from the Ubuntu servers?

Sulligogs

---

### Post by BigSilly on 2007-07-26
I haven't got a clue, but if you find out let me know and I'll add my voice too. 

By the way, have you had any luck with the Commodore emulator VICE? I got it off the repository but I'm having no joy trying to use the thing. I found a link to the manual for it, but it's very tricky to get to grips with and is clearly written for those well versed in the behaviour of Linux. 

Let me know anyway.

---

### Post by Sabeltann on 2008-09-11
Hi, hope it's ok to dig up this thread, I couldnt find a more recent one with a solution. but I've just managed to get Fuse 0.9.0
 to build and run ok. I'm using ubuntu 7.10 in a (windows) Virtual PC 2007 environment. I had a clean install prior to this. 

I needed to get the build essentials package using synaptic package manager, and then I found I needed x11-dev which is also on synaptic.

After that I made and installed libspectrum with:
./configure
make
sudo make install

then did the same with fuse
./configure
make
sudo make install

Now I got confused because Fuse couldn't locate the libspectrum libraries. Fortunately I found a howto - which explains everything:
[http://wiki.eeeuser.com/howto:install_spectrum_emulator](http://wiki.eeeuser.com/howto:install_spectrum_emulator)

The solution was to do the following:
cd /usr/lib 
sudo ln -s /usr/local/lib/libspectrum.so.5 libspectrum.so.5 
sudo ln -s /usr/local/lib/libspectrum.so libspectrum.so

sudo ldconfig

It now runs ok. The window size is a bit small, but hopefully I'll figure that out soon :) BTW I'm a total noob! This is the first thing I've ever done successfully in linux after literally years of trying, failing and giving up!

---

### Post by RetroTechie on 2008-10-01
> 
The solution was to do the following:
cd /usr/lib
sudo ln -s /usr/local/lib/libspectrum.so.5 libspectrum.so.5
sudo ln -s /usr/local/lib/libspectrum.so libspectrum.so

sudo ldconfig

Tried this too, but found that just the last command should be enough. I think the reason is this: the loader that searches for shared libraries when you run an executable, keeps a cache for performance reasons. Now when you add shared libraries, it doesn't know about those.

In a distribution, package managers usually take care of things like this. But not always when you manually install libraries, like compiled from source and placed somewhere under /usr/local/
Procedure then becomes this:

1. Check that directory where you manually install shared libs, is noted in /etc/ld.so.conf (on my Ubuntu install, it includes a directory, and /usr/local/lib is mentioned in one of the included files)

2. After manually installing a library, execute "ldconfig" (as root)

You may want to do (2) after *each* manual install of a shared library. I installed libdsk, lib765 and libspectrum (in that order), but running "ldconfig" once after this was enough to get fuse working. If you already compiled fuse, you can use the "ldd" command on the executable like this: "ldd /usr/local/bin/fuse". That will show what the dynamic loader sees as 'missing'. You might see a few 'not found' entries for libspectrum etc., and see these updated after the "ldconfig" command.

Hope this helps. Better would be if someone picked up the task of maintaining a full-featured fuse package for installation using regular Ubuntu package tools. I saw a Spectrum emulator in the repositories, but upstream project for that looked old/unmaintained (read: not as good as fuse).

---

### Post by schneil on 2011-05-14
HI all

I know this is an old thread, but following the instructions I managed to install fuse  1.0.0.1a from source.  (Not bad for a noob!)

However I can't get sound working.  It says
"fuse: error: couldn't open sound device '/dev/dsp': No such file or directory"

can anyone help me?

thanks

---

