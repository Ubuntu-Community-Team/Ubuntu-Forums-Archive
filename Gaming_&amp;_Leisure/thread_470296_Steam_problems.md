---
title: "Steam problems"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by WheelDawg on 2007-06-10
I'm at the step now where I must copy Tahoma.ttf manually into the drive_c\Windows\fonts folder, but I have no idea how to browse to this folder to do this.

Supposedly drive_c is supposed to be in the home folder according to what I've read, but it's not there on this machine, and I can't find it.

---

### Post by WheelDawg on 2007-06-10
Ok I think I got that part done, by copying Tahoma into Ubuntu's Truetype folder, however I still don't know how to browse to the drive_c folder.

Also, I'm getting the crash at 27% a lot of people have gotten, but when copy pasting the command I found to fix that I get this:
```
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
```

I don't understand why it's telling me it can't find something in system32 when I'm telling it in the command that it's in Program Files.

---

### Post by seekers on 2007-06-10
Well welcome to answer your question about where to put the font.  you can open your Home Folder and View Show Hidden Files and then scroll down to .wine and navigate to your Fonts folder in System.   The second question is it does not know the path.  If you do a search I believe find a script that will do this for you.   To get it running just open a terminal and type cd /.wine and navate to the Steam folder and then run wine from there and it should open.:p

---

### Post by seekers on 2007-06-15
Your home folder you need to show all files to see the home folder.   Click on Places and then Home Folder Click on View and the Show Hidden Files.  Then scroll down to .wine folder and open it.  Then find the Fonts Folder.  This should take care of that problem.

---

### Post by cogadh on 2007-06-16
You can also just do CTRL-H to temporarily unhide hidden files when using the GUI to browse files. 

The reason why it is telling you it can't find that SteamTmp.exe in System32 is because the Steam.exe executable "calls" that other exe when it is run. When you are browsing to place the font file, check the System32 directory for the SteamTmp.exe file. If it is there, then just do as seeker suggests and navigate to the .wine directory before running Steam. If it isn't there, then you may need to re-run the install.

---

