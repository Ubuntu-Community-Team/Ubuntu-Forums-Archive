---
title: "I'm going back to Windows XP"
date: 2005-09-16
forum: Desktop Environments
---

### Post by jeffreyvergara.NET on 2005-09-16
Im really disappointed with my experience in Ubuntu, I really like to throw away windows but it wont let me. this is my first post after i reformat my pc and installed Win XP. I really like Ubuntu but I just encountered too much problem in version 5.04 which I think you called the stable version?

I was using my UBuntu normally, made a full system update (the red icon beside the volume control on the upper right corner) restarted my PC and it went fine. and do my usual web browsing. I have problem with FireFox 1.0.6, it just suddenly drop without popping any error... so I need to reboot again, or reintall it. then i downloaded an avi file, leave my PC for awhile, after a few hours, I watched the movie, it's still ok.... but when I restarted the PC, I was able to login.... but in command prompt... i tried to restart again and again but same thing happend... I didnt change anything before It happend. So thats time I went back to windows....  to download new Ubuntu 5.10.... :roll:  :roll:  :roll: 

just a question.... is installing the Unbuntu 5.10 Preview as my main OS recommended? or just stay with 5.04?

if I stay with version 5.04, do you recommend that I do a system update? I think my problems only happend after I updated my system..

---

### Post by lao_V on 2005-09-16
[QUOTE=jeffreyvergara.NET]I really like Ubuntu but I just encountered too much problem in version 5.04 which I think you called the stable version?
...........
just a question.... is installing the Unbuntu 5.10 Preview as my main OS recommended? or just stay with 5.04?
[/QUOTE]

So are you expecting a beta/preview release - 5.10 to be more stable then Hoary 5.04 stable release??

---

### Post by rmjokers on 2005-09-16
It sounds like when you did the update, a new version of x.org was downloaded that somehow did not work with your old configuration file.  Thus, when you rebooted, the graphical login manager failed to load and you were dropped back to the command line.  If you log in and run

sudo dpkg-reconfigure xserver-xorg

You can create a new configuration file for the X server and it should work again.  The problem here is obvious:  How is a new user, particularly someone not familiar with Linux, supposed to know to do this?  It boggles the mind that configuring the X server is STILL this difficult.  Why it doesnt have a more reasonable failure mode (VESA VGA or framebuffer) when the primary configuration fails is beyond me.  People should never be FORCED to log in at the command line unless they dont have an X server or their graphics card is broken.

---

### Post by earobinson on 2005-09-16
bye!

---

### Post by Daniel G. Taylor on 2005-09-16
Okay, so I assume Firefox was crashing on you. Did you have any extensions installed? Was firefox updated during the system update? Did it always crash on the same page, when you hit a particular button, or randomly? Is there any output after the crash when you run it from a terminal?

I'm assuming by your other comments that X.org won't start (the grahpical interface server component), but that you can log in to a terminal. Is there any error output? When X.org crashes it usually leaves a log in /var/log/ that you can check out. What kind of graphics card do you have? Have you manually modified /etc/X11/xorg.conf? 

I wouldn't recommend Breezy for another few weeks. Just wait for the final release and try it then. If you want you could check it out by [grabbing a live cd](http://releases.ubuntu.com/breezy/) and testing it without installing to your system. Note that the preview release has known bugs though.

---

### Post by lao_V on 2005-09-16
[QUOTE=earobinson]bye![/QUOTE]

I don't understand the point of this comment.

---

### Post by void_false on 2005-09-16
bye. happy windoze "using"

---

### Post by KingBahamut on 2005-09-16
[QUOTE=earobinson]bye![/QUOTE]

EAR try not to be spiteful please. Specially in a non community forum. 

Mods, can someone grab this prease?

---

### Post by BIGtrouble77 on 2005-09-16
[QUOTE=rmjokers]It sounds like when you did the update, a new version of x.org was downloaded that somehow did not work with your old configuration file.  Thus, when you rebooted, the graphical login manager failed to load and you were dropped back to the command line.  If you log in and run

sudo dpkg-reconfigure xserver-xorg

You can create a new configuration file for the X server and it should work again.  The problem here is obvious:  How is a new user, particularly someone not familiar with Linux, supposed to know to do this?  It boggles the mind that configuring the X server is STILL this difficult.  Why it doesnt have a more reasonable failure mode (VESA VGA or framebuffer) when the primary configuration fails is beyond me.  People should never be FORCED to log in at the command line unless they dont have an X server or their graphics card is broken.[/QUOTE]
 I agree that there should be better utilities to configure x, but windows is hardly any better.  At least when x fails it drops you to a command promt to give you a fighting chance.  Win, on the other hand, will 9 times out of 10 give you a bsod.  Sometimes safemode and 'use last known working configuration' works, but it's like playing russian roulette.  

-BT

---

### Post by jeffreyvergara.NET on 2005-09-16
[QUOTE=BIGtrouble77]I agree that there should be better utilities to configure x, but windows is hardly any better.  At least when x fails it drops you to a command promt to give you a fighting chance.  Win, on the other hand, will 9 times out of 10 give you a bsod.  Sometimes safemode and 'use last known working configuration' works, but it's like playing russian roulette.  

-BT[/QUOTE]
 hello, I aprreciate all your replies. actually I installed windos again to learn more about Ubuntu and Linux without hassle. I've learned manything from you guys... Im getting excited to have my Ubuntu back again.

So... after I install Ubuntu 5.04, is it recommended to make a full system update? (all of the 120++ files) I also noticed that firefox update is not included on the first system update, and it will be available on the second time i run the update.

And when the new Ubuntu version is released, can we get the Upgrade without downloading the Full installation CD?

Thanks guys, im ready now to forget about Windoze. W00t.

---

### Post by grj on 2005-09-16
One more thing. After running the update manager, you do not have to reboot your machine. It is almost never necessary.

---

### Post by jeffreyvergara.NET on 2005-09-16
[QUOTE=grj]One more thing. After running the update manager, you do not have to reboot your machine. It is almost never necessary.[/QUOTE]
 w00t! just installed Ubuntu again. and I was surprised that the first problem I encountered is FireFox... I havnt update my sytem yet so I guess its a FF bug or something... I just visited ubuntuforums.org and ugtech forum, browse a little and then.... it just suddenly crashed without any error. I also noticed that if I click on the FF toolbar(file, edit, etc...), FF crash... I havn't encountered this problem in Windoze...

---

### Post by jeffreyvergara.NET on 2005-09-16
I think the problem with me is that I keep on relying with Windoze, so if I have a problem with Ubuntu, I know there's still a Windoze that i can rely on. But I think, the best way for me to learn more about linux is to forget about Windoze. hehehe...
> the other reason why I went back to Windoze is that I backup my files on my 2nd NTFS HD and converted it to FAT32 so I would not have any problem mounting my FAT32 drive 

anyways, my second problem i encountered is, the gnome toolbar is blank, after I restart my PC because of the other problem in Firefox, so the other solution is to reboot again. is there any shortcut key to execute the "Terminal" so if I encounter this problem again, i just use the shortcut key to use Terminal for: killall gnome-panel?

---

### Post by Turtle.net on 2005-09-17
[QUOTE=jeffreyvergara.NET]I think the problem with me is that I keep on relying with Windoze, so if I have a problem with Ubuntu, I know there's still a Windoze that i can rely on. But I think, the best way for me to learn more about linux is to forget about Windoze. hehehe...
 

anyways, my second problem i encountered is, the gnome toolbar is blank, after I restart my PC because of the other problem in Firefox, so the other solution is to reboot again. is there any shortcut key to execute the "Terminal" so if I encounter this problem again, i just use the shortcut key to use Terminal for: killall gnome-panel?[/QUOTE]
 As it was said previously : do not reboot your PC all the time....
Linux is not like windows, you do not have to reboot to solve 80% of your problems and reinstall to solve the 20% remainings.
I had a lot of problems also then I decided to move from Windows to Linux. I had to learn a lot to be able to install my first linux distro (Gentoo, I personnaly recommend this one if you really want to spend tens of hours to have good installation, and then hundreds of hours to learn how really works a Linux box...for me that's the best way to learn). With Ubuntu everything is much simpler, and stable, but you also have to learn a lot of things to be able to repair your Ubuntu box when its not working properly.

Normally, you can access the terminal just by right-clicking on your desktop.

Try to launch Firefox in a terminal, to see if you have any message when it crashes.

---

### Post by jeffreyvergara.NET on 2005-09-17
i just learned the right-clicking on desktop to access the terminal yesterday and it was a relief, i've also learned commands like killall gnome-panel, and how to install packages and many more things I never dream Im going to learn. i also like the ctrl+alt+backspace... ehehehe... anyways.... i think I'll never go back to window$ ever again... hehehe... Im really excited everytime I use my Ubuntu... cased closed... ^_^

---

### Post by Leif on 2005-09-17
[QUOTE=jeffreyvergara.NET]I think the problem with me is that I keep on relying with Windoze, so if I have a problem with Ubuntu, I know there's still a Windoze that i can rely on. But I think, the best way for me to learn more about linux is to forget about Windoze. hehehe...[/QUOTE]

necessity is the mother of invention  :) you're right that you learn linux much faster if you forget that you can reboot to xp. that way you stick with it and find the solution, which is not that complicated most of the time.

---

