---
title: "Dressing up ubuntu:Doing it right!"
date: 2010-08-08
forum: Desktop Environments
---

### Post by jinba.ittai on 2010-08-08
[CENTER]This is my 7th or 8th time reinstalling ubuntu. A few times were due to hard ware change, but the main reason was i allways messed up the environment! Im still getting used to ubuntu, and using the terminal (somewhat addicted to ubuntu now) and have already accomplished a few things. 

Ive got conky up an running, with no bugs, and actually figured out how to set up my own .conkyrc file, this was my first mod to ubuntu, or app, what ever you choose to call it. Now that that is up and running smoothly i want to get a few other things to make my desktop look appealing.

Im not too worried about graphics processing, take a look at my specs, should i be?



What i am trying to do now is make the Gnome Terminal run transparent as the background, but i have been having a few problems. I havent messed with the geometry because it still looks pretty strange, and it moves around in its own window instead of being sticky to the background. Id also love to make it sticky to all workspaces, or does that require more instances of terminal?

This thread isnt just a help thread for me, im going to try and track my progress in modifying the environment, so if i crreate something beautiful, it will be easy to share![/CENTER]


This is how my desktop looks now
[my work in progress]("http://i34.tinypic.com/2d29a2v.png")


The terminal still has the bar on top, and i dont know if devilspie did anything.

---

### Post by jinba.ittai on 2010-08-08
Ok, so in the [thread]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop") i get stuck at part 5. Ive succesfully installed devilspie and pasted the code in it, but havent modified the geometry. 

Does the bar on top of the terminal show because of the theme? im still on the default theme. Dont know know if that changes anything.

Stil trying to figure out how to get terminal to look like [this.]("http://img336.imageshack.us/img336/378/desktopterminal0uz.png")

---

### Post by nick_goodfate on 2010-08-08
> **jinba.ittai said:**
> Ok, so in the [thread]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop") i get stuck at part 5. Ive succesfully installed devilspie and pasted the code in it, but havent modified the geometry. 

Does the bar on top of the terminal show because of the theme? im still on the default theme. Dont know know if that changes anything.

Stil trying to figure out how to get terminal to look like [this.]("http://img336.imageshack.us/img336/378/desktopterminal0uz.png")

For step 5 : System -> Preferences -> Startup Applications . Press "add" and in command field write "devilspie". In Name and Comments write whatever you want doesn't matter ... Press "add" to save it . Same for "gnome-terminal --window-with-profile=DesktopConsole" .

My desktop looks like [this]("http://tinypic.com/r/207ucn4/4") . Just to give some ideas. If you like something ...

---

### Post by jinba.ittai on 2010-08-08
Wow, i love your setup. I went and tried another tut for eterm, but i dont like the way its an actual app that shows up in the workspace switcher.

Im going to close eterm and try this one again. I wanted it to have no borders and just sit as an actual background, but that seems to be too complicated. Going to try what you said and report back.

---

### Post by jinba.ittai on 2010-08-08
done and done


but it still starts up with the bar at the top. Not the menu bar, but the bar thatt changes with what ever theme you select. 

If its possible, id like to stop using these panels all together, they are quite bothersome. What dock are you using?

---

### Post by nick_goodfate on 2010-08-08
try this : uncheck the "gnome-terminal --window-with-profile=DesktopConsole" entry at your startup applications and reboot. Then open a terminal and type "gnome-terminal --window-with-profile=DesktopConsole". I want you to try this to see if the "check to see that devilspie is running *before* the gnome-terminal command." part of [this thread]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop") is whats wrong .

I m using AWN. I believe its the best and complete panel-replacement...

---

### Post by jinba.ittai on 2010-08-08
Mmm ive used awn before, but it didnt look as sexy as your hehe. 

Will report back in a few.

---

### Post by jinba.ittai on 2010-08-08
I ran the command you told me, and all it did was open a knew terminal. I dont think devilspie is doing anything at all (what is it supposed to do again?) cause my terminal looks exactly the same as it did when you first install ubuntu except i changed the transparency etc. 

The bar above the menu bar still apears.

---

### Post by nick_goodfate on 2010-08-08
i m sorry i cant help you more with devilspie , i ve never tried to use it. 
But i don't think it's very important for the appearance of your desktop and i believe it's impractical to have the terminal as part of your wallpaper... Anyway i hope someone who have used devilspie see this thread and help you with that .

---

### Post by oldos2er on 2010-08-08
If you're running compiz, you might want to take a look at [http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html](http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html)

---

### Post by jinba.ittai on 2010-08-08
> **nick_goodfate said:**
> i m sorry i cant help you more with devilspie , i ve never tried to use it. 
But i don't think it's very important for the appearance of your desktop and i believe it's impractical to have the terminal as part of your wallpaper... Anyway i hope someone who have used devilspie see this thread and help you with that .

Well thanks for the help you have given me, i apreciate it. I terminal ALOT, but this is the first time i have actually gotten into modding the environment.

---

### Post by StephanG on 2010-08-09
I know this thread is for modifying Ubuntu, but I couldn't help but want to show off my Kubuntu desktop a bit.

I've only made a few basic changes to the desktop itself.  These include using Lancelot instead of the default Application Launcher. It just works much better for me.

As far as Console goes, I use Yakuake.  I find it really convenient.  Everytime I need a console, I press F12, and a loaded one drops down from above.  I don't have to wait for it.  I don't have to look at it when I'm not using it.  But its always there, ready for use.

For the transparency in my windows I use Bespin.  Unfortunately I had to compile the latest version myself.  But I think the result is well worth the effort.

For the blurring used by my transparent windows and Yakuake I had to install KDE 4.5 RC 2.

I use the Tragedy plasma theme.  Not the best, I know.  But for some reason I can't explain, I just like it.

And lastly, I'm using Smaragd to run emerald themes as a KDE Window decoration.  The current emerald theme is called smarald-black.

Anyway, that's my desktop.

P.S.  You'll have to forgive the absurdly high readings on my RAM and CPU plasmoids.  I'm currently running a lot of processes in the background.  Most notably Strigi is busy indexing my harddrive.

---

### Post by jinba.ittai on 2010-08-09
Wow stephen, thats a nice set up. Im running 6 gigs of ram and actually just baught a new vid card right now. 1 gb of ddr5 video ram!

Gona try this tut for the terminal in the background and install awn then post some pics. Also trying to figureout how to get one of these gtk themes from gnome-look to work.

---

### Post by nick_goodfate on 2010-08-09
> **jinba.ittai said:**
> Also trying to figureout how to get one of these gtk themes from gnome-look to work.

download the theme you like, open Apearance Preferences->theme tab (right click on desktop->change desktop backround). Then just drag-drop the file you downloaded into themes area.

---

### Post by nick_goodfate on 2010-08-09
Some nice themes(follow the install instructions of the links i give you, if you like any of them) :
[LIST][*][_Elementary theme_]("http://www.omgubuntu.co.uk/2010/06/elementary-theme-gets-new-release.html")[*]Community-themes(you can find it in Synaptic Package Manager)[*][_Ubuntu 10.10 Light themes_]("http://www.omgubuntu.co.uk/2010/08/is-thisubuntu-1010-light-themes-new.html")[*][_Themes by pr09studio_]("http://www.omgubuntu.co.uk/2010/06/daily-5-5-beautiful-themes-by.html")


[/LIST]

And a great [_icons pack_]("http://tiheum.deviantart.com/art/Faenza-Icons-173323228"), which i use. You can install icon packs the same way you install gtk themes...

---

### Post by fabounet on 2010-08-10
you can try GLX-Dock to sexy up your desktop (and replace your gnome-panels)
it also has a nice terminal that you can detach from the dock, and use ala Tilda.

---

### Post by jinba.ittai on 2010-08-11
> **fabounet said:**
> you can try GLX-Dock to sexy up your desktop (and replace your gnome-panels)
it also has a nice terminal that you can detach from the dock, and use ala Tilda.


Ill check that out after i try some of these themes on for size. Searched it up, looks neet.

---

### Post by liza123 on 2010-08-11
Hi,

Thanks for the great information.

[Company Name Ideas]("http://www.squadhelp.com")

---

