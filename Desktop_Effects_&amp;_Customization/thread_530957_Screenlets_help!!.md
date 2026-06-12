---
title: "Screenlets help!!"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by borovy3488 on 2007-08-21
OK, this screenlets thing is just killing me.  Ive installed g/adesklets, and now screenlets, which didn't have MOST of what I was looking for.  gdesklets looked like open windows and just would not load on startup.  adesklets just plain didn't work.  So, my question is, does anyone know how to install the new (third-party) screenlets?  I have made a file in ~/.screenlets.  I put ONE new screenlet in there ("NowPlaying" screenlet).  Then, the file dissappeared!!!  WHAT?  Does anyone know another way to install new screenlets or how to make the file come back?  I have searched my entire file system for a file named .screenlets.  Nothing.  SO, I tried to create another file named ".screenlets".  Can't because it says there is already a file named that.  

Thanks in advance!!:mad:

---

### Post by Dark Star on 2007-08-21
A small how to on Adding screenlets...

1'st install Screenlets as mentioned in the guide then after it get installed  Download few screenlets from [Gnome-Look]("http://gnome-look.org/index.php?xcontentmode=165&PHPSESSID=1d7159a6185d9186c6ffc84604ac8520")

Now since You need to move those screenlets in Folder . 1'st Unzip the zipped pack .. then Extract the folder to Desktop  

After that copy the folder to /home/<user name> ... Then Open Terminal and type the following 

```

sudo mv <folder name> /usr/local/share/screenlets
```

---

### Post by borovy3488 on 2007-08-22
ok, that worked like a charm!! Now, how do i get them to open on startup??

---

### Post by Dark Star on 2007-08-22
> **borovy3488 said:**
> ok, that worked like a charm!! Now, how do i get them to open on startup??
Same question I also did not know this :lolflag: Though Screenlets open but the screenlets that I set did not open :x

---

### Post by kbzona on 2007-08-22
What version are you using?... Screenlets 0.10 have an option to open them at startup....
however if that doesnt work.. you always can make them start in
System->Preferences->Sessions....

---

### Post by Romanus81 on 2007-08-22
any file that begins with a "." such as .screenlets will tell the computer that it is a hidden file. Press Ctrl+H or look for "show hidden files" in your file browser's options to see it.

---

### Post by borovy3488 on 2007-08-22
OK, awesome I got them to work!!!  I never even noticed the menu option to run at start.  So, only a couple more ?'s.  How do I get the comic and nowplaying screenlets to work???

---

### Post by borovy3488 on 2007-08-22
anyone know?  Its probably a stupid question.  When I try to open either comic or nowplaying, it shows up, but they are blank, like they are showing no data.  Do I  have to do anything special to configure these??

Thanks

---

