---
title: "Warcraft 3 and FrozenThrone installation"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by kookookachooo on 2006-07-07
Hi, I am pretty new to Ubuntu and I only know the basics; so can anyone help me with the installation of WC3 and FT? I've read many other threads and guides including wine and there are small details that I do not understand. I'm a big fan of free so I decided not to use Cedega ;) . So can anyone please post and plain and simple (explained) guide to installing WC? If anyone out there can help a 'noob' out, many thanks.

---

### Post by Iarwain ben-adar on 2006-07-07
Hi,
well, to install WC3 you'd normally install wine first (you do have it, don't you?)

- If you have no Wine installed: 
```
sudo apt-get install wine
```

- If you have Wine installed:
```
sudo umount /dev/cdrom    #mount the cd (if neccessary)
cd /dev/cdrom
wine install.exe     #if the installer IS install.exe

```

And for The Frozen Throne you do the same :D


Iarwain

---

### Post by eqisow on 2006-07-07
Hi there kookookachooo. What Iarwain told you is pretty much spot on. If you run across any problems or need clarification let us know.

Also, once it's installed you may find that you get errors telling you to insert the correct CD-ROM. This can be solved by installing a No-CD Crack. :)

---

### Post by Hairy_Palms on 2006-07-07
no need for a no-cd crack since tha latest version of wine implements the cd protection :) cant remember if i got it from the wine repo or dapper repo but its version 0.9.16 ill post a screenie of it running in window mode  :)
once its installed to get maximum performance add -opengl to the launcher :)
[http://three.fsphost.com/mikemorley/wc3.png](http://three.fsphost.com/mikemorley/wc3.png)

---

### Post by LordRaiden on 2006-07-07
You just have to use winecfg and configure the CD drives to recognized as CD drives.

In a shell, do winecfg >> Select 'Drives' 

Select the advanced tab. Click on your CD drive in the listbox. select the dropdown box and change from Auto or Local hard Drive to CD ROM. Do this for all your CD drives then press ok.

---

### Post by kookookachooo on 2006-07-07
Hi, thank you all. I tried what Iarwain said; I had wine installed so I moved on to the mounting. I ran into errors, such as "could not find directory.." so I winged it:-| . I think it's a rather crude way but I installed both WC3 and FT (totally not sure if this way will work) I opened places>>home folder, on the left side I opened up cdrom1, WC3 was there; double-clicked, an icon mounted on my Desktop. Installed WC3 just like you would in Windows. Saved to C:/Program Files/WarcraftIII (no idea where it is, something to do with wine I'm guessing). Did the same thing with FT; the only problem now is I do not know where it is and I do not know how to play. I have wine 0.9.12 and I ran into the Error...'retry correct CD-rom' thing eqisow was talking about. By the way how do I install the No-Cd crack? I'not sure if WC even works so I haven't really tried. One last question, where do I type in the -opengl thing Hairy_Palms was taking about. Thank you all again.:)

PS: Do you guys think this way will work? Or should I start all over again?

---

### Post by Iarwain ben-adar on 2006-07-07
Hi kookooachooo,

First of all, could you specify (sp?) wich dir's couldn't be found?

2nd: Did the game actually install (meaning: did you see the files being installed etc?)

3rd: Normally (i don't have wine, so bear with me) i think wine would be in the ~/.wine folder (~ being your /$USER/home dir)

4th: The No-cd crack is installed by:
     backing up the original exe (you'll thank me if the crack does something wrond ;) ) and then replace it with the crack's exe
     OR
     executing the exe in the no-cd crack (and the exe being a file that "patches" your game.exe)

5th and last of this series of numbers :D : I THINK he means that the -opengl is an argument; meaning that you should type:
```
wine -opengl game.exe
```


Hope this helps ;)


Iarwain

---

### Post by Linkhiei on 2006-07-07
One no-cd patch for FT can be found here:

[http://gbw.seedhost.com/files/Warcraft3TheFrozenThronev1.18aFixedexeAll.rar]("http://gbw.seedhost.com/files/Warcraft3TheFrozenThronev1.18aFixedexeAll.rar")

its a rar file tho so ur gonna need to unzip it and then copy the war3.exe into ur frozen throne directory. No-cd patches aren't illegal if u have a legal copy of the game ;) 
then the command should be something like 

```
wine "/insert warcraft directory here/war3.exe" -opengl 
```

---

### Post by kookookachooo on 2006-07-07
Hello again,
Iarwain-
1. The directory that wasn't found was the 'cd /dev/cdrom'. So i could not proceed with your installation process.

2. The game installed (pretty sure), when WC3 and FT was installing there is a dialog box and a processing window. I could see all the files being installed; just like if you would install in windows.

3. I dont know where my wine directory is.:-? (if someone could help me find it):p 

4. I do not know where my Warcraft3 directory is. It said it should be in
c:/Program Files/Warcraft3 but I do not know where to go about finding this directory.

5. Thank you, even though I don't know what to do with it. After I type it in it reads 'wine: could not load L"c:\\windows\\system32\\-opengl.exe": Module not found'

6. Thank you :D 

Thank you too Linkhiei,
I'd also like to know, would you know where to find the defualt Warcraft3 directory? Also, thanks for the crack.

---

### Post by Iarwain ben-adar on 2006-07-08
Hi there,

now, for the cdrom not being found: you got the game installed (so the cdrom isn't any longer a problem :D )

Good to hear it is installed 

And your Wine dir should be in your home folder (type this in your "adress  thingy: /.wine )
With a tad of luck, you should see the folder (or even better, be in the folder :D)

Once you found your Wine folder, you can navigate to your W3 dir.

And the 5th: i was wrong: type this: ```
wine gameprogram.exe -opengl
```

But remember you have to be in the dir where the exe is (otherwise you have to use absolute paths ;) )


Iarwain

---

### Post by meastp on 2006-07-08
[I]Hello again,
Iarwain-
1. The directory that wasn't found was the 'cd /dev/cdrom'. So i could not proceed with your installation process.
[/I]
Normally, you would not have to do the mount process in the terminal, it should mount the cd automatically. 

If you want to mount something, the right command would be:
```

sudo mount /dev/cdrom

```

```

sudo umount /dev/cdrom

```

as suggested by Iarwain ben-adar, will umount/de-mount/remove it.

[I]2. The game installed (pretty sure), when WC3 and FT was installing there is a dialog box and a processing window. I could see all the files being installed; just like if you would install in windows.

3. I dont know where my wine directory is.:-? (if someone could help me find it):p [/I]

it's in /home/yourusername/.wine/

[I]4. I do not know where my Warcraft3 directory is. It said it should be in
c:/Program Files/Warcraft3 but I do not know where to go about finding this directory.[/I]

it's in /home/yourusername/.wine/drive_c/Program Files/Warcraft3/

*5. Thank you, even though I don't know what to do with it. After I type it in it reads 'wine: could not load L"c:\\windows\\system32\\-opengl.exe": Module not found'*

Check if you have installed your drivers for your gfx card correctly.

---

### Post by kookookachooo on 2006-07-08
Cool, thanks. Now I have the problem of actually getting the game to run. I've found the WC3 directory and i double-click Frozen Throne.exe but it comes up "insert correct CD-rom". I've treid the no-cd crack that Linkhiei posted but it doesn't seem to work. Do you guys know of a crack that works for sure? Thank you meastp, and how would one go about finding if he installed his drivers correctly? I have a ATI 9200SE, I was reading how the lastest drivers dont work for the 9000+ series; i dont know though..Many thanks again.

---

### Post by vem0m on 2006-07-08
hmmmmm what version of WC3 are u trying to run??

---

### Post by Linkhiei on 2006-07-08
usually i just search google with something like "warcraft 3 frozen throne no-cd". but sometimes theyre a pain in the butt to find. :mad:

---

### Post by Zifnab on 2006-07-08
I just installed Dapper (64-bit) a couple days ago and so far have pretty much everything up and running. Today I've been experimenting with Wine (version 0.9.16), and one game I'd actually like to play is Warcraft 3.

The installation went fine, but when I run the game the entire screen goes black and the CD drive runs for a bit, but nothing happens. If I switch to a console (e.g. with Ctrl-Alt-F1) and kill the War3.exe process then switch back to X, the screen is still black, though I do get a mouse cursor and clicking near my desktop shortcuts causes the "busy" cursor to appear so it's apparently responsive. I'm forced to reboot via the console to get my GUI back.

When I run it through winedbg, after taking a couple steps through the program with "cont", I keep getting error messages like this:
```
First chance exception: divide by zero in 32-bit code (0x0045ae47).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:0045ae47 ESP:55c1fe90 EBP:55c1fe9c EFLAGS:00010212(   - 00      - RIA1)
 EAX:0000000c EBX:55a77214 ECX:00000000 EDX:00000000
 ESI:00467fdc EDI:55755d00
Stack dump:
0x55c1fe90:  55755d00 00467fdc 55a77214 55c1fec8
0x55c1fea0:  00461470 55c1fef8 0045a0c0 55755d00
0x55c1feb0:  00467fdc 55a77214 0045a0b0 00000000
0x55c1fec0:  00467fdc 004676d9 55c1ff08 00468090
0x55c1fed0:  00000001 5fcd0928 5fcd0950 55755d00
0x55c1fee0:  00467fdc 55a77214 55c1ff08 555cd9c1
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x0045ae47 in war3 (+0x5ae47) (0x0045ae47)
  2 0x00461470 in war3 (+0x61470) (0x00461470)
  3 0x00468090 in war3 (+0x68090) (0x00468090)
  4 0x55a3d94f in kernel32 (+0x4d94f) (0x55a3d94f)
  5 0x55573443 wine_switch_to_stack+0x17 in libwine.so.1 (0x55573443)
0x0045ae47: idivl       %ecx,%eax

```
That divide-by-zero bit looks um, bad.

Anyone seen something like this before? Should I even bother installing The Frozen Throne?

---

### Post by vem0m on 2006-07-08
the version i mean what patch as then a no cd would be easier to find for u

---

### Post by kookookachooo on 2006-07-09
Hi, umm I'm trying to run the lastest patch of WC3:FT. Ive look in places but they haven't worked. Does anyone have a No-cd crack that they are currently using that works? thanks in advanced

---

### Post by Iarwain ben-adar on 2006-07-09
> **Zifnab said:**
> I just installed Dapper (64-bit) a couple days ago and so far have pretty much everything up and running. Today I've been experimenting with Wine (version 0.9.16), and one game I'd actually like to play is Warcraft 3.

The installation went fine, but when I run the game the entire screen goes black and the CD drive runs for a bit, but nothing happens. If I switch to a console (e.g. with Ctrl-Alt-F1) and kill the War3.exe process then switch back to X, the screen is still black, though I do get a mouse cursor and clicking near my desktop shortcuts causes the "busy" cursor to appear so it's apparently responsive. I'm forced to reboot via the console to get my GUI back.

When I run it through winedbg, after taking a couple steps through the program with "cont", I keep getting error messages like this:
```
First chance exception: divide by zero in 32-bit code (0x0045ae47).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:0045ae47 ESP:55c1fe90 EBP:55c1fe9c EFLAGS:00010212(   - 00      - RIA1)
 EAX:0000000c EBX:55a77214 ECX:00000000 EDX:00000000
 ESI:00467fdc EDI:55755d00
Stack dump:
0x55c1fe90:  55755d00 00467fdc 55a77214 55c1fec8
0x55c1fea0:  00461470 55c1fef8 0045a0c0 55755d00
0x55c1feb0:  00467fdc 55a77214 0045a0b0 00000000
0x55c1fec0:  00467fdc 004676d9 55c1ff08 00468090
0x55c1fed0:  00000001 5fcd0928 5fcd0950 55755d00
0x55c1fee0:  00467fdc 55a77214 55c1ff08 555cd9c1
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x0045ae47 in war3 (+0x5ae47) (0x0045ae47)
  2 0x00461470 in war3 (+0x61470) (0x00461470)
  3 0x00468090 in war3 (+0x68090) (0x00468090)
  4 0x55a3d94f in kernel32 (+0x4d94f) (0x55a3d94f)
  5 0x55573443 wine_switch_to_stack+0x17 in libwine.so.1 (0x55573443)
0x0045ae47: idivl       %ecx,%eax

```
That divide-by-zero bit looks um, bad.

Anyone seen something like this before? Should I even bother installing The Frozen Throne?

Hi zifnab,
i think it would be better if you'd start a new thread (no thread hijacking ;) )
But i have never seen that before, so sorry.

> **kookookachooo said:**
> Hi, umm I'm trying to run the lastest patch of WC3:FT. Ive look in places but they haven't worked. Does anyone have a No-cd crack that they are currently using that works? thanks in advanced

Hi kookookachooo,
happy to see it all worked out :D
Now: the patch :D
Can you right-click on the original exe, and see if there's a version number?


Iarwain

---

### Post by polpak on 2006-07-09
> **kookookachooo said:**
> Hi, umm I'm trying to run the lastest patch of WC3:FT. Ive look in places but they haven't worked. Does anyone have a No-cd crack that they are currently using that works? thanks in advanced

You don't need a no cd crack. You just need to configure your drives under wine.

from a terminal run:

winecfg


Then go to the "Drives" tab click the "AutoDetect" button. Then select your cdrom drive (probably /media/cdrom0) and click the "Show advanced" button. Change the "Type" dropdown to say "CD-ROM" and click, apply and OK.  Then put the War3 cd in the drive and try to run the game again.

Works great.

---

### Post by Max Luebbe on 2006-07-09
On the topic of Frozen Throne - I used to play it all the time on battle.net with no problems and great performance using cedega.

Cedega isn't free, but if you're a gaming nut like I was, it might be worth taking a look at.

---

### Post by kookookachooo on 2006-07-09
Hi, ok, I'm a big fan of free and I was VERRY close to subscribing, but then I thought to myself, "It can't help to try one more time." I looked around all the threads again and tried and tried...then I finally got WC3:FT to work!!:D As It turned out I guess I was using the wrong No-cd crack.:oops: Well, It was going great but I ran into a few snags. 
   
    #1 WC runs SUPERRR sloww.I've tried the -opengl thing and it doesn't seem to change it. Is there some other way to quicken the speed or check if I did it correctly or not?

    #2 The graphics seem really weak, and I know they should be better; is there a way to check if I installed my ATI drivers correctly? I have an ATI 9200SE.

Many thanks for all your help to solve the MAJOR problem guys!:D Especially Iarwain.:p

---

### Post by Iarwain ben-adar on 2006-07-09
:D

Well, if you can't play the game like you should play it...

For #1 i cant help much, only ask you if you have any background processes that take alot of cpu/ram.

And #2: and to see if your gfx card is installed properly, type this:
```
glxgears -printfps
```
If you get large numbers (a big fps thus :D ) i think you can say your drivers are installed correctly ;)

But know: i have an 6600 TD (Nvidia) and i get around 30fps in Morrowind (and in windows i got around 60fps)


Iarwain

---

### Post by vem0m on 2006-07-09
or pay for a month or 2 of cedega then stop paying tell it to not log in anymore or check for updates and u can use the full version without paying u just don't get updates :P

---

