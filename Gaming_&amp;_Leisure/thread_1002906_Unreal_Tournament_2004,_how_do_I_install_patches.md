---
title: "Unreal Tournament 2004, how do I install patches?"
date: 2008-12-05
forum: Gaming &amp; Leisure
---

### Post by campbuds on 2008-12-05
How do I install the patches into unreal tournament 2004?

I got it installed easily and it runs but no sound and I read that the patches fix this. But didn't find anywhere on how to install them.

Like patches 3355 or 3369? They downloaded as tar.bz files.

---

### Post by Perfect Storm on 2008-12-05
Download the mega instead; [http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)

then;
```
cd ~/Desktop
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * <into ut2004 directory>
```

---

### Post by campbuds on 2008-12-05
Does this include every update released for the game? Including the ECE bonus pack?

---

### Post by Perfect Storm on 2008-12-05
Aye

---

### Post by campbuds on 2008-12-06
I did everything exactly the way you told me and now the game won't run at all.

---

### Post by Perfect Storm on 2008-12-06
Are you using 64-bit?
Which error shows up in the terminal?

---

### Post by campbuds on 2008-12-06
I don't even get an error. The terminal won't open.

I clicked just run and nothing happens. It seems like it tries to but cannot do anything. I tried running in terminal and still nothing.

I am in 32bit

---

### Post by Perfect Storm on 2008-12-06
Is UT2004 installed globally or local?

---

### Post by campbuds on 2008-12-06
I am not sure how to answer that. All I can tell you is I installed it to my directory since I didn't have permission for the usr directory and I skipped out on installing the second thing during install that asked for a directory because no matter where I picked it said I didn't have permission for the second item. It was running when I finished though. Just the sound wasn't working.

---

### Post by Perfect Storm on 2008-12-06
Then you installed it locally ($user).

When I gave you the command;

sudo cp -r * <into ut2004 directory>
it may affect ut2004 permission because of sudo infront. Instead it should be

cp -r * <into ut2004 directory>


Try all over again; If you want to install it globally; Here a hint/guide for that - [http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd)

---

### Post by campbuds on 2008-12-06
So do I need to uninstall and do a complete reinstall?

If so will uninstalling be affected by the permissions?

---

### Post by Perfect Storm on 2008-12-06
If you install it in a folder in your home you can just trash it.

---

### Post by campbuds on 2008-12-06
I followed the directions on that page to the "t"

Then I tried to run the game and came up with this error

```
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

---

### Post by Perfect Storm on 2008-12-06
```
sudo apt-get install libstdc++5
```

---

### Post by campbuds on 2008-12-07
I would like to understand what you had me do. It worked great!

One last issue then I would like help with. Video driver related I suppose.

In Vista when I ran the game it would run great with maxed out settings. Now it is choppy with the default settings. It seems my FPS is low. But I have no idea how to tell you what they actually are.

I have an intel video card. My laptop is a Vaio VGN-CR220E

If you need to know more than that, let me know how to get the info you require.

THANKS AGAIN!

---

### Post by Perfect Storm on 2008-12-07
Don't expect great 3D performance with intel cards in Linux. Intel cards in Linux is worse than in Windows when it comes to games.

Sorry.

---

### Post by campbuds on 2008-12-08
Is it a driver issue? Just thought it seemed odd since it ran better than perfect in windows.

Thanks for all your help

---

### Post by campbuds on 2008-12-08
it would seem i encountered one annoyance, that if I could rectify would be nice.

After playing the game or even just running and then exiting out of the menu I lose sound in the OS.

For example, I use atunes and when I run atunes after playing the game atunes will say it is playing a song but the slider isn't moving, the counter isn't counting and no sound comes out. Similar things happen when trying to play music in other apps.

Is there a fix for this? Currently all I can do is log out and log back in.

---

### Post by campbuds on 2008-12-12
I tried installing on my 64bit desktop, but I got an error during install (which blanked out so I was not able to read it)

It happened on disk 4

---

### Post by Perfect Storm on 2008-12-12
Ut2004 is a bit more complicated;
[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)
this guide is for DVD, but try copy the installer to your Desktop and run it from there.

---

### Post by campbuds on 2008-12-12
you did give me that link before, the problem is I am not able to get through a complete install

---

### Post by Perfect Storm on 2008-12-12
Have you tried with a search regading ut2004 and CDs? I have only the DVD version.

---

### Post by Kosimo on 2008-12-25
> **Artificial Intelligence said:**
> Download the mega instead; [http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)

then;
```
cd ~/Desktop
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * <into ut2004 directory>
```

By doing this I broke all my system...

---

### Post by Kosimo on 2008-12-25
Now I could install Unreal 2004 and works perfectly.
Even do it works, I want to install megapack patch. But I'm afraid of running again the above command.   There is any other way to do it?

---

### Post by Kosimo on 2008-12-25
> **Kosimo said:**
> By doing this I broke all my system...

Never mind... It was my fault, now I did it again and everything works as a charm.  Thank you.

---

