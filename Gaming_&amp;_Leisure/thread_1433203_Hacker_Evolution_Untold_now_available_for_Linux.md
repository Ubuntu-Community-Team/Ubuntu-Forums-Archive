---
title: "Hacker Evolution: Untold now available for Linux"
date: 2010-03-18
forum: Gaming &amp; Leisure
---

### Post by mrobert on 2010-03-18
Hello everyone,

We would like to announce the port of our popular game:
**Hacker Evolution: Untold** to Linux.

**Website and download link:**
[http://www.exosyphen.com/page_hacker-evolution-untold.html](http://www.exosyphen.com/page_hacker-evolution-untold.html)

[IMG]http://www.exosyphen.com/xproduct-hackerevolution-untold/site-screenshot-500pix.jpg[/IMG]

**About Hacker Evolution: Untold**
When the number of computers in existence and their processing capacity exceeds that of all mankind, a point of technological singularity is encountered.
A massive economic and systematic crisis hits the entire world. Nobody knows the exact cause, and all solutions to fix it, are failing. We are about to lose our position as a dominant specie on the planet, in favor of something we have created... computers.

You play the role of Brian Spencer, a young computer programmer working for a company he started with a couple of friends, which has developed the technology from where it all started. 

When you are being framed for crime, it's up to you to prevent computers from becoming the next dominant specie, and clear your name, using your hacker skills.

The concept behind Hacker Evolution: Untold is to create a game that challenges the gamers intelligence, attention and focus, creating a captivating mind game. Solve puzzles, examine code and bits of information, to help you achieve your objectives.

---

### Post by Nisal on 2010-03-23
when playing the ganme i think its kinda slow what can be the problem?

---

### Post by mrobert on 2010-03-23
> **Nisal said:**
> when playing the ganme i think its kinda slow what can be the problem?

Hmm ... not sure.
What are your system specs?
Also, what is the framerate displayed in the top right corner?

---

### Post by Nisal on 2010-03-23
> **mrobert said:**
> Hmm ... not sure.
What are your system specs?
Also, what is the framerate displayed in the top right corner?

i have 2ghz AMD  Processer With 512MB Ram and 128mb VGA

---

### Post by matchett808 on 2010-03-23
what no .deb? lol

---

### Post by mrobert on 2010-03-24
@Nisal: That system is quite at the lower end of the game's requirements :(

@matchett808: coming soon.

---

### Post by thesenu on 2010-03-24
tank your info...

---

### Post by Nisal on 2010-03-25
> **mrobert said:**
> @Nisal: That system is quite at the lower end of the game's requirements :(

@matchett808: coming soon.

what the exact requirement since im new to linux i had installed it in secondary PC if u give me exact requirement i can try dual booting my main PC

---

### Post by mrobert on 2010-03-28
What is the FPS you are getting? (The number in the top right corner)

---

### Post by Perfect Storm on 2010-04-27
I just madePkgbuild for Arch Linux(both i686 and x86_64) of the demo: [http://aur.archlinux.org/packages.php?ID=36775](http://aur.archlinux.org/packages.php?ID=36775)

---

### Post by mrobert on 2010-04-27
> **Artificial Intelligence said:**
> I just madePkgbuild for Arch Linux(both i686 and x86_64) of the demo: [http://aur.archlinux.org/packages.php?ID=36775](http://aur.archlinux.org/packages.php?ID=36775)

Thanks a lot!
If there is anything we can do for you, just let me know.

---

### Post by Perfect Storm on 2010-04-27
No problem.

I have just ordered the game (downloading as we speak). I might build one as well for the full game.

---

### Post by mrobert on 2010-04-27
Cool! :)
I hope you enjoy the game.

---

### Post by Perfect Storm on 2010-04-28
Minor changes made to the Arch linux pkgbuild of Hacker Evolution Demo:
[http://aur.archlinux.org/packages.php?ID=36775](http://aur.archlinux.org/packages.php?ID=36775)


Now also Arch pkgbuild for full version;
[http://aur.archlinux.org/packages.php?ID=36809](http://aur.archlinux.org/packages.php?ID=36809)

Just drop the full .zip file of the game into your build folder and the pkgbuild will select and install the right architecture (i686 or x86_64). Then setting up right permissions, icon launcher and terminal launcher (and ofcause solving dependencies).


Just let me know if any changes hits full version or the demos so I can make the changes to the pkgbuilds.

---

### Post by mrobert on 2010-04-29
Thanks!
I will keep you updated if there are any changes.

---

### Post by ben2000677 on 2010-07-12
I can't get the demo to install! maybe I'm doing something wrong, I'm double clicking the hacker-evolution executable after extracting the .tar.gz and nothing happens!
please help :) 
Ben

---

### Post by mrobert on 2010-07-12
Can you run it in the console, by typing:

./hackerevolution

That will spill out whatever error occurs.

---

### Post by ben2000677 on 2010-07-12
ye haha remembered the whole './' thing. 
I just done it and got this:
```
./hacker-evolution: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

---

### Post by mrobert on 2010-07-12
You have to install libSDL.
Do you know how to use this?

---

### Post by ben2000677 on 2010-07-12
search for it in synaptic? ...I honestly have no idea :p

---

### Post by mrobert on 2010-07-12
That's it.
Install it using Synaptic.

Let me know if it worked.

---

### Post by ben2000677 on 2010-07-12
there are 28 packages listed under libSDL which one do i need?

---

### Post by mrobert on 2010-07-12
Try this in the console:
sudo apt-get install libsdl-1.2debian libsdl-image1.2 libsdl-mixer1.2

It should get them installed easier.
Or select the packages from above in Synaptic.

---

### Post by ben2000677 on 2010-07-12
can't find package libsdl-1.2debian, the rest I got ok :)

---

### Post by ben2000677 on 2010-07-12
Woo! i did the ./Hacker-Evolution and it booted up! how would i make a shortcut for the ./ command?

---

### Post by mrobert on 2010-07-12
Try running the game with what it has installed so far.

---

### Post by mrobert on 2010-07-12
> **ben2000677 said:**
> Woo! i did the ./Hacker-Evolution and it booted up! how would i make a shortcut for the ./ command?

No need.
It should run double-clicked now, also.

---

### Post by ben2000677 on 2010-07-13
you're right! the games pretty good too! I'm planning on getting the full version except i got a problem, 
does anyone else have problems typing capitals in game?
shift + any key doesn't work so I can't type file names with underscores
e.g some_cool_/file.exploit...
any suggestions?

---

### Post by mrobert on 2010-07-14
Capitals don't work on purpose, since they are not needed and the game is case insensitive.

This was a design decision, to keep the "typing part" within reasonable complexity.

---

### Post by ben2000677 on 2010-07-14
ok that's all cool, but how_do i_write_an_underscore in the game?

---

### Post by mrobert on 2010-07-14
It should be SHIFT + the key on right of 0 (normally).
Doesn't it work to you?

Also, you can press TAB to autocomplete when you get to type the "_"

---

### Post by ben2000677 on 2010-07-14
nope, its what i've been trying SHIFT + 'anything' doesn't work, it just comes out with whatever key pressed without the shift.

---

### Post by mrobert on 2010-07-15
> **ben2000677 said:**
> nope, its what i've been trying SHIFT + 'anything' doesn't work, it just comes out with whatever key pressed without the shift.

This issue has been solved now.
Please download the game again from our website as we have updated it.

---

### Post by angelsinraver on 2010-08-27
so I cannot get the demo to run. when I try to run the program from the gui it does nothing, or at least nothing i can see. when i run the program from terminal it goes through a long list of things all of which it says its testing and are ok, after that it just stops.
I tried all the things previously mentioned in this thread, if anyone could help that would be awesome

---

### Post by mrobert on 2010-08-27
Try this before running the game:

apt-get install openssh-server

---

### Post by angelsinraver on 2010-08-27
tried it still got nothin

---

### Post by mrobert on 2010-08-28
Can you run it in a terminal window and paste me the errors it throws out?

---

### Post by angelsinraver on 2010-09-01
Powered by CrissCross 0.8.0-rc3
    [http://www.uplinklabs.net/crisscross/](http://www.uplinklabs.net/crisscross/)
(c) 2006-2010 by Uplink Laboratories. Licensed under the New BSD License.

heLog::heLog() - log file opened.


Testing archive /home/sin/Desktop/heuntold-demo-2.2-rc3-5-g48e8f7a-linux-x86/bin/../data.dat

Testing     heuntold-data/command.alias                               OK 
Testing     heuntold-languages/heut-font-french.bmp                   OK 
Testing     heuntold-data/engine.ini                                  OK 
Testing     heuntold-languages/heut-font-english.png                  OK 
Testing     heuntold-graphics/intro-background.png                    OK 
Testing     heuntold-graphics/main-background.png                     OK 
Testing     heuntold-graphics/mainmenu-anim-worldmap.png              OK 
Testing     heuntold-graphics/mainmenu-animbar.png                    OK 
Testing     heuntold-graphics/mainmenu-background-1440-1024-demo.png  OK 
Testing     heuntold-graphics/mainmenu-background-1440-1024.png       OK 
Testing     heuntold-graphics/mainmenu-check-false.png                OK 
Testing     heuntold-graphics/mainmenu-check-true.png                 OK 
Testing     heuntold-graphics/mainmenu-return.png                     OK 
Testing     heuntold-graphics/mainmenu-volumebar-slider.png           OK 
Testing     heuntold-graphics/mainmenu-volumebar.png                  OK 
Testing     heuntold-graphics/mainmenu-window-cursorbackground.png    OK 
Testing     heuntold-graphics/mainmenu-window.png                     OK 
Testing     fonts/Lucida Console.ttf                                  OK 
Testing     fonts/Trebuchet MS.ttf                                    OK 
Testing     heuntold-data/bounce-help.txt                             OK 
Testing     heuntold-data/console-help.txt                            OK 
Testing     heuntold-languages/languagedefines.txt                    OK 
Testing     heuntold-data/message-levelcompleted.txt                  OK 
Testing     heuntold-data/popup-quickhelp.txt                         OK 
Testing     heuntold-data/text-intro-1.txt                            OK 
Testing     heuntold-data/text-intro-2.txt                            OK 
Testing     heuntold-data/text-intro-3.txt                            OK 
Testing     heuntold-data/textanim-consoleboot.txt                    OK 
Testing     heuntold-data/textanim-deletelogs.txt                     OK 
Testing     heuntold-data/textanim-killtrace.txt                      OK 
Testing     fonts                                                     OK
Testing     heuntold-data                                             OK
Testing     heuntold-graphics                                         OK
Testing     heuntold-languages                                        OK
All OK

Testing archive /home/sin/Desktop/heuntold-demo-2.2-rc3-5-g48e8f7a-linux-x86/bin/../sound.dat

Testing     heuntold-music/DJ-Velocity-Exposure.mp3                   OK 
Testing     heuntold-music/DJ-Velocity-Manhattan.mp3                  OK 
Testing     heuntold-music/DJ-Velocity-Sakura.mp3                     OK 
Testing     heuntold-music/DJ-Velocity-Symbiotica.mp3                 OK 
Testing     heuntold-music/hemusic-djvelocity-conceptual-design.mp3   OK 
Testing     heuntold-music/hemusic-djvelocity-plasma.mp3              OK 
Testing     heuntold-music/hemusic2-djvelocity-hardwire.mp3           OK 
Testing     heuntold-music/hemusic2-djvelocity-intuition.mp3          OK 
Testing     heuntold-music/track-intro.mp3                            OK 
Testing     heuntold-music/hc-playlist-game.txt                       OK 
Testing     heuntold-music/hc-playlist-intro.txt                      OK 
Testing     heuntold-music/hc-playlist-menu.txt                       OK 
Testing     heuntold-soundfx/0.wav                                    OK 
Testing     heuntold-soundfx/1.wav                                    OK 
Testing     heuntold-soundfx/10.wav                                   OK 
Testing     heuntold-soundfx/2.wav                                    OK 
Testing     heuntold-soundfx/3.wav                                    OK 
Testing     heuntold-soundfx/4.wav                                    OK 
Testing     heuntold-soundfx/5.wav                                    OK 
Testing     heuntold-soundfx/6.wav                                    OK 
Testing     heuntold-soundfx/7.wav                                    OK 
Testing     heuntold-soundfx/8.wav                                    OK 
Testing     heuntold-soundfx/9.wav                                    OK 
Testing     heuntold-soundfx/countdown-disconnect.wav                 OK 
Testing     heuntold-soundfx/hesfx-click.wav                          OK 
Testing     heuntold-soundfx/hesfx-hit.wav                            OK 
Testing     heuntold-soundfx/hesfx-newmessage.wav                     OK 
Testing     heuntold-soundfx/hesfx-tick.wav                           OK 
Testing     heuntold-soundfx/hesfx_untold_email.wav                   OK 
Testing     heuntold-soundfx/hesfx_untold_mapzoomin.wav               OK 
Testing     heuntold-soundfx/hesfx_untold_searching.wav               OK 
Testing     heuntold-soundfx/hesfx_untold_tick2.wav                   OK 
Testing     heuntold-soundfx/hesfx_untold_ui1.wav                     OK 
Testing     heuntold-soundfx/hesfx_untold_ui2.wav                     OK 
Testing     heuntold-soundfx/voice-accepted.wav                       OK 
Testing     heuntold-soundfx/voice-access-denied.wav                  OK 
Testing     heuntold-soundfx/voice-all-systems-operational.wav        OK 
Testing     heuntold-soundfx/voice-closing.wav                        OK 
Testing     heuntold-soundfx/voice-complete.wav                       OK 
Testing     heuntold-soundfx/voice-connecting.wav                     OK 
Testing     heuntold-soundfx/voice-disconnecting.wav                  OK 
Testing     heuntold-soundfx/voice-downloading.wav                    OK 
Testing     heuntold-soundfx/voice-incoming-transmission.wav          OK 
Testing     heuntold-soundfx/voice-loading.wav                        OK 
Testing     heuntold-soundfx/voice-piy.wav                            OK 
Testing     heuntold-soundfx/voice-please-confirm.wav                 OK 
Testing     heuntold-soundfx/voice-pleasehold.wav                     OK 
Testing     heuntold-soundfx/voice-secure.wav                         OK 
Testing     heuntold-soundfx/voice-system-activated.wav               OK 
Testing     heuntold-soundfx/voice-welcome.wav                        OK 
Testing     heuntold-music                                            OK
Testing     heuntold-soundfx                                          OK
All OK loadGameOptions() - loading game options...
 loadGameOptions() - loading skin colors...
loadSkinColors() - [heuntold-skins/heut-default/colors.txt]
 done.
Engine version : heut.engine-0.8.0-rc3.demo [Jul 14 2010.13:48:59]
_checksum: 0

_checksum: 34797


thats all it does after that it just stops and goes back to the prompt

---

### Post by mrobert on 2010-09-03
Hi,

Could you try re-downloading it?
It could be corrupted data in the download.

---

### Post by angelsinraver on 2010-09-07
unfortunately same thing happens

---

### Post by mrobert on 2010-09-13
I am continuing to look into this.

---

### Post by Shazzner on 2010-09-14
Same problem :(

---

### Post by rpdillon on 2010-09-20
Same problem here.  32-bit version of the demo.  I saw this on Steam on my Mac, and thought it would be nice to have on my Linux laptop, so I wanted to d/l the demo and see if it worked correctly with my Dvorak keyboard (lots of games don't).  Alas, it verifies all the archives, but then simply exits.  Any help appreciated.

---

### Post by mrobert on 2010-09-21
I think there is something wrong with the latest demo.
We are working to update this right away.

---

### Post by angelsinraver on 2010-09-22
well let us know when you figure it out, i would love to try this game, my friend highly recommended it

---

### Post by mrobert on 2010-09-23
Will do so.
Feel free to try the PC/Mac demo in the meanwhile, if you have one of those OS-es.

---

### Post by navets on 2010-09-23
Downloaded the Hacker evolution demo ... 
But i have the bug can't write the "_" anyone have the same problem?? 
i suppose to write "_" but i can't write it ..
Or is it because it's demo ?

---

### Post by navets on 2010-09-23
sry i haven't see to the end of post ..It's alread solved ? Looks like a lot of you have the same problem .. I will download the demo again .. Thx

---

### Post by Fervid on 2010-09-23
I hope you guys get the issues worked out. I loved the first Hacker Evolution. According to the reviews this one blows the original out of the water.

---

### Post by mrobert on 2010-09-23
@navets: Did you sort it out?
@Fervid: Did you get to try the game?

---

### Post by Ragnarok_91 on 2010-12-31
Hey everyone, I just joined the forum here and am a tad new to Ubuntu (and any Linux flavor for that matter)...but I first off wanna say I'm glad I became part of this forum and I actually really like Ubuntu.

However, I have a dual boot (Vista and Ubuntu) and just started using Ubuntu more.
I stumbled across the game: Hacker Evolution: Untold and wanted to know exactly how to install it on Ubuntu. I'm not sure if I wanna buy it just yet but can I upgrade the demo to the full version or do I have to buy it and re-download?

just curious about that, but I would like to know how to install it if anyone can help me out

---

### Post by Drakx on 2010-12-31
> **Ragnarok_91 said:**
> Hey everyone, I just joined the forum here and am a tad new to Ubuntu (and any Linux flavor for that matter)...but I first off wanna say I'm glad I became part of this forum and I actually really like Ubuntu.

However, I have a dual boot (Vista and Ubuntu) and just started using Ubuntu more.
I stumbled across the game: Hacker Evolution: Untold and wanted to know exactly how to install it on Ubuntu. I'm not sure if I wanna buy it just yet but can I upgrade the demo to the full version or do I have to buy it and re-download?

just curious about that, but I would like to know how to install it if anyone can help me out

Welcome to Linux and Ubuntu!, this is rather easy first when you have downloaded the zip locate it, in my case I found it in my Downloads folder, right click it choose extract here once thats finished. You will find a new folder called 

heuntold-demo-2.2-rc3-5-g48e8f7a-linux-x86_64 (this assumes your using x64) inside there find hacker-evolution (this is already setup so that you don't have to change its permissions) just double click it and choose run.

Then it should just start the game for you :)

Sorry about the step by step but i've been told by many i assume too much when giving instructions to people ;)

EDIT: for some reason that little script wont work so locate the bin folder and find a file called hacker-evolution.

EDIT again:

[IMG]http://img.photobucket.com/albums/v621/Drakx/justNotright.png[/IMG]

I take it thats not right? also a suggestion would be to allow users the choose what ress they run in window mode? oh and that back ground is the same full screen also.

---

### Post by mrobert on 2011-01-02
@Drakx: Thanks for the quick help

@Ragnarok_91: If you need any assistance, please let me know. As the developer of the game, I can assist you easily.

---

### Post by DijitalX on 2011-01-04
Has anyone gotten this to work?  i downloaded (twice) and tried running in terminal with sudo ./hacker-evolution but i just get the string of output (no errors visible) and then back to the command prompt.  :(

---

### Post by mrobert on 2011-01-05
@DijitalX:

Get in touch with us here:
[http://www.exosyphen.com/page_contact.html](http://www.exosyphen.com/page_contact.html)

and we will sort this out.

---

### Post by William Dojinn on 2011-05-18
Have to say the Demo on the Cr-48 runs fairly well (had the same 'could not run' problem stated earlier in thread... and was sorted out easy enough
Only getting 27fps so the mouse runs a little jittery, but other than that game's fairly responsive. Gonna want to see if I can set aside money for the developer version (friend of mine might want a look at the code, see if anything can be done to tweak this or that.)

Final note: As always the music is appropriate and, while not distracting while in the middle of things, a welcome addition to my playlist.

Looking forward to hand over my money.

---

### Post by mrobert on 2011-05-19
@William Dojinn:

Thank you for the feedback.
Keep an eye out on [http://www.HackerEvolutionDuality.com](http://www.HackerEvolutionDuality.com) - it will have a native Linux version from day one.

As for the developer edition, get in touch with me. I can offer you at least a 50% discount on that.

---

