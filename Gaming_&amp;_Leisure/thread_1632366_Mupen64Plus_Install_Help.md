---
title: "Mupen64Plus Install Help"
date: 2010-11-27
forum: Gaming &amp; Leisure
---

### Post by Siramau on 2010-11-27
Hello,

I'm completely new to Linux, I converted from OS X five days ago. Everything up until now has gone smoothly, and I've been able to solve any problems I've had by googling. 

I tried installing Mupen64Plus via the software center, but it said it required installation of untrusted packages and would not let me continue. (Error text: Requires installation of untrusted packages.T he action would require the installation of packages from not authenticated sources. Details: libsdl-ttf2.0-0 libxdg-basedir1 mupen64plus). I went to their Google code site, downloaded the most recent binary for Linux (1.99.4), extracted it to my home folder (I think), and tried to run the install script in terminal. Result:

```
sabrina@Sabrina-Latitude-D510:~$ sudo ./install.sh
Installing Mupen64Plus Binary Bundle to /usr/local
install: cannot stat `libmupen64plus.so.2.*': No such file or directory

```I'm not sure if I did any part of the installation process correctly, except for downloading the file (I think). I read all of the threads related to this, but I couldn't find anything that helped. What would be extremely helpful would be a complete-beginner no-prior-knowledge-assumed step-by-step walkthrough of the install process, because I don't really know what I'm doing. I understand what sudo means, and what a shell script is, so I do know *what* I'm typing into terminal, but not if it's correct.

Thanks in advance!

---

### Post by thatguruguy on 2010-11-27
Try installing from synaptic instead of the software center.

---

### Post by DangerOnTheRanger on 2010-11-27
Yeah, Synaptic still lets you choose to install packages even if they come from untrusted sources.

Synaptic is under System > Administration > Synaptic Package Manager.

---

### Post by Siramau on 2010-11-27
Okay, thanks. That works, although it's an old version. Is installing from the binary difficult (I would rather install the newest version if that's an option), or was I just messing something up?

---

### Post by ThatBum on 2010-11-28
Hello. I just ran the install script for mupen64plus, and it ran fine. This was my output:
```
justyn@NetbookOfAwesomeness:~/Downloads/mupen64plus-bundle-linux32-1.99.4$ sudo ./install.sh 
[sudo] password for justyn: 
Installing Mupen64Plus Binary Bundle to /usr/local
install: creating directory `/usr/local/share/mupen64plus'
install: creating directory `/usr/local/share/mupen64plus/doc'
install: creating directory `/usr/local/man/man6'
install: creating directory `/usr/local/lib/mupen64plus'
Installation successful.
```
All I did was extract the archive from [mupen64plus' Google Code]("http://code.google.com/p/mupen64plus/downloads/detail?name=mupen64plus-bundle-linux32-1.99.4.tar.gz&can=2&q="). I assume you used this, it is the latest version, being built just 5 days ago. Then, without moving anything from where it was extracted, just execute install.sh as root. If you still have problems, I can make a .deb for you.

---

### Post by Siramau on 2010-11-28
*facepalm* Noob mistake. I didn't change the directory first. Thanks!

Except this is what happens when I run it...
Is it because I'm running it by itself and without a ROM?

```
sabrina@Sabrina-Latitude-D510:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 1.99.4

dlopen('./libmupen64plus.so.2') error: ./libmupen64plus.so.2: cannot open shared object file: No such file or directory
AttachCoreLib() Error: failed to find Mupen64Plus Core library

```

---

### Post by ThatBum on 2010-11-28
Oh, I found out some things about the Google Code version.

1. It has no GUI unlike the repos version, it only takes command line arguments.
2. Only Rice video plugin is included, which isn't very good.
3. Most important, it depends on libpng14, which hasn't made it down the pipe to ubuntu or even debian repos. Ubuntu only has libpng12. I think SUSE has it.

I think it's smarter to get the repos version, at it's been tested for stability and things for ubuntu. Better yet, you can use WINE to run Project64, which is a far better emulator.

E: Also, I despise Software Center. It was fine back in Jaunty when it was just Add/Remove Software, but it somehow mutated into this huge bloated thing. I just use apt most of the time, or Synaptic if I don't know the exact name of the package. And for installing non-repo debs, GDebi. Also apt-file makes life so much easier...[/RANT]

E2: Shoot you ninja'd me Siramau. Anyway, yes, that's the EXACT same error I got when I tried to run it. it's looking for a library that isn't there. The lib got installed to /usr/local/lib, but no matter where I move it (/usr/lib, /usr/local/lib/mupen64plus, etc.) it won't work. Bah humbug.

---

### Post by Siramau on 2010-11-28
Okay, thanks.

1. It is only command line, but there are several GUIs avalible. It doesn't really bother me though, once the game's up there's no need for a GUI. 
2. I don't really care about having only Rice, since I'm pretty much downloading this to play OoT, and the site says it works best with Rice. 
3. I have absolutely no idea what that means.

Forgive my noobishness, but what's the repos version? Google says repository, but I don't know what that means in this context.

---

### Post by thatguruguy on 2010-11-28
The "repos" version is the version in the repository.  I.e., the version in synaptic.

---

### Post by Siramau on 2010-11-28
Oh okay, thanks.

The only problem with the repos version is it's only 1.5. I guess as long as it works okay with OoT (I have yet to test it) then it will suffice until 2.0 comes out, and I can worry about installation from binary then.

Update: Can't get 1.5 running either. *sigh*.

---

### Post by ThatBum on 2010-11-28
Does it not even run? It works fine for me, even on my crappy little netbook.
```
justyn@NetbookOfAwesomeness:~$ mupen64plus 
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

Config Dir:  /home/justyn/.config/mupen64plus/
Data Dir:  /home/justyn/.local/share/mupen64plus/
Cache Dir:  /home/justyn/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Rom cache up to date. 0 ROMs.

```

It then presents you with a pretty self-explanatory GUI.

What I meant about the libpng thing...a lib, or library, is a bunch of common functions that a bunch of different programs call instead of having to write them every time and make things unnecessarily big and tangled. If you're familiar with Windows monkeying, the equivalent is dll files (dynamically linked library). I don't know how they do it in OSX, bu it might be similar because it's also UNIX-based like Linux. libpng12 in particular is a library for creating and manipulating PNG image files. The ubuntu repo version is libpng12, and the version required by the 1.99.4 incarnation of mupen is libpng14. The ubuntu repo version is therefore out of date. A way to get around it is to grab the package from another distribution that has it and decompress it, or compile it from source, both of which are kludge fixes.

Holy crap, I feel smart now.

---

### Post by Siramau on 2010-11-28
I realized I hadn't uninstalled 1.99.4. Oops. Problem solved.

Well, it runs, but the sound is sooo choppy. Hopefully I can tinker with settings and fix it, because playing OoT without sound is close to a nerdcrime.

Okay, thanks. I understand.

---

### Post by ThatBum on 2010-11-28
> **Siramau said:**
> Well, it runs, but the sound is sooo choppy.

Your machine's specs might be insufficient to run the emulator at full speed. The framerate is tied to the sound, so they don't get out of sync. So if you get bad framerate, you get bad sound. How is your framerate? Do you know your processor and graphics card? Do you have integrated graphics?

Also, you might want to use the Glide64 plugin, it's a little better. Change some settings around too.

On an unrelated note, I beat OoT for the first time in a decade on a real N64 a week or so ago. Gannon kept kicking my *** in the final battle...I got him eventually. Now I'm going at Majora's Mask. Fun.

Protect the Triforce!

[COLOR=Red]E: I found libpng14 in SuSE's repos. I got 1.99.4 to work for me. Assuming you know how to move files around in a terminal, just uncompress the archive attached here, and stick the contents into /usr/lib. If you reinstall 1.99.4, it should work. If you run it without telling it where a ROM is, it should say this if it's set up right.

[/COLOR]```
[COLOR=Red] __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4[/COLOR] [COLOR=Red]
            Includes support for Dynamic Recompiler.
Error: no ROM filepath given[/COLOR]
```[COLOR=Red]
[/COLOR] 
E2: Better yet, I've made a deb of 1.99.4 with libpng14 in it. Enjoy y'all.
[http://dl.dropbox.com/u/5771418/mupen64plus.deb](http://dl.dropbox.com/u/5771418/mupen64plus.deb)

---

### Post by Siramau on 2010-11-29
I actually have almost no idea what my system specs are. I'm on a Dell Latitude D510 (from '02), so my guess is they're not great. After playing for a bit, the sound got better, it was only really choppy for the intro screen. Now I just need a controller, because playing this on a keyboard is ridiculous. 

I have yet to play OoT or any game actually on the N64, it's a bit before my time. I figured OoT is too awesome not to play through in at least some form.

Awesome, thank you :D! This works perfectly.

---

### Post by ThatBum on 2010-11-30
> **Siramau said:**
> I have yet to play OoT or any game actually on the N64..

You haven't??? Blasphemy! I grew up with that game (that and Majora's Mask).

This is my controller [http://www.logitech.com/en-za/gaming/controllers/devices/7359](http://www.logitech.com/en-za/gaming/controllers/devices/7359)
It works great, even has rumble. Not sure how you would configure it from the command line though.

By the way, to see what hardware you have, run "lshw" as root.

---

### Post by trinitydan on 2010-12-01
Controllers are a must for playing Mupen64 with any degree of nostalgic authenticity.  The only trouble is getting the controller to behave like the N64 controller, which is a kind of unique setup with six buttons on the right side of the controller whereas all the controllers I have seen have only four.  You can overcome it with some creative configuring but you have to reconfigure for different games and some are more difficult to set up, like Goldeneye for example, the controls on that game are complicated.  I have yet to find a comfortable configuration to play that game.  I am playing with a MadCatz xBox 360 controller.  It's a cheapy ($25US) from a nationwide juggernaut chain store.  It has great support under Ubuntu 10.10 with the drivers working out of the box (also including rumble), you will definitely want to get the graphic interface installed though when it comes to configuring it.  Good luck with the game playing!

---

### Post by ThatBum on 2010-12-02
What I do with my four button, two analog stick controller is map all the C-buttons to my right stick, which works pretty well, unless I have to hit Up C and Down C or Left C and Right C at the same time, but that never happens. In doing this, I've essentially made a GameCube-style C-stick, but it's only digital.

I put L and R on the triggers, and Z on the shoulder bumper above the trigger, also GameCube style. That means my X and Y buttons are unused. Ho-hum.

Another option is [one of these]("http://www.amazon.com/Nintendo-64-N64-2in1-Controller-Adapter/dp/8565000168"). It's a little converter box that gets the inputs from a genuine N64 (or Playstation) controller and runs it through an SDL/DirectInput chipset to your computer via USB. Some words of warning: they tend to be unreliable (I've had one, it died), they tend to have a low compatibility rate with third-party controllers (and even certain revisions of first-party Nintendo ones, it's a bit of a crapshoot), and force feedback does not work. Also, obviously, you just get the box, you need to get an N64 controller to use with it. I think having it be able to work with a Playstation controller is redundant, because there are plenty of controllers out there that have Playstation controls and are native USB (like mine).

One more worth mentioning...the elusive [Adaptoid]("http://www.adaptoid.com/"). This thing looks fantastic, it has a custom chipset designed for the N64 controller. It DOES support force feedback if you have a Rumble Pak, and you can even use a Memory Pak to save an emulated game, and continue the game on a real N64, and vice versa. However, the custom chipset also means that it needs a custom driver, which is a pain, because all other controllers are almost universally SDL/DirectInput or Xinput (even the N64-USB thing above, it doesn't need additional drivers). Also, every single emulator that wants to work with the Adaptiod has to have an Adaptoid input plugin ported to it for force feedback and saving to a Memory Pak to work. Software support is therefore poor (especially in Linux, I bet). Most importantly, they are nigh-impossible to find, since they are not being manufactured anymore, and haven't for years. You would be incredibly lucky to find one, and even if you did, they are absurdly expensive (or so I hear). The original manufacturers must have missed the market, because even now they're selling like hotcakes.

Hope I was helpful.

---

### Post by STurner31 on 2010-12-04
I feel like I'm missing some obvious step here. I downloaded the .deb linked above, but when I run Package Installer, I get this status:

```
Error: Dependency is not satisfiable: liblzma2 (>= 4.999.9beta)
```

and it won't let me install. Is there a different method I should be using for this .deb?


BTW, I'm running Lucid on an older laptop. I tried mupen64plus 1.5 from the repos, and it was slow and buggy. I spent a couple of hours trying as many different combinations of the graphics and sound settings as possible, but it was a fruitless effort. Project64 works flawlessly under Windows XP on the same machine, but running it under WINE makes it laggy (which is expected, I guess). I really would prefer playing N64 games under Linux, since that's where I do all my work. I guess what I'm looking for is the ability to take a 10 minute Rogue Squadron break from reading papers. If I have to boot into a different OS just to play, I know I'm going to stay for longer than that.

One more thing: always check ebay before dropping a wad of cash on something. When I started using zsnes and Gens/GS, I found 2 Sidewinder USB gamepads for $8. They have 6 buttons on the right, two shoulder buttons, and a large button in the center. If you can remap your muscle memory, you can use the center button as you would the z-trigger on the original N64 controller. So far, they work fine under Lucid. (I managed to pull off a Fatality in MK II the other day, so I guess that was the real usability test.)

---

### Post by ThatBum on 2010-12-05
> **STurner31 said:**
> I feel like I'm missing some obvious step here. I downloaded the .deb linked above, but when I run Package Installer, I get this status:

```
Error: Dependency is not satisfiable: liblzma2 (>= 4.999.9beta)
```and it won't let me install. Is there a different method I should be using for this .deb?


Oh jeez, I built it in Maverick...I forgot Lucid has older packages. I don't think Lucid has liblzma2, from what [packages.ubuntu.com tells me]("http://packages.ubuntu.com/search?keywords=liblzma2&searchon=names&suite=all&section=all"). It is a compression/decompression algorithm. Maybe mupen uses it to decompress the ROM images?

I got the list of dependencies from Maverick's 32bit mupen 1.5, which follows:

```
Depends: libbz2-1.0, libc6 (>= 2.11), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.16.0), libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.12.0), liblzma2 (>= 4.999.9beta), libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libsamplerate0, libsdl-ttf2.0-0, libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.4.0), libxdg-basedir1, zlib1g (>= 1:1.1.4), ttf-dejavu-core
```This is the list from Lucid's:

```
Depends: libbz2-1.0, libc6 (>= 2.7), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.16.0), libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.12.0), liblzma1 (>= 4.999.9beta), libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libsamplerate0, libsdl-ttf2.0-0, libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.4.0), libxdg-basedir1, zlib1g (>= 1:1.1.4), ttf-dejavu-core
```So it seems that Lucid needs liblzma1 then. I'll make a Lucid one shortly.

E: Here you go! Try this one:
[http://dl.dropbox.com/u/5771418/mupen64pluslucid.deb](http://dl.dropbox.com/u/5771418/mupen64pluslucid.deb)

---

### Post by STurner31 on 2010-12-05
Thanks, ThatBum!

I just tried the mupen64pluslucid.deb and it works. The graphics and sound are still a bit slow when I load up OoT, but I think it's because of the Rice plugin. I'll try to tweak the settings to make it work better.

Speaking of OoT, all the talk about that game earlier ITT made me want to play it again. So I grabbed a ROM and proceeded to time warp ~10 hours into the future. Seriously, I feel like I blinked and then BAM! There I was with two Spiritual Stones, about to get the third, and then I noticed the sunrise was actually happening irl. oops. The only real downside was that I had to boot into Windows to do it. Hopefully, my future nerd-out sessions can happen in Linux with the latest mupen.

E: sorry for being such a n00b, but can someone give detailed instructions for downloading, adding, and using plugins with this emulator? I'm assuming the plugins are cross-platform, and that if I download one and put in the /usr/local/share/mupen64plus/ folder, I can use it by adding "--gfx (plugin)" or "--audio (plugin) to the command when I call the program. Does this sound correct?

---

### Post by ThatBum on 2010-12-07
I have no idea...I don't know much about mupen, I just packaged it. I only know how to do it through the GUI interface. Try the man page.

If you have WINE, you can run Project64, which is a far better emulator, IMO.

---

### Post by emoguitarist06 on 2011-01-23
> **ThatBum said:**
> Your machine's specs might be insufficient to run the emulator at full speed. The framerate is tied to the sound, so they don't get out of sync. So if you get bad framerate, you get bad sound. How is your framerate? Do you know your processor and graphics card? Do you have integrated graphics?

Also, you might want to use the Glide64 plugin, it's a little better. Change some settings around too.

On an unrelated note, I beat OoT for the first time in a decade on a real N64 a week or so ago. Gannon kept kicking my *** in the final battle...I got him eventually. Now I'm going at Majora's Mask. Fun.

Protect the Triforce!

[COLOR=Red]E: I found libpng14 in SuSE's repos. I got 1.99.4 to work for me. Assuming you know how to move files around in a terminal, just uncompress the archive attached here, and stick the contents into /usr/lib. If you reinstall 1.99.4, it should work. If you run it without telling it where a ROM is, it should say this if it's set up right.

[/COLOR]```
[COLOR=Red] __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4[/COLOR] [COLOR=Red]
            Includes support for Dynamic Recompiler.
Error: no ROM filepath given[/COLOR]
```[COLOR=Red]
[/COLOR] 
E2: Better yet, I've made a deb of 1.99.4 with libpng14 in it. Enjoy y'all.
[http://dl.dropbox.com/u/5771418/mupen64plus.deb](http://dl.dropbox.com/u/5771418/mupen64plus.deb)

I tried installing but your .deb is only built of i386 but I'm running 10.10 64bit. I am running 1.5 via software center successfully but sound is very chopping but then again I'm not sure if my specs are enough

Asus 1201N, Atom 330 (dual core @ 1.6 plus hyper threading but mupen can only use one core) + Nvidian Ion (first gen)

I thought of using the --force-architecture command but I decided to post this instead

---

### Post by ThatBum on 2011-01-23
I recently got a machine (built it from scratch, actually) that I put 64 bit OS's on. It's a beast, with a i7 950 OC'd to 3.8 GHz, a GTX 570, 6GB of 1600MHz RAM, liquid cooling, etc, etc. I would make you a 64 bit package, but I presently got a bad fever and don't feel like doing anything. Maybe in a few days, if I don't forget.

---

### Post by emoguitarist06 on 2011-01-23
> **ThatBum said:**
> I recently got a machine (built it from scratch, actually) that I put 64 bit OS's on. It's a beast, with a i7 950 OC'd to 4.2 GHz, a GTX 570, 6GB of 1600MHz RAM, liquid cooling, etc, etc. I would make you a 64 bit package, but I presently got a bad fever and don't feel like doing anything. Maybe in a few days, if I don't forget.

Living up to your user name eh? Lmao jk jk
Or you could just teach me how muahaha another jk jk lol

---

### Post by ThatBum on 2011-01-25
Yeah, I shot up a jewlery store and pawned off the loot for high-end computer parts (JK, obviously).

Unfortunately, whatever I have has worsened and is exacerbating my asthma. I can hardly breathe as I type this. I think I might have to see a doctor because I feel completely enervated. I also have lots of reflex coughing, the top back of my lungs hurting when I inhale, and severe wheezing, all of which makes it hard to sleep dispite the exhaustion. At least I'm still thinking lucidly. Still, this is the longest lasting (but not most intense) asthma issue I've ever had at 3 days and counting. My temperature seems to be getting back to normal (from about 102 F to 99) but the symptoms aren't going away; my body must stlll flipping out about it for some reason. Good thing I got lots of Albuterol...I'm also not making this up to get out of helping on the forum, I swear!

I guess I'll be back in a while, I don't think I'm going to die...not yet, at least.

E: Wow, big monolog about being sick. Didn't see how long it was until I posted it. I'm too tired to edit it...

---

### Post by ThatBum on 2011-01-31
Whew, feeling a lot better today after a trip to the ER a while ago, so here we go.

I've looked at the Google Code again, and this is new since I last looked at it.

> This was built on Ubuntu 9.10, linking against libpng 1.2.  The featured Linux binary links against libpng 1.4, failing to run on some distributions including Ubuntu.

So now I don't need to stick the new libpng in it, so that's good. Even better, this new package built for 64 bit is the subversion one (or whatever source management they use), so the engine was built on January 4th, and the plugins on the 20th. You can't get much newer than that. It still doesn't have a GUI though.

So try this.

[http://dl.dropbox.com/u/5771418/mupen64plus_amd64.deb](http://dl.dropbox.com/u/5771418/mupen64plus_amd64.deb)

---

