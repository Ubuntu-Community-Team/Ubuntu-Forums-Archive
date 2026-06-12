---
title: "Wine Copy Protection - show me the files!"
date: 2006-07-02
forum: Gaming &amp; Leisure
---

### Post by monomaniacpat on 2006-07-02
I would like to install some of my PC games, like Half-Life, but with wine installed, the contents of the CDROM are invisible and the CD automatically loads as an audio CD.:confused: 

I asked on the IRC channel, and they said it was to do with copy protection. They told me to look at the wine appdb ([http://appdb.winehq.com)](http://appdb.winehq.com)), but since I have no clue what to look/search for, I don't know what to do.

How can I get HL working through wine?

Thanks,

mono.

---

### Post by FallenWizard on 2006-07-02
Try to install STEAM and play HL with it, it should work.

---

### Post by monomaniacpat on 2006-07-02
Won't I have to pay for the game again if I do that? Isn't there some way to get the CDROM recognised?

---

### Post by Grimmeehh on 2006-07-02
No, steam works under an account system. You create an account and register your valve games with it (HL, CS, HL2 DOD etc) Once you have your cdkey registered to an account all you need to remember is your username and password. you do not need to buy the game again. 

I dont know about the cd problem, but steam will be fine if you have a broadband internet connection.

---

### Post by monomaniacpat on 2006-07-02
Hmm, I'll give it a go. In the meantime, if anyone knows how to get to CD files directly, let me know.

---

### Post by monomaniacpat on 2006-07-02
Downlaoded Steam to install, the updater gets to about 26% and then says:

Steam.exe (main exception): ERROR: delete of steam.exe failed. Win32 "Sharing violation"

Any ideas?

---

### Post by Brucevdk on 2006-07-02
[QUOTE=monomaniacpat]Downlaoded Steam to install, the updater gets to about 26% and then says:

Steam.exe (main exception): ERROR: delete of steam.exe failed. Win32 "Sharing violation"

Any ideas?[/QUOTE]

See: [linuX-gamers.net Howtos: Steam, Half-Life, Half-Life 2, Counter-Strike 1.6 and Source with Wine]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games"). If you follow this howto, it'll work like a charm.

```

Q: Steam crashes at 26% of the update with a "Sharing violation"

Run the following command in the console (substitute the path to steam executables with your path)
wine C:\Program Files\Steam\SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

```

[QUOTE=monomaniacpat]
I would like to install some of my PC games, like Half-Life, but with wine installed, the contents of the CDROM are invisible and the CD automatically loads as an audio CD. 
[/QUOTE]

I've noticed this myself too, right clicking the icon on your desktop and selecting "Browse Folder" doesn't work either. It doesn't have anything to do with Copy Protection, more likely it has to do with how GNOME handles mixed cds. Just start up a Nautilus session and browse to /media/cdrom (ALT + F2, nautilus), this works.

---

### Post by monomaniacpat on 2006-07-02
Well I'm not entirely sure how I got it installed, but I think it was through downloading a wine tarball and building it from source. I previously could even see any files on the cdrom through the terminal.

Anyway, now I have another problem:

```
patrick@patrick:~/.wine/drive_c/SIERRA/Half-Life$ wine hl.exe
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\ddraw.dll") not found
err:module:import_dll Library DDRAW.dll (which is needed by L"C:\\SIERRA\\Half-Life\\hl.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\SIERRA\\Half-Life\\hl.exe" failed, status c0000135
patrick@patrick:~/.wine/drive_c/SIERRA/Half-Life$ wine hl.exe
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\ddraw.dll") not found
err:module:import_dll Library DDRAW.dll (which is needed by L"C:\\SIERRA\\Half-Life\\hl.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\SIERRA\\Half-Life\\hl.exe" failed, status c0000135

```

I assume I am missing those dll files? I downloaded DDRAW.dll, but that didn't help.

What to do?

---

### Post by monomaniacpat on 2006-07-02
[QUOTE=Brucevdk]I've noticed this myself too, right clicking the icon on your desktop and selecting "Browse Folder" doesn't work either. It doesn't have anything to do with Copy Protection, more likely it has to do with how GNOME handles mixed cds. Just start up a Nautilus session and browse to /media/cdrom (ALT + F2, nautilus), this works.[/QUOTE]

Just tried this when I inserted another cd, and yet again I cannot see the files on the CD, even using nautilus as you suggest! :confused:

EDIT: OK, done it again now. Put the CD in, select explore from the auto-loader-type prog and see only DirectX folder there. Navigate to /cdrom and bingo! It loads the files. :confused:

---

### Post by monomaniacpat on 2006-07-02
OK, so I have a game that actually works (Quake 2) except when I try to run it, I get a sound problem:

```
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(0) failed

```

I can switch wine to use OSS, which prevents the error message, but doesn't give me sound.

Any ideas?

PS. the Half-Life installer successfully played the wav file.

---

