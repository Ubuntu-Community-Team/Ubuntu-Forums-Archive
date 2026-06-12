---
title: "Help with Diablo 2 under Wine"
date: 2006-01-03
forum: Gaming &amp; Leisure
---

### Post by Razielx on 2006-01-03
I'm trying to get Diablo 2 to work under wine, and when I run Game.exe, I get the following error messages:

> 
[email]rodney@Asmoday:~/.wine[/email]/fake_windows/Program Files/Diablo II$ wine Game.exe
Invoking /usr/lib/wine/wine.bin Game.exe ...
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 00000001
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 00000001
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x126e,00007f00),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x1276,00007f8a),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x127e,00007f03),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x1286,00007f01),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x128e,00007f88),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x1296,00007f86),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x129e,00007f83),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x12a6,00007f82),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x12ae,00007f84),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x12b6,00007f04),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x744a0000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x744a006c
fixme:user:SetSystemCursor (0x12be,00007f02),stub!
fixme:ntdll:FILE_GetNtStatus Converting errno 16 to STATUS_UNSUCCESSFUL
fixme:user:SetSystemCursor (0x11c6,00007f8a),stub!
fixme:user:SetSystemCursor (0x11ce,00007f00),stub!
fixme:user:SetSystemCursor (0x11de,00007f03),stub!
fixme:user:SetSystemCursor (0x11e6,00007f01),stub!
fixme:user:SetSystemCursor (0x11f6,00007f88),stub!
fixme:user:SetSystemCursor (0x1206,00007f86),stub!
fixme:user:SetSystemCursor (0x1216,00007f83),stub!
fixme:user:SetSystemCursor (0x1226,00007f85),stub!
fixme:user:SetSystemCursor (0x1236,00007f82),stub!
fixme:user:SetSystemCursor (0x1246,00007f84),stub!
fixme:user:SetSystemCursor (0x1256,00007f04),stub!
fixme:user:SetSystemCursor (0x1266,00007f02),stub!
fixme:advapi:SetSecurityInfo stub
wine: Unhandled exception (thread 0009), starting debugger...
Usage: winedbg [--auto] [--gdb] cmdline
Wine failed with return code 1


When I run a no-cd crack, I get the following (significantly shorter) error message:

> rodney@Asmoday:~/.wine/fake_windows/Program Files/Diablo II$ wine Game_crk.exe
Invoking /usr/lib/wine/wine.bin Game_crk.exe ...
fixme:advapi:SetSecurityInfo stub
wine: Unhandled exception (thread 0009), starting debugger...
Usage: winedbg [--auto] [--gdb] cmdline
Wine failed with return code 1


Did anyone else have this happen, and if so, how did you guys solve it?

---

### Post by ed_d on 2006-01-14
did you run the vid test? What I did is I ran winecfg, added the game_crack.exe to the programs protion, then I went to the diplay properties and hard set the vidio to 1024x768, saved and restarted. It actually worked for me. The down sid is it will hang my system. I have  P3 with 3 gb ram too. I also had toe kill the wine program at exit sometimes. Try using windows 98 or 2000, and also XP vis "global options under winecfg too.

---

### Post by Dark Damo on 2006-01-15
Mine comes up with an error. something about direct3d or something.

[img]http://img66.imageshack.us/img66/8596/error257dy.jpg[/img]

I have done that "whatchamacallit" Video test ;)

---

### Post by Dark Damo on 2006-01-15
Anyone?

---

### Post by ed_d on 2006-01-15
OK, run the vid test again, but dont go through the whole test, just start the program, then, cant remember the button, but I think its the middle one, then choose the 2d option, will be the first one on the list, not the suggested one. Then rune the winecfg, and select game_crack.exe, select os level of win98, then go to the video tab and check the virtual screen. set it to 800x600 or 1024x768. Then rune the wine game-crack.exe and tell me what happens. Maybe Ill try and get the screen shots of what I did if this soounds confusing.

---

### Post by Dark Damo on 2006-01-15
Ok i'll try that now.

Do i have to use a crack. Because i only wantto play online. I dont care about single player and im afraid of getting my serial key banned.

---

### Post by ed_d on 2006-01-17
well, use the crack because a lot of people, including myself, have had issues playing the game without it. Also, there is a script to write that will allow you to connect to battlenet. Ill check the link tonight when I get home to the site that seemed to help me the most and post it then.

---

### Post by madjinx on 2006-01-17
hmm for Diablo 2 all i had to do was copy it from my Winodows dir to my linux one, and it ran flawlessly.

---

### Post by proud2bcdn on 2006-01-18
[QUOTE=madjinx]hmm for Diablo 2 all i had to do was copy it from my Winodows dir to my linux one, and it ran flawlessly.[/QUOTE]

Worked for me too...thanks for the suggestion :)

---

### Post by Dark Damo on 2006-01-18
How can i accsess my windows partition under linux? O_o

---

### Post by handy on 2006-01-18
If you have a look in the *Ubuntu Menu:*  **System/Help**

Then choose:  **Ubuntu 5.10 Starter Guide**

Then on the left hand navigation window you will see:  **Windows Partitions**

Select that for a quick & easy rundown on what you need to know.

G'luck

---

### Post by Dark Damo on 2006-01-18
Same problem. It still wants the cd even when it is in the damn drive.. :confused:

---

### Post by polpak on 2006-01-18
[QUOTE=Dark Damo]Same problem. It still wants the cd even when it is in the damn drive.. :confused:[/QUOTE]


Try running winecfg and go to the drives tab. Select the appropriate drive for your CD rom and then click advanced. Change the drive type to CD ROM rather than automatic or local hard disk.

That should get it working. (Works for Warcraft 3 at anyrate)

---

### Post by Dark Damo on 2006-01-19
Ok thanks.. Will boot up into ubuntu now.

IT WORKS! THANK YOU SOOO MUCH!

Now on to the second problem :mad: 

No Audio :( And wine freezes when i click the audio tab :(

---

### Post by jon_z on 2006-01-20
That happens to me when i click the audio tab, it didnt freeze, give it about a good minute, and it should come up, dont fret.

---

### Post by Dark Damo on 2006-01-20
It just closes off and gives a big error report. Anyone got any ideas?

---

### Post by polpak on 2006-01-20
[QUOTE=Dark Damo]It just closes off and gives a big error report. Anyone got any ideas?[/QUOTE]

Nope, I have the same issue.

---

### Post by Dark Damo on 2006-01-20
Hmm this calls for a frown.. :x

Damn this sucks.

---

