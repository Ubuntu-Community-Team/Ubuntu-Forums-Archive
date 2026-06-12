---
title: "Oh bother, ...another Mame post...from a Linux newbie"
date: 2011-04-20
forum: Gaming &amp; Leisure
---

### Post by H2o Buffalo on 2011-04-20
[SIZE=2]Hi everybody,

I have gotten totally fed up with Bill and Steve's so called Operating Systems[/SIZE].  Since Bill decided that XP will no longer be supported and I should pay  him more money to buy his new buggy expensive unsecure resource hog of  an os. AAK! enough ranting. Plunge taken. I am using ubuntu lucid lynx  for my home built mame arcade machine. I am very new to the linux life  so I am having some teething issues.

My test machine self  installed GMAMEUI and seems to work fine. The arcade computer seems to  work but when I launch the rom it says the roms cannot be found "The  following ROMs were not found:
a1 NOT FOUND
a3 NOT FOUND
b1 NOT FOUND
b3 NOT FOUND
b5 NOT FOUND
bd-06.1l NOT FOUND
bd-07.4a NOT FOUND
bd-08.5a NOT FOUND
bd-09.8a NOT FOUND
bd-10.9a NOT FOUND
bd01.8j NOT FOUND
bd02.9j NOT FOUND
bd03.11k NOT FOUND
bd04.11l NOT FOUND
blkdrgon.10e NOT FOUND
blkdrgon.5b NOT FOUND
blkdrgon.6e NOT FOUND
blkdrgon.9b NOT FOUND
blkdrgon.9e NOT FOUND
It  finds them just fine in the audit, and I know the rom path and mame  path are correct. the roms are the same on both computers.

I have  tried different versions of mame and it only got worse as they would  not be recognized by the registory ..(still getting used to linux ;)and  would not extract or install...

Friends, penguins, please grant me the boon of your wisdom that I may enjoy Mame once again.

Thanks, 
H2o Buffalo

---

### Post by disturbedite on 2011-04-20
one thing to NEVER do with mame & roms is mix & match versions. you must use the same version romset & mame (currently at 0.142).
if you update one, you must update the other.
you probably are using either different versions of the aforementioned or the wrong (version) dats for your audit.
oh, and if you're not, use mame not xmame.

---

### Post by mips on 2011-04-21
What ^^ said.

Also install QMC2 and try to launch the game with it and see what happens.

---

### Post by H2o Buffalo on 2011-04-21
Hmm,

I tried to uninstall mame from the self installing ubuntu menu and It does not seem to actually remove it. It found the mame file or something like it that I sent to the recycle bin. gotta figure this out. 

How do I completely remove apps installed through the Ubuntu menu so I can re-install and try again.


Any other Ideas?

Thanks,

H2o Buffalo

---

### Post by mips on 2011-04-21
> **H2o Buffalo said:**
> 
How do I completely remove apps installed through the Ubuntu menu so I can re-install and try again.


You can use Synaptic (System->Administration->Synaptic Package Manager) or you can do it from the terminal sudo apt-get remove/purge <package-name>, sudo apt-get --help for all options.

---

### Post by H2o Buffalo on 2011-04-21
Hey! Synaptic! that works.

Thanks, It would be cool if there was a working tutorial for new linux/ ubuntu users that was well shown and narrated.  so New-Bees like myself could look like Real users when we show off our non windows machines. Like I used to do with my Amiga ;)

Thanks for the help.

H2o Buffalo

---

### Post by mips on 2011-04-21
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by H2o Buffalo on 2011-04-23
[SIZE=4]PROBLEM SOLVED![/SIZE]

Ok, here was the issue. In the guimame settings toolbar there is an option to use mame default settings. Do not select this option. I believe that by using mame's propriatary settings it will not use the specified path for the roms after mame launches. Thatis why the audit finds the roms but then it would not find them when mame launched and used it's default paths for the roms.

I think this was the problem. I discovered this after a re-install (I know bad windows user habit sheesh) and after staring at the mame gui off and on for a week I remembered that setting and compared it to the new umbutu machine's settings. Eureka! 

I hope this helps other New Beans whomay have Mame trouble. Everything works perfectly now. 

Thanks for the link to understanding Linux/Umbutu they were instrumental to my Success.

H2o Buffalo

---

### Post by mips on 2011-04-24
When gmameui breaks in future which it seems to do at regular intervals rather remove it and install QMC2.

---

### Post by H2o Buffalo on 2011-04-25
Thanks Mips (million instructions per second?...)

I have a few more problems. 

1: I have a 19" lcd monitor that rotates 90deg for optimal vertical viewing pleasure. For some reason I cannot get the rotate options to work with Guimame. The options are there but no rotation actually happens. anybody else have this problem?

2: When I was running microsoft windows xp (haawk!...Ptooey!) mame was fluidly smooth using 3d accelleration. Now it seems even with the same hardware it only displays around 25 fps. open gl enabled
and full screen.

3: None of the screen effects are being displayed. I cannot get scan lines or grid effects to show.  I like these as they more closely resemble my dead CRT monitor.

Any knowledge or advise is appreciated.

H2o Buffalo ;)

---

### Post by mips on 2011-04-25
That and the MIPS architecture.

1&2 works fine when I use QMC2. I have not tried 3 so can't comment on it.

You persist in using gmameui when there is something better, choice is yours though.

---

### Post by H2o Buffalo on 2011-04-25
Right then, QMC2 repository added and Qmc2 installed. It even added the launcher to the menu for me. Good thing, as I am still learning how to do this myself. I try to run it and nothing happens...hmm Do i have to remove guimameeu 
sigh ...what now...going back to try looking for help again.
H2o Buffalo

---

### Post by mips on 2011-04-26
> **H2o Buffalo said:**
> Right then, QMC2 repository added and Qmc2 installed. It even added the launcher to the menu for me. Good thing, as I am still learning how to do this myself. I try to run it and nothing happens...hmm **Do i have to remove guimameeu **
sigh ...what now...going back to try looking for help again.
H2o Buffalo

What happens when you run **qmc2-sdlmame** from a terminal?
Have you specified all your paths? See attached image, the blacked out part is your username.


No, you can leave it installed. Install sdlmame and try qmc2 again.

---

