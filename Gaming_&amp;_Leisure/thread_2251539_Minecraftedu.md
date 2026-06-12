---
title: "Minecraftedu"
date: 2014-11-04
forum: Gaming &amp; Leisure
---

### Post by cmcanulty on 2014-11-04
I can easily install minecraft but minecraftedu is a different matter. I have it installed on our library public computers and can launch it by going to the mincraftedu directory and double clicking Launcher.jar but that is a bit much for our library kids. All efforts to create a desktop or panel launcher have failed. I tried adding a launcher on desktop by making a link to Launcher.jar  no go. Also tried new launcher on desktop and put the command to /home/username/minecraftedu/Launcher.jar that doesn't work either and it isn't in the games menu either. I need help on this.

---

### Post by oldrocker99 on 2014-11-04
> **cmcanulty said:**
> I can easily install minecraft but minecraftedu is a different matter. I have it installed on our library public computers and can launch it by going to the mincraftedu directory and double clicking Launcher.jar but that is a bit much for our library kids. All efforts to create a desktop or panel launcher have failed. I tried adding a launcher on desktop by making a link to Launcher.jar  no go. Also tried new launcher on desktop and put the command to /home/username/minecraftedu/Launcher.jar that doesn't work either and it isn't in the games menu either. I need help on this.

I believe you need to include the command 'java' before the path, thus:
```
java /home/username/minecraftedu/Launcher.jar
```

Also, make sure the .jar file is executable:
```
chmod +x /home/username/minecraftedu/Launcher.jar
```

Of course, you may already have done that.

---

### Post by JohnnyComeL8ly on 2014-11-04
I guess since you already have Minecraftedu, your kids probably don't really care for it, but you, if interested in FOSS will like [Minetest]("http://minetest.net").  The reason I bring it up is because depending on your situation, you could have "the same" experience with all the benefits of FOSS.  Of course, this is my opinion...  maybe you already thought about it.;)

---

### Post by cmcanulty on 2014-11-05
that launcher doesn't work either

---

### Post by Nytram on 2014-11-05
It may be that the current directory needs changing to *minecraftedu* before it's launched.

This *should* work: create a new text file on your desktop with a name of your choice (it will be the Mincecraftedu launcher.)

Insert this text:
```

cd /home/username/minecraftedu
java ./Launcher.jar

```

Then make this file executable, it should launch your Mincecraftedu now.

---

### Post by cmcanulty on 2014-11-05
nope just opens the text file. I could click open with but java doesn't show in list and in /usr/bin there are several java things

---

### Post by Nytram on 2014-11-05
My mistake, Ubuntu seems to have changed how it handles text files and scripts since I last did something like this (it used to give an option to edit the file or run it.) To have the file run instead of be edited, it's necessary to change an option in *Files* -  go into *settings/preferences* and choose the *Behaviour* tab. Then select *Run executable text files when they are opened* or *Ask each time* whichever you prefer.

---

### Post by cmcanulty on 2014-11-05
I thought of that but I don't want our public patrons to be able to execute a txt file at all. It seems awfully weird that there is no easy yet secure way to set a launcher for a java app. I have never used java apps before so this is new. I have to run 10 public library machines and it sure would be better to have a minecraftedu launcher on desktop than having kids have to navigate to /home/username/minecraftedu/Launcher.jar

---

### Post by ringstaart on 2014-11-06
Have you considered just putting the Launcher.jar file on the desktop? If I remember correctly, that doesn't mess anything up - it doesn't change anything about where the game files are located.

---

### Post by cmcanulty on 2014-11-06
yes I tried that first nothing happens when I double click it and it is executable yet I get this error see screenshot 2nd screenshot is something else but I can't delete it-ignore

[ATTACH=CONFIG]257784[/ATTACH]

---

### Post by ringstaart on 2014-11-06
> **cmcanulty said:**
> yes I tried that first nothing happens when I double click it and it is executable yet I get this error see screenshot 2nd screenshot is something else but I can't delete it-ignore

[ATTACH=CONFIG]257784[/ATTACH]

That's weird. It looks like it's actually trying to install to "/", the root directory - it's not supposed to do that. Does it work normally when started up from the /home/username/minecraftedu/ directory?

A temporary fix to make it easier to start it properly would be to make a link to the /home/username/minecraftedu/ directory instead of Minecraft.jar. If you do that, they can click the folder and figure out that they need to click the Minecraft.jar file - it's not optimal, but it should be better.

---

### Post by cmcanulty on 2014-11-06
no, it's installed to users home, very weird but this is my first exposure to a .jar file except in macs. it works properly once you navigate to it but no links to it will work. I tried putting  a link to minecraftedu directory on desktop as you suggested but I get the same error as in the screenshot when I try to launch the Launcher.jar from the link

---

