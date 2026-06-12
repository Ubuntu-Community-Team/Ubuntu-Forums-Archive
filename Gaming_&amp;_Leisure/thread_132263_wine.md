---
title: "wine"
date: 2006-02-18
forum: Gaming &amp; Leisure
---

### Post by montablac on 2006-02-18
ok,i know that for games you have to install off the cd(or extract if theve been DLED) but how does wine do this?

does it go and make a folder for it or what?

cause i want to get deus ex working under linux,and show my brother its true power

---

### Post by TheIdiotThatIsMe on 2006-02-18
WINE creates a folder that emulates the C drive in windows (although it is by default hidden). When you run the setup program through wine, it installs the files to this folder. I believe the folder is .drive_c (the . means it's hidden). So if you try to install, say the game Tropico, it would install to ~/.drive_c/Program Files/Tropico.

Also, WINE does not work with all Windows programs (in fact I've only ever had one work correctly). To check to see if your program is able to run under wine and find tips on making it run, visit [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by montablac on 2006-02-18
ok,so if it doent work,what other windowes emulators are there?

---

### Post by gerowen on 2006-02-18
Cedega is, from what I've seen, more aimed at DirectX and gaming support, although you have to pay for it.  I think you can get the source code for free and compile it, and you can get the source code for dx9wine that is basically wine with some DirectX support.  Juse use google to see where they are because I didn't save the links.

---

### Post by Yagisan on 2006-02-18
Current wine (0.9.8 - see winehq for .debs) seems to have better directx support then cedega as far as I can tell. It does have some issues with copy protection crap like securerom et al.

---

### Post by montablac on 2006-02-18
ok,so wine has directx souport,and my game works

but are there any altertinaves to wine in the resportistys?

PS.my spelling suxs

---

### Post by terrapin on 2006-02-18
I'm having trouble applying a patch to Wine. I'm trying to run [Kaboodle]("http://www.kaboodle.org/linux.html"). The patch that needs to be applied involves iphlpapi.dll. How do I apply this patch to Wine?

---

### Post by Yagisan on 2006-02-19
[QUOTE=terrapin]I'm having trouble applying a patch to Wine. I'm trying to run [Kaboodle]("http://www.kaboodle.org/linux.html"). The patch that needs to be applied involves iphlpapi.dll. How do I apply this patch to Wine?[/QUOTE]
1) That patch was released in 2003. Please try the current wine first, then see if your app will run.
2) Please start a new thread in future for off topic questions. Thanks.
[QUOTE=montablac]but are there any altertinaves to wine in the resportistys?[/quote]
No.

---

### Post by montablac on 2006-02-19
ok,well,thanks for that

i got it working,(kinda)

and my game works great(besides the 3d suport)

---

### Post by kenweill on 2006-02-19
How can I run windows/dos programs that needs an argument for the program?
Example:
start main.exe cal/u204.50.60.178 /p44405
It wont work with
wine start main.exe cal/u204.50.60.178 /p44405
or 
wine "start main.exe cal/u204.50.60.178 /p44405"
or
wine 'start main.exe cal/u204.50.60.178 /p44405'

What should I do? The command was extracted from an Psychic-Doom.bat, a batch files for DOS/Windows.

Got any solution?

---

### Post by kenweill on 2006-02-19
Oh, I got it now with:
wine main.exe cal/u204.50.60.178 /p44405

The game run succesfully but got a problem with the Windowing of the program. My resolution changed to the resolution of the program and I got the display of something like all 4 windows have been merged into 1 window. The game, my browser, my console, and the other console displaying the errors of wine.

I can't show the screenshot here coz when I try to have a screenshot, my machine hungs. I turn it off and restart manually.

Don't know if you guys have experienced this.
How can I make a program in wine run as full screen? I guess thats the problem.

---

