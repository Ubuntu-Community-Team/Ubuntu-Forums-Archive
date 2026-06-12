---
title: "xmame not working...."
date: 2006-03-07
forum: Gaming &amp; Leisure
---

### Post by riwa on 2006-03-07
It just doesn't start... I get the following message:

```

$ xmame
info: trying to parse: /etc/xmame/xmamerc
error: /etc/xmame/xmamerc(71): unknown option joyusb-calibrate, ignoring line
info: trying to parse: /home/riwa/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /home/riwa/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /home/riwa/.xmame/rc/pacmanrc
I386 joystick interface initialization...
OSD: Warning: No joysticks found disabling joystick support
loading rom 0: pacman.6e
loading rom 1: pacman.6f
loading rom 2: pacman.6h
loading rom 3: pacman.6j
loading rom 4: pacman.5e
loading rom 5: pacman.5f
loading rom 6: 82s123.7f
loading rom 7: 82s126.4a
loading rom 8: 82s126.1m
loading rom 9: 82s126.3m
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.

```

Doesn't matter if I start a file or not.. Same output but different files...

What do do? [step-by-step explanation appreciated]

/Richard

---

### Post by patbuntu on 2006-03-07
do you have the files listed (eg pacman.6e etc) on your system?  Could just be a path issue.

-Pat

---

### Post by Master Shake on 2006-03-08
If you run xmame without specifying a game rom, it will try to run pac-man by default.  What exactly are you typing in?

Also, there is a great frontend for xmame (I forget the name atm)  you may want to try using that.

---

### Post by daveg on 2006-03-09
[QUOTE=riwa]It just doesn't start... I get the following message:

```

$ xmame
<SNIP>

```

Doesn't matter if I start a file or not.. Same output but different files...

What do do? [step-by-step explanation appreciated]

/Richard[/QUOTE]

Richard, the xmame program isn't also a frontend like the mame32 program on Windows.

You best bet is to install [GXMame]("http://gxmame.sf.net") which is very similiar to mame32. 
[LIST=1]
[*]Download the .deb for it from [here]("http://prdownloads.sourceforge.net/gxmame/gxmame_0.35beta2-1_i386.deb?download")
[*]Install the .deb. From the terminal, goto the directory that you downloaded the .deb file to, then: sudo dpkg -i gxmame_0.35beta2-1_i386.deb
[*]Run gxmame. It'll show up in Applications -> Games -> GXMame
[*]Make sure you configure GXMame to correct paths to your ROMs, etc.
[/LIST]

---

### Post by Mr Green on 2006-03-09
[QUOTE=daveg]Richard, the xmame program isn't also a frontend like the mame32 program on Windows.

You best bet is to install [GXMame]("http://gxmame.sf.net") which is very similiar to mame32. 
[LIST=1]
[*]Download the .deb for it from [here]("http://prdownloads.sourceforge.net/gxmame/gxmame_0.35beta2-1_i386.deb?download")
[*]Install the .deb. From the terminal, goto the directory that you downloaded the .deb file to, then: sudo dpkg -i gxmame_0.35beta2-1_i386.deb
[*]Run gxmame. It'll show up in Applications -> Games -> GXMame
[*]Make sure you configure GXMame to correct paths to your ROMs, etc.
[/LIST][/QUOTE]

Well that worked like a charm, but how do I locate some rom files? Are they free, or do I need to purchase them at Pirate Bay?

---

### Post by daveg on 2006-03-09
[QUOTE=Mr Green]Well that worked like a charm, but how do I locate some rom files? Are they free, or do I need to purchase them at Pirate Bay?[/QUOTE]They're not free and I'd recommend against purchasing them from people on Pirate Bay.

Two (but still illegal) ways of obtaining them are:

[LIST=1]
[*]Get them from [here]("http://www.freemameroms.com/web/burners.php")
[*]or download from [here]("http://www.pleasuredome.org.uk/")
[/LIST]

If you want to just get a couple now though, have a look in the newsgroup alt.binaries.emulators.mame.

---

### Post by leech on 2006-03-09
Technically speaking, if you own the arcade machine that the rom is for it's not illegal.  Or at least some think so.  I do kind of find it funny that these roms roam around the internet, and yet you don't really see arcade manufacturers going around and sewing every website like you see the MPAA or the RIAA.  I think in general it's just because they're a bunch of [expletives].  

Really, if you think about it, the world is not going to end if you happen to download and play the original arcade versions of Pac-Man or Donkey Kong.  It's not like these are selling anymore.  Granted there are always those CD collection of "Classic games" that come out every so often.  But these are all using some sort of emulation technology that usually the open source community creates.  So I think these companies should just release a lot of these out into the wild to repay for the hard work the Mame and other emulator writers have spent creating the software.

Leech

---

### Post by takayuki on 2006-03-12
here's a good link to help with the controls and such once you get the game going.

[http://www.mame.net/mamefaq.html#t04](http://www.mame.net/mamefaq.html#t04)

5 = drop one coin in the "machine"
1 = play button
tab = shows the setup menu for the game.  great if you want to see where the keyboard controls are for each game. 

takayuki

---

### Post by mpeters13 on 2006-03-13
I'm having my own xmame issues.  I've downloaded xmame, xmess, xmame-common and xmess-common, but cannot get anything to install with dpkg. It seems that when I try to install xmess, I'm told to install xmess-common first, only to be instructed to install xmess.  The xmame files do the same. I'm going nuts here. I'm in dependency purgatory and would really like someone to pull me out xD. Note: I have the breezy backports, universe and multiverse repositories available to synaptic, but when I sudo apt-get install xmame-common, it cannot find anything. I've tried an array for wildcard combinations but nothing.

Files I'm working with:
xmame-common_0.86-3_all.deb
xmame-x_0.86-3_i386.deb
xmame-gl_0.86-3_i386.deb
xmame-tools_0.86-3_i386.deb
xmess-x_0.86-3_i386.deb
xmess-common_0.86-3_all.deb
gxmame_0.35beta2-1_i386.deb

(AS you can see I was desperate enough to even try different versions of xmame to see if it would install...)
Any help is appreciated.

---

### Post by daveg on 2006-03-14
[QUOTE=mpeters13]I'm having my own xmame issues.  I've downloaded xmame, xmess, xmame-common and xmess-common, but cannot get anything to install with dpkg. It seems that when I try to install xmess, I'm told to install xmess-common first, only to be instructed to install xmess.  The xmame files do the same. I'm going nuts here. I'm in dependency purgatory and would really like someone to pull me out xD. Note: I have the breezy backports, universe and multiverse repositories available to synaptic, but when I sudo apt-get install xmame-common, it cannot find anything. I've tried an array for wildcard combinations but nothing.[/QUOTE]

Can you paste in your /etc/apt/sources.list here? You should just be able to do a sudo apt-get install xmame-common without having to manually download the .debs as its in the multiverse repository.

---

### Post by riwa on 2006-03-16
Well, that's exactly the info i need except that the games doesn't launch neither. Everything seems fine but when all the modules are loaded i get an empty pop-up with a big stop sign on it. I'm trying to run my own games. By the way, how do I download the games on that humoungous list??

/Richard

---

### Post by ToiletDuck on 2006-03-16
Riwa, 

 Are you running GXmame for the first time? If i remember you need to click yes to let it audit the roms. Then after you obtain some roms (This is what i do) Hit the refresh button. Also to make it easy click Available Roms on the left hand side. As far as roms go ppl are weary of giving out direct address. But Google is our friend. Send me a pm so i know you got this and i can help you further.

---

### Post by rich_phoenix on 2008-03-11
just doesn't make much sense

Installed xmame (common, svga, x11 and via another attempt sdl) and downloaded (a) rom (contained several files)

#1. when I linked the file up with xmame and clicked on it...Voila! game loads. The only problem is that I couldn't define keys and it was in in a small 2XX x 2XX window.

#2. thinking that a frontend might help with this, I downloaded and attempted Kxmame (before I found Gxmame which I'd assume would work better with Gnome). well, I tried to audit roms, and build....nothing...was told that the directory I entered was not a rom (umm...duh!)...so catering to the anti-logic, I thought "ok, it asked for a directory that it wants to execute as a rom? fine..I'll give it a rom file as a directory name"..no go...try as I might it did/could not see the roms (and I had several d/l'd by then)

It seems to have alot of areas....and it somehow figures out how to use xmame as an application to run the rom, but if I tell it to do so at the command line (to be able to mod fullscreen and key setup)...forget it..

also, something else doesn't make sense...how can it load roms without finding them?! I go into the directory that the roms are...type 'xmame' by itself and it 'loads' pacman roms that I don't have.....then after it says it's "done' loading them...tells me it can't find them

BTW- when I do specify a rom, it 'loads' supposedly loads the rom and says 'done' before stating it was NOT FOUND....reminds me of when I get paid....I load my wallet with cash and later, when I'm asked for change....change not found! :D

---

### Post by Lux Perpetua on 2008-03-11
To load a rom from the current directory, the command is ```
xmame ./name_of_game
```Don't forget the "./".

I don't use kxmame now, but I have before, and if memory serves, you have to tell it first where to find your roms by selecting "add rom directory" or something from the menu.

---

