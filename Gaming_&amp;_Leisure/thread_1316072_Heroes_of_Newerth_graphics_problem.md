---
title: "Heroes of Newerth graphics problem"
date: 2009-11-05
forum: Gaming &amp; Leisure
---

### Post by TaoBoogie on 2009-11-05
Hi

My system:
Karmic Koala 9.10 Gnome 2.28.1 (fully updated)
AMD Athlon 64 X2 Dual Core Processor 4600+
4 gig RAM
GeForce 8500GT

The install seemed to go ok I let it install to the defalt location suggested which was
/home/name/HoN
I tried starting the game through Applications/Games/Heroes of Newerth/
The result is a screen full  of large black/white squares and stripes and arrow cursor and nothing else. I can't close the game down so I'm going to have to restart the computer and try again.
I have Compiz running with the cube and Cario Dock.
Am I doing anything wrong and what would you suggest I do to get the game up and running?
I have also posted this problem to the HoN Forums but have not yet had a reply.
Cheers

---

### Post by Vadi on 2009-11-05
Make sure that you have installed the recommended nvidia drivers from system - administration - hardware drivers.

---

### Post by edin9 on 2009-11-05
Disable Compiz and turn off Cairo-Dock. See if that helps.

---

### Post by Vadi on 2009-11-05
That shouldn't be the problem, as I on 8600gt play with compiz fine.

---

### Post by TaoBoogie on 2009-11-05
Thank you Vadi and edin9

Just checked and I am already using the NVIDIA "accelerated graphics driver (version 185) which is marked as "recommended" in Hardware drivers.

Shall I try disabling some visual effects through Preferences > Appearance perhaps or Compiz? If my eye candy addiction will allow me :)

---

### Post by edin9 on 2009-11-05
Disable all effects, and certainly disable Cairo-Dock.

---

### Post by TaoBoogie on 2009-11-05
I disabled Cario-Dock first and tested.
Same as before, two large black and white squares at first then a screen full of B/W blocks I could just make out the login text at the top. But...This time I had sound.

Tried again with Cario dock and Compiz disabled but this produced exactly the same results as above but this time I had no way of exiting the game even ctrl+alt+delete did not give me the usual dialogue box.

---

### Post by TaoBoogie on 2009-11-05
One thing I have to remind myself and others. This game is in beta and is still being tested. 

I am still open to suggestions though :)
I wonder how many people have actually got the game working?

---

### Post by joeelmex on 2009-11-05
Game runs without issues at all for me, but I use the nvidia drivers from Nvidias web site not the ones in the Ubuntu respository.

---

### Post by edin9 on 2009-11-05
> **TaoBoogie said:**
> One thing I have to remind myself and others. This game is in beta and is still being tested. 

I am still open to suggestions though :)
I wonder how many people have actually got the game working?

I do, on nVIDIA, for *ages* :P

---

### Post by TaoBoogie on 2009-11-06
Well then, I'm at a loss for the moment. I can not think of what else to do. The downloaded "HoNClient-0.1.41.sh" file appears to be solid. Ran it and accepted all default install locations. It's as if there are no textures or GUI's loaded.
Hmmm
The rest of my machine is running smoothly I don't really want to jeopardise that by messing up on an update from NVidia that isn't supported by Ubuntu.

The game is not listed in "Ubuntu Software Centre" so I assume I will have to uninstall it via "uninstall-HoN.sh" in the install folder.

---

### Post by Vadi on 2009-11-06
Try posting in the HoN support forums, then. They have a dedicated Linux programmer who'll help you.

(not that I understand why didn't you post there to begin with)

---

### Post by TaoBoogie on 2009-11-06
> **TaoBoogie said:**
> Hi


I have also posted this problem to the HoN Forums but have not yet had a reply.
Cheers

Hello Vadi
I did say this in my first post. :)

Actually I have just checked back at the HoN support forum and one suggestion I got was to start the game from the console. So I know how to navigate to the HoN folder but I do not know the command to start the game from there. I did try > ged@ged-desktop:~/HoN$ hon-x86
hon-x86: command not found

Cheers

---

### Post by Vadi on 2009-11-06
You need to do

./hon-x86

./ implying that the program is in the folder you're currently in.

---

### Post by TaoBoogie on 2009-11-06
Ahhh 
"./" that's the fellah I was looking for.
Unfortunatel;y still white and black blocks
Thanks

---

### Post by Vadi on 2009-11-06
That doesn't fix it... it's supposed to say something in the terminal which you show to people.

---

### Post by canseco on 2009-11-06
I play this game too, and got no probs, but i use nvidia driver from website, as joeelmex.
Anyway, Canonical doesn't give support for privative drivers, source it not avalaible, :) 

Mini-howto to install nvidia driver from web:

Disable 185 driver on Hardware drivers
Download drivers from nvidia website
Crtl+Alt+F1 (Opens terminal without X)
sudo service kdm stop (stops X)
./NVIDIA-Linux-x86-190.42-pkg1.run (yes, yes, yes)
sudo service kdm start

And, if you can, copy&paste what terminal says when launching game.

---

### Post by Vadi on 2009-11-06
You can just install it from the PPA easier: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

if you really want them

---

### Post by TaoBoogie on 2009-11-06
Here is a screen shot of what I see when starting the game 
[Here ](http://digitao.co.uk/images/hon.png)]

When I tried to run from the terminal this is what I see in the window after I have to "Kill" the game to close it down

> ged@ged-desktop:~/HoN$ ./hon-x86
warning: The VAD has been replaced by a hack pending a complete rewrite

---

### Post by edin9 on 2009-11-06
Have you added xorg edgers PPA?

---

### Post by TaoBoogie on 2009-11-06
> **edin9 said:**
> Have you added xorg edgers PPA?

Ah!
I have no idea what that is or how to do it.

---

### Post by Vadi on 2009-11-06
(08:24:45 PM) S2Slacker: probably worth deleting ~./Heroes of Newerth in case something got screwed up there

---

### Post by TaoBoogie on 2009-11-06
I've found the console.log and crash.log in 
".Heroes of Newerth/game/"
From what I can tell in the console.log there are a lot of "Invalid file type" entries.
The file is 124kb and a little to long to post here I think.
Here is a link to the file:
[console.log](http://digitao.co.uk/hello/console.log)


The HoN support Forums are down at the moment.

I did delete the .Heroes of Newerth/ directory before restating so this is freshly written.

---

### Post by Vadi on 2009-11-07
Try reinstalling then. All your textures are corrupted and can't be loaded, as it says.

---

### Post by TaoBoogie on 2009-11-07
That does seem to be the case Vadi.
I think the whole package might need to be re-installed so I'm going to try to un-install first. I can't do that via Software Centre or Synaptic as it does not show up there. I did notice a file called "uninstall-HoN.sh" in the "/home/ged/HoN" folder, so perhaps I can do that from there?
I'm not at all sure what the commands will be to do that but I'll have a try.
Thanks

---

### Post by TaoBoogie on 2009-11-07
I cannot find a way to do an un-install so as recommended in quite a few places I just deleted the HoN and ./Heores of Newerth folders.
Then I tried to install again ```
ged@ged-desktop:~$ sh HoNClient-0.1.41.sh

```
I left it to install to the default locations and I still get only the Black/white squares

How do I check the MD sum to see if the package is not currupt somehow?

---

### Post by Vadi on 2009-11-07
md5sum HoNClient-0.1.41.sh

---

### Post by TaoBoogie on 2009-11-07
Thanks for sticking with me Vadi

Checked the md5sum and got this:
> ged@ged-desktop:~$ md5sum HoNClient-0.1.41.sh
08d613d7fc3eefaa8ef5ced3daee6ab6  HoNClient-0.1.41.sh

On the first post of the [ HoN linux support thread](http://forums.heroesofnewerth.com/showthread.php?t=1059)
 they give:
"9426e3caa948ff85f21ec70f7fe7fdf5 HoNClient-0.1.41.sh"
This does not look good.

---

### Post by Vadi on 2009-11-07
Yeah, so re-download your installer.

---

### Post by TaoBoogie on 2009-11-07
Crikey!
Last time that took six hours!
Ah well you've got to do what you've got to do. See you on the bright side when I hopefully DL a complete copy.

BTW How do I uninstall the game?

---

### Post by TaoBoogie on 2009-11-07
Downloaded another copy (did not take too long) and this time the md5sum checked out.

Installation went without a hitch installing to the suggested locations.

On first starting the game through Applications-Games_Heroes of Newerth. I logged in and an update started about 50MB but right at the very end of the update it hung on an image of a black loader bar, this locked my system too.
So I rebooted, started the game, logged in, the same update started again but this time it completed.

So it looks like the game is all set to play, which is a result.
Now I have not been able to play yet as I could not find a game to join. When I tried to perform a search for an available game the screen froze locking me out so after a few minutes I switched desktop and killed the game from the context menu in Cairo dock.

I will mark this thread as solved soon, I just want to actually get into the game itself before I do that.

---

### Post by TaoBoogie on 2009-11-07
The problem at the moment is that as soon as I find a server to join and try to join it the loading bar gets to about 90% then crashes and I get to stare at my desktop again.
This has happened about a dozen times so far i have not been able to join a server and play the game.

So although the graphics problem has been fixed and I will mark the thread to reflect this. I still cannot play the game.
 I can play Savage 2 on-line without a problem

---

### Post by TaoBoogie on 2009-11-07
On a whim, I decided to un-install or should I say delete the folders "HoN" and ".Heroes of Newerth" I then went for a new install started the game and let it update. This failed the first time right at the end of the update install leaving me with a black screen and a white progress bar.

I had to force a restart of the computer then let the game update again and this time the update was successful and I could join a server.

I played my fist game just now and (fingers crossed) everything seems to be working as it should. I'll have to go and read up on game play and stratagy now and practice. Thanks for the help.

My game character name is **Tecumseh**

---

### Post by Vadi on 2009-11-07
Oh, glad you got it working.

I hope your skin is thick enough to weather the community and desire to become good at the came strong - some people can get *really* good at the game.

Here's a series of vids of a high-level competitive clan match to watch: [http://www.youtube.com/watch?v=8Y9xrXmS1io](http://www.youtube.com/watch?v=8Y9xrXmS1io)

---

### Post by TaoBoogie on 2009-11-08
Thank you Vadi, from what little I have seen and heard of the gameplay I realise I have a lot to learn.I have also been playing Savage 2 which I think can give me a feel for HoN.
I'll have session with those videos to see what I'm up against.

---

### Post by henz103 on 2009-11-08
Works good here, (Alt + F9) to minimize game.

Pentium 4
Geforce 6800 GS
Ubuntu 9.10
Nvidia accelerated graphics driver (version 185) [Recommended]

2 Bets keys:
fq5wcfm73wokhpt

aisx4qu4a6z2hy9

Have fun :)

---

### Post by 10dollarNOOBIE on 2010-03-22
i already installed heroes of newerth but when im already playing the whole map is black  and i cant see anything... 

My Ubuntu 9.10 is fully updated, do i need some graphic drivers or i just need some repositories? i tried to install nvidia (185) but my HON wont start anymore.. ive installed HON 1st before nvidia fyi.
heres my video card model:
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

please help im a begginer in linux and im starting to like ubuntu than windows ;)[ATTACH]151122[/ATTACH] in vista it runs smoothly so i think i just need something on my ubuntu :)

---

