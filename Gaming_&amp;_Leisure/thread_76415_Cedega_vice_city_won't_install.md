---
title: "Cedega: vice city won't install"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by amatthews_1 on 2005-10-15
I just registered with Cedega and downloaded and installed both the cedega and point2play deb files.

When I tried to install GTA: Vice city I got an 'unhandled exception' error. So then I tried to install san andreas, and it installed fine, but it does not run.

I have a pentium 4 2.5 Ghz processor with 512 Mb of ram and I am running an Nvidia GeForce 4 Mx .

If anyone could help me get point 2 play working I would be greatful

---

### Post by seethru on 2005-10-15
whats the error you get when trying to run san andreas, I'm running it perfectly fine minus the odd screen encompassing artifact.

---

### Post by amatthews_1 on 2005-10-15
I don't get an error when I try to run San Andreas, thats  why its hard to debug. WHen I try to run it nothing happens.  I just checked the file permissions and they are all good.

---

### Post by seethru on 2005-10-15
run it with the command line -opengl, see if that works, and set winver to winxp.

---

### Post by amatthews_1 on 2005-10-15
[QUOTE=seethru]run it with the command line -opengl, see if that works, and set winver to winxp.[/QUOTE]

I tryed running it in the command line with opengl, but it didn't work.  what do you mean by setting winver to winxp?

---

### Post by seethru on 2005-10-15
in point2play, you can set the winver to winxp, just be sure to make a seperate profile for gta.

---

### Post by amatthews_1 on 2005-10-15
I tried that, but I still get the same results,  I have been looking around at the gentoo site, and I some suggest getting the No-Cd crack, I tried this but the file that I download is .rar, which I can not open.

---

### Post by Perfect Storm on 2005-10-15
If possible (I don't tried that game) try with an older version of cedega. Go to transgaming tab in Point2play and choose 'Download previous Cedega Version'. When it ask for making it default just say no. 
Now try to install it like this:
Press the install button. ( a windows pop up). Pick the advance tab and choose 'options'. Set Cedega version to the one you downloaded. Also try both win98 or WinXP in Winver.

Or

move all the CD files on your haredrive eg. /home/<username>/myGTAInstall
Instead of pointing Point2Play/cedega to your cd-rom point it to /home/<username>/myGTAInstall
Now go to the advance tab(which is desribed above) and select **Big EXE** and select **Run Directory** 

a third options are to combine my first suggestion with my second suggestion.



.:=The AI Dude=:.

---

### Post by seethru on 2005-10-15
to open a .rar do sudo apt-get install unrar-nonfree

---

### Post by gil-galad on 2005-10-15
Or you can get a native linux install that works with cedega [http://liflg.org/?catid=7&gameid=32]("http://liflg.org/?catid=7&gameid=32")

---

### Post by amatthews_1 on 2005-10-17
Using the nocd crack, I got san andreas to startup, but now I only get a black screen and then a long error message pops up in the terminal

the following is the bottome of the error


Backtrace:
=>0 0x405e03cf (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0xe3cf in winedbg.so) (ebp=40831eb0)
  1 0x405e07a1 (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0xe7a1 in winedbg.so) (ebp=40831f04)
  2 0x405dd5a1 (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0xb5a1 in winedbg.so) (ebp=40832074)
  3 0x405e79f8 (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0x159f8 in winedbg.so) (ebp=40832198)
  4 0x405e7dc2 (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0x15dc2 in winedbg.so) (ebp=4083220c)
  5 0x405e827a (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0x1627a in winedbg.so) (ebp=40832240)
  6 0x405d13d5 (/usr/lib/transgaming_cedega/winex/bin/winedbg.EntryPoint+0x2d in winedbg) (ebp=4083225c)
  7 0x400cb440 (NTDLL.DLL.wine_server_call+0x1e74 in libntdll.so) (ebp=40832304)  8 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=40832438)  9 0x4035f361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=408324b8)
  10 0x402f4bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x405e03cf (/usr/lib/transgaming_cedega/winex/bin/winedbg..data+0xe3cf in winedbg.so): cmpl     $8,0xc(%eax,%ecx,1)
Modules:
Address                 Module  Name
0x40057000-40059000     (PE)    NTDLL.DLL
0x405d0000-405d2000     (PE)    /usr/lib/transgaming_cedega/winex/bin/winedbg
0x40855000-40857000     (PE)    ADVAPI32.DLL
0x4089d000-4089f000     (PE)    KERNEL32.DLL
Threads:
process  tid      prio
0000000c (D) /usr/lib/transgaming_cedega/winex/bin/winedbg
        0000000d    0 <==
00000001
        0000000b    0
        0000000a    0
        00000008    0
        00000007    0
        00000006    0
        00000005    0
        00000003    0
        00000002    0
WineDbg terminated on pid c
Cannot close *fd* 12
Cannot close *fd* 13
Cannot close *fd* 11
Cannot close *fd* 14

---

### Post by amatthews_1 on 2005-10-18
I know got it to start up and by modifying the trangaming config file I got it to start up fine, and it runs until after the nvidia intro, then it quits.  the following is what I changed in the config file

;; Gta San Andreas
[AppDefaults\\gta_sa.exe\\d3dgl]
"Windows" = "winxp"
"VertexShaders" = "N"
"PixelShaders" = "Y"

After it quits I get a similar error as in the last post

I have a similar problem with civilization 3.  But with civ3 i don't get any errors

---

### Post by seethru on 2005-10-18
> **amatthews_1]I know got it to start up and by modifying the trangaming config file I got it to start up fine, and it runs until after the nvidia intro, then it quits.  the following is what I changed in the config file

 said:**
> 
"Windows" = "winxp"
"VertexShaders" = "N"
"PixelShaders" = "Y"

After it quits I get a similar error as in the last post

I have a similar problem with civilization 3.  But with civ3 i don't get any errors
are you running it with -opengl?

---

### Post by amatthews_1 on 2005-10-18
I tried running it both with and without -opengl

---

### Post by patrick295767 on 2005-12-17
I tried the loki installer and the :
```
cedega gta-vc
```
  
game crashes once everthg is loaded in the bar (dont see the movie)
& also the menu is very slow ...  
   
  
Did you manage to play with the game or did you give up ?
  
I am sure that there is a way 'cos linux ougth to be much better than window s!!
  
kind regards, 

patrick

---

### Post by bjweeks on 2005-12-18
[QUOTE=patrick295767]I tried the loki installer and the :
```
cedega gta-vc
```
  
game crashes once everthg is loaded in the bar (dont see the movie)
& also the menu is very slow ...  
   
  
Did you manage to play with the game or did you give up ?
  
I am sure that there is a way 'cos linux ougth to be much better than window s!!
  
kind regards, 

patrick[/QUOTE]

No, Linux is not better than Windows. It is a Windows game there for it plays right in windows.

---

