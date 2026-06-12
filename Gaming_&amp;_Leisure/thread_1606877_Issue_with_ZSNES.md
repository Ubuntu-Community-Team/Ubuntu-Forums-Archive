---
title: "Issue with ZSNES"
date: 2010-10-27
forum: Gaming &amp; Leisure
---

### Post by KBD20 on 2010-10-27
Hi, I have used ZSNES on and off in the past, but each time I have used it, even though I set a save directory etc. Games (roms) I play don't save (when they normally should), no save files are created in my "save" directory I set. Have others encountered this problem? and if so is there a way to fix this?

Thanks in advance

---

### Post by dfreer on 2010-10-27
I think by default it saves in ~/.zsnes/, have you looked in there?

---

### Post by mister_playboy on 2010-10-27
Just to clarify, the.zsnes folder is a hidden folder and isn't normally displayed.  The keyboard shortcut to display hidden folders is CRTL+. in Dolphin, but I can't remember what it is in Nautilus... perhaps someone else can chime in.

---

### Post by Quadunit404 on 2010-10-27
> **mister_playboy said:**
> Just to clarify, the.zsnes folder is a hidden folder and isn't normally displayed.  The keyboard shortcut to display hidden folders is CRTL+. in Dolphin, but I can't remember what it is in Nautilus... perhaps someone else can chime in.

Ctrl + h in Nautilus ;-)

---

### Post by KBD20 on 2010-10-27
> **dfreer said:**
> I think by default it saves in ~/.zsnes/, have you looked in there?

I have looked in there, but no saves are stored there as I had set a custom directory for the saves, however in the directory I have set the games wont create any save files. This problem has occurred on more than one version of Ubuntu (8.04 - 10.10).

---

### Post by ericdn on 2010-10-27
Wow - I had no idea ZSNES works in Ubuntu!  Now I'm happy!! :)

---

### Post by dfreer on 2010-10-27
Did you have any spaces or weird characters in your path, and can you read/write to the save directory? Also make sure the capitalization is correct as linux is case sensitive. Try removing the custom save path and see if they then save to ~/.zsnes if nothing else.

---

### Post by mister_playboy on 2010-10-27
> **ericdn said:**
> Wow - I had no idea ZSNES works in Ubuntu!  Now I'm happy!! :)

I really recommend bsnes over zsnes if your computer meets the minimum requirements.  Check out the leftmost link in dfreer's signature.

Deb packages for the current version of bsnes can be found here: [http://tukuyomi.kuro-hitsuji.net/stuff/bsnes/deb/bsnes_v072/](http://tukuyomi.kuro-hitsuji.net/stuff/bsnes/deb/bsnes_v072/)

---

### Post by ericdn on 2010-10-27
> **mister_playboy said:**
> I really recommend bsnes over zsnes if your computer meets the minimum requirements.

Good point.  However, I've been using ZSNES since my college days, I'm very comfortable with it, and it does everything I need to.  I'll take a look at BSNES, though, and see which one I like better.

---

### Post by mister_playboy on 2010-10-28
Changes in the bsnes project have made it a bit hard to compile on Ubuntu.  If you try to compile yourself and you have trouble, try this:

```
cd bsnes
make -j3 compiler=gcc ui=ui-qt profile=performance
sudo make install
```

For the usual use case (dual core computer, use of the performance core) this will get you the binary you want.  Then you can create a launcher and point it at /usr/bin/bsnes

---

### Post by freesparks on 2010-10-28
Hello all,

  Seems as though you guys are very familiar with the install process of running ZSNES Emulator, I have version 1.51 installed and was wondering how to go about loading games and playing them.  Please excuse my ignorance.  just want to know what the pitfalls are.  and would like to avoid going to sites that are virus prone and full of annoying ads.  thanks for all you help.

Best regards,

freesparks

---

### Post by dfreer on 2010-10-28
We can't link or discuss the downloading of ROM images on this board. You will have to look elsewhere for help with that.

---

### Post by freesparks on 2010-10-28
Hello [dfreer]("http://ubuntuforums.org/member.php?u=66193"),

  In no way did I mean to disrespect this forum and its collective. I thought, because of the open source mantra, we were excluded from certain provisions, since Zsnes was developed under the GNU license, please feel free to expound and correct me if I'm wrong.  Again, thank you for your help, and my most sincere apologies.

Best Regards,

freesparks

---

### Post by KBD20 on 2010-10-29
> **dfreer said:**
> Did you have any spaces or weird characters in your path, and can you read/write to the save directory? Also make sure the capitalization is correct as linux is case sensitive. Try removing the custom save path and see if they then save to ~/.zsnes if nothing else.

There wasn't anything strange with my path, unless all caps in some affects this in any way, my path was /home/username/SNES/SAVES/ 
(this is a separate path from the Roms [/home/username/SNES/ROMS])
In the past I think I have used the /.zsnes path, but I will try this just to be sure. 
:)

EDIT: I have changed the path to ~/.zsnes path, but the saving still does not work.

---

### Post by phz_swe on 2010-10-29
> **KBD20 said:**
> There wasn't anything strange with my path, unless all caps in some affects this in any way, my path was /home/username/SNES/SAVES/ 
(this is a separate path from the Roms [/home/username/SNES/ROMS])
In the past I think I have used the /.zsnes path, but I will try this just to be sure. 
:)

EDIT: I have changed the path to ~/.zsnes path, but the saving still does not work.

```
SRAMPath="/home/username/.zsnes/saves/"
```
That is how the path is written in ~/.zsnes/zsnesl.cfg on my current (Debian, but shouldn't matter) system. This directory of course exists and nothing weird is done with the permissions.

---

### Post by dfreer on 2010-10-29
> **freesparks said:**
> Hello [dfreer]("http://ubuntuforums.org/member.php?u=66193"),

  In no way did I mean to disrespect this forum and its collective. I thought, because of the open source mantra, we were excluded from certain provisions, since Zsnes was developed under the GNU license, please feel free to expound and correct me if I'm wrong.  Again, thank you for your help, and my most sincere apologies.

Best Regards,

freesparks

IANAL. While ZSNES is technically legal as it does not contain any sort of copyrighted code, the SNES games themselves are. Thus linking to a site (whether just by mentioning the name or a full blown http link) that contains SNES games can get ubuntuforums in trouble, which is why it's against the rules.

As for what you mentioned, about avoiding sites with viruses, I was trying to stave off people from linking to virus free ROM sites is all. You didn't do anything wrong as far as I know.

Generally speaking, most viruses people get are from downloading an emulator from random badguywebsite.com, instead of a "trusted" source like the original emulator website. The games themselves would be a lot harder to hide a virus in, as the games are run by the emulator it would have to expoit code in the emulator first, and then exploit the operating system.

So just make sure you know what type of files your emulator can play, and make sure the files you use are of that type. You should be good.

---

### Post by dfreer on 2010-10-29
I can't think of any other reason it shouldn't work. You might try the ZSNES boards, although if it's something relatively simple expect to get berated that's just the way ZSNES boards works :D

You might also try making a backup of your config file, and then move it elsewhere. ZSNES should then create a new one with all the default options, maybe it will work then.

EDIT: Ooops forgot to edit my first post. I haven't double posted like this in years lol.

---

### Post by KBD20 on 2010-10-29
I think I may have figured out the issue (although I haven't tested it yet), when I set my directory in ZSNES it showed my directory in all caps (regardless of what I typed) "HOME/USERNAME/SNES/SAVES/" however in the config file it was "home/username/snes/saves/", so I changed the snes and saves to all caps just to be sure. 
However I still have to test if this solved the problem :KS

---

### Post by mister_playboy on 2010-10-30
> **KBD20 said:**
> I think I may have figured out the issue (although I haven't tested it yet), when I set my directory in ZSNES it showed my directory in all caps (regardless of what I typed) "HOME/USERNAME/SNES/SAVES/" however in the config file it was "home/username/snes/saves/", so I changed the snes and saves to all caps just to be sure. 
However I still have to test if this solved the problem :KS

That could be it... zsnes was originally designed with case-insensitive Windows in mind.

---

### Post by sendblink23 on 2010-10-31
Why not install wine... and use the regular windows ZNES, works 100% fine over here (I placed mines inside the *Wine "c:" directory), never had any issues with it with saves or any game not working... even my controller pad is detected

---

### Post by del_diablo on 2010-10-31
Because running a native application over a translation layer is completely ridiculess when its suppose to run fine.

---

### Post by dfreer on 2010-10-31
> **KBD20 said:**
> I think I may have figured out the issue (although I haven't tested it yet), when I set my directory in ZSNES it showed my directory in all caps (regardless of what I typed) "HOME/USERNAME/SNES/SAVES/" however in the config file it was "home/username/snes/saves/", so I changed the snes and saves to all caps just to be sure. 
However I still have to test if this solved the problem :KS

IIRC in the config file you had to escape the backslashes as well. But it's been forever since I looked at it so I don't know. I think setting the path inside the emulator itself rather than by editing the config file was the preferred method as well. Here's mine on windows:

```
ROMPath="C:\\Users\\dfreer\\Games\\snes\\"
; Save states & SRAMs, snapshots, SPCs
SRAMPath="C:\\USERS\\DFREER\\GAMES\\SNES\\SAVES\\"
SnapPath="C:\\USERS\\DFREER\\GAMES\\SNES\\SCREENSHOTS\\"
SPCPath=""
```

---

### Post by KBD20 on 2010-10-31
It seems the 'save' (or SRAM) path is where the save states go, I am not sure about this though, but when sram was pointed to /home/username/SNES/SAVES/ files were only created there when I created a save state, I tried adding changing the SPC path to the same directory, and only one game has created an spc file in that path, the others I think I have to stick to save states for now.

---

### Post by dfreer on 2010-11-01
> **KBD20 said:**
> It seems the 'save' (or SRAM) path is where the save states go, I am not sure about this though, but when sram was pointed to /home/username/SNES/SAVES/ files were only created there when I created a save state, I tried adding changing the SPC path to the same directory, and only one game has created an spc file in that path, the others I think I have to stick to save states for now.

SPC = music files btw. Save states can get corrupted pretty fast, so they generally don't recommend using them exclusively. Not much else I think I can help with :(

---

