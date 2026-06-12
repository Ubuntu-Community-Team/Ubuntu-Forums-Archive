---
title: "How to remove winfile.jpg(virus) from xp?"
date: 2009-02-19
forum: General Help
---

### Post by zohaib44 on 2009-02-19
hi everyone

here is my problem
when i right click on any drive i.e. C,D,E,F it shows an autoplay tab on top instead of open, when i double click on a drive  the drive doesn't open. I want to know that how to remove that winfile.jpg virus from xp.
i have tried so many well known antivirus programs but no antivirus detects it.

sorry for posting such a topic in ubuntu forums but seems like its my last hope.:(

take care.

---

### Post by Therion on 2009-02-19
Do you mean winfile.exe?  Follow these manual removal instructions:

[http://www.spywareremove.com/removewinfileexe.html](http://www.spywareremove.com/removewinfileexe.html)

---

### Post by zohaib44 on 2009-02-19
> **Therion said:**
> Do you mean winfile.exe?  Follow these manual removal instructions:

[http://www.spywareremove.com/removewinfileexe.html](http://www.spywareremove.com/removewinfileexe.html)

No its not winfile.exe, its winfile.jpg. i also tried those instructions but did not get rid of this thing.

any other help?

---

### Post by Therion on 2009-02-19
> **zohaib44 said:**
> No its not winfile.exe, its winfile.jpg. i also tried those instructions but did not get rid of this thing.

any other help?
My searches for anything related to a virus with the name of "winfile.jpg" turn up nothing.  I'm sorry, but I have no idea.  

One of my favorite places for Windows support though, back from the days when I needed help with things like removing viruese, is this website:

[http://forums.techguy.org/](http://forums.techguy.org/)   ...       Tech Support Guy (dot) org  -- great people on this site.

Maybe you should consider coming over to Ubuntu so you can leave issues like these behind?  Hint, hint...

Either way, good luck!

---

### Post by Tek-E on 2009-02-19
> **zohaib44 said:**
> hi everyone

here is my problem
when i right click on any drive i.e. C,D,E,F it shows an autoplay tab on top instead of open, when i double click on a drive  the drive doesn't open. I want to know that how to remove that winfile.jpg virus from xp.
i have tried so many well known antivirus programs but no antivirus detects it.

sorry for posting such a topic in ubuntu forums but seems like its my last hope.:(

take care.

Your problem doesnt sound like a virus to me at all.  And I havnt really heard of a virus with an extension of .jpg but I suppose it could be a parasitic virus.  If you know of the location of the virus. and you have a live cd of any flavor of linux, you should then be able to remove it from inside the linux live cd. That is how I have fixed a majority of my virus infections.  If you have issues with file permissions trying to remove the virus from inside linux then read the manual pages on the chown command.  Once you remove the virus or whatever it may be successfully I highly suggest you run ThreatFire and AVG on XP if you arent already doing so.  They are both free and work amazingly well.

---

### Post by philip.prem on 2009-04-15
> **Tek-E said:**
> Your problem doesnt sound like a virus to me at all.  And I havnt really heard of a virus with an extension of .jpg but I suppose it could be a parasitic virus.  If you know of the location of the virus. and you have a live cd of any flavor of linux, you should then be able to remove it from inside the linux live cd. That is how I have fixed a majority of my virus infections.  If you have issues with file permissions trying to remove the virus from inside linux then read the manual pages on the chown command.  Once you remove the virus or whatever it may be successfully I highly suggest you run ThreatFire and AVG on XP if you arent already doing so.  They are both free and work amazingly well.

Well I tried a messy process for removing this. The file is indeed a virus script with the extension .jpg! It is a unicode format VB Scipt.

To remove, my friends infected had no ready tool, so I did the following and it removes, but does not recover your windows to old state fully.

Use BartPE to create a windows offline boot for your XP. Boot BartPE from your CD (get help on this at [http://windowsxp.mvps.org/peboot.htm](http://windowsxp.mvps.org/peboot.htm))

Then do a manual removal of files as below;
1. C:\Autorun.inf winfile.jpg, and remove winjpg.jpg. Remove win.exe in windows folder/sub folders.
2. Where ever you find these files (.jpg) in your drives, remove them.
3. Then using BartPE registry editor, remove CTFMON and Regdiit from the Windows/CurrentVersion/Run 
4. Load different hives as said in the above site, and search for winfile.jpg or winjpg.jpg win.exe being executed as shell script
5. As the virus attaches to many registry keys - you may end up removing it, but having a non proper windows os. But if you do a windows repair after the above removal, everything should be back to normal

Any questions write to me as I just wrote the above from quick memory.

To prevent this in the future, disable autorun in all removable media - refer [http://autorun.moonvalley.com/enable.htm](http://autorun.moonvalley.com/enable.htm)

- Philip

---

### Post by juancarlospaco on 2009-04-15
LOL, if i ask on Microsoft Forum how to recompile my Ubuntu Kernel, 
no one reply...

:)

---

### Post by philip.prem on 2009-04-15
lol, the gentleman started with an apology, and it exposes the weakness of some others, why not detail it.
 - When I say "Some others" means other platforms!!! not people!!!

---

