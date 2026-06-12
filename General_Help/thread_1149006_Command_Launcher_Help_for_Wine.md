---
title: "Command Launcher Help for Wine"
date: 2009-05-04
forum: General Help
---

### Post by rcayea on 2009-05-04
Hi everyone,

Question about Command Launcher under 9.04

I am looking for a little help about command launcher information. I was at the Main Menu screen and for some crazy reason I deleted wine (meaning now when I go to the Applications list I can't see the launcher anymore). OK, so I tried to create a new launcher. No dice. I don't know what to enter for the command. I have tried the Ubuntu Command Launcher examples where they list gedit as the example. I just can't figure out what to enter. 

I have used the browse option and made a link to usr/bin/wine but that doesn't seem to work. I have tried 'wine %U' and no luck with that either. 

I have uploaded two pics so you can see the area I am talking about. 

Thanks in advance,
Randy.

---

### Post by brettg on 2009-05-04
OK

If you need to rebuild the default wine entry on your menu enter this command;

sudo apt-get install wine --reinstall

To re-create your application entries you need to do something similar to this (test it out at the console before pasting into the "Command" field of your launcher);

env WINEPREFIX="/home/brettg/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\EXCEL.EXE" 

Alter the above path to suit your requirements of course.

HTH

---

### Post by rcayea on 2009-05-04
thanks for the help. I'll give it a go and report back any success. 

Randy.

---

### Post by rcayea on 2009-05-04
I had no luck. 

I used good ol' GIMP to edit my pic to show the exact area I need to fill in.

---

### Post by brettg on 2009-05-04
I think the problem is that you don't know what the question is.

What exactly are you trying to do? I am assuming you are trying to configure a launcher for a windows app that runs under wine.

In that case you need to do what I said before. The simplest answer is that you need to put the path to the windows exe you want to run after the wine command.

wine "/home/username/.wine/drive_c/Program Files/Microsoft Office/OFFICE11/EXCEL.EXE"

This example would start MS Excel assuming you have Office installed into the default location under wine. For a different program you are going to have to determine the path to the exe file you want to run and modify the command I gave you to suit that app.

---

### Post by rcayea on 2009-05-05
I guess sometimes a person needs a smack in the face to get it right, eh?


I will re-try to submit my question later (when I arrive home from work). 

Thanks for following up...


Randy

---

### Post by mc4man on 2009-05-05
If you deleted wine from your Applications menu then look in home folder -> .config/menus/applications.menu  (.config is a hidden folder, when in home folder go Ctrl+h if not visible 

You should see an entry like this (i added the red
```
</Menu>
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>
```

Remove what's in red, and save

---

### Post by rcayea on 2009-05-05
Thank you so much, Mc4man. I appreciate it!

Randy.

---

### Post by rcayea on 2009-05-05
How do I mark this thread as solved?

---

