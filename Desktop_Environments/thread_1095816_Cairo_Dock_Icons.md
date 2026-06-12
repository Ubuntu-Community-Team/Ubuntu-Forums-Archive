---
title: "Cairo Dock Icons"
date: 2009-03-14
forum: Desktop Environments
---

### Post by s.fox on 2009-03-14
Hi,

I have a cario dock using a macOSX theme.  I have set my own custom icons for the launchers but when I click the launcher a different icon for the running application appears on the right hand side of the dock.  For example when I click my firefox icon I get a safari icon appear on the rught hand side of the dock.

Ideally I would like the icons to match.  Any thoughts on what is going on and what I can do about it?

Many thanks,

-Ash R

p.s.  If any clarification is needed please ask.

---

### Post by andrea000 on 2009-03-15
Ash R.

I don't know if this help out but start by finding jpeg's that match the programs you have then open them in gimp and resize all of then to the same size.You can then put all of them in a folder and right click on the icon on cairo dock and go to modify this launcher were it says image name or path click open find the folder click on the jpeg you would like to use and say ok.you can also import the jpeg's into cairo dock the first way is just a little easyer they both work the same.or you can just drag firefox down to thebar and so on.
There is also a check box that says use new cairo dock icons somewere in the config. 

good luck i hope this helps

:popcorn:

---

### Post by blackened on 2009-03-15
You could also change the applications' main icons that are part of the icon theme you are using. I can't say that I would suggest doing this as it would be enormously tedious.

If you would go this route, begin by locating your icon theme either in /usr/share/icons or ~/.icons, and from there start changing individual icons to suit your taste.

---

### Post by s.fox on 2009-03-15
Hi everyone,

I think I am not being clear by what I mean. 

In the screen shot I have a custom icon that I set for firefox in my dock.  Problem is that when I click it a Safari logo appears in the dock.   I hope the screen shot helps explain the problem better.

Many thanks,

Ash R

---

### Post by Zahne on 2009-03-15
Yeah, I'm having the same issue. I like the mac osx dock itself but I'd like my own icons. Fox example I dragged my Celtx app down to the dock and its icon was replaced by that default box spring-like icon that apps with no icon have. I attempted to restore the icon by going to "modify launcher" in the dock but the .png was already selected and simply not appearing. Then I tried re-locating it and was prompted with an error message.

---

### Post by blackened on 2009-03-15
> **Ash R said:**
> Hi everyone,

I think I am not being clear by what I mean. 

In the screen shot I have a custom icon that I set for firefox in my dock.  Problem is that when I click it a Safari logo appears in the dock.   I hope the screen shot helps explain the problem better.

Many thanks,

Ash R

Ah I see. That looks like it's going to be a setting somewhere in Cairo dock itself. I can't really be any help as I've never used it.

---

### Post by fabounet on 2009-03-16
you're using the "LocalTheme" icons set, that is to say, the one located in ~/.config/cairo-dock/current_theme/icons.

so either :
- in the config, remove this theme from the list of icons themes (in "Icons" tab)
- in ~/.config/cairo-dock/current_theme/icons remove the firefox.svg icon or change it.

---

### Post by s.fox on 2009-03-16
> **fabounet said:**
> you're using the "LocalTheme" icons set, that is to say, the one located in ~/.config/cairo-dock/current_theme/icons.

so either :
- in the config, remove this theme from the list of icons themes (in "Icons" tab)
- in ~/.config/cairo-dock/current_theme/icons remove the firefox.svg icon or change it.

Messing with the config files probably isn't a smart thing for me to do.  I don't really want to mess it up.

Thanks anyway though :D

---

### Post by fabounet on 2009-03-17
it is not messing, but choosing the icon set
you should choose the icon set you want in the config, it exists for this purpose ^_^

---

### Post by blackened on 2009-03-17
> **Ash R said:**
> Messing with the config files probably isn't a smart thing for me to do.  I don't really want to mess it up.

Thanks anyway though :D

Why not make a backup and start tinkering? What's the worst that could happen, you break it? But that's the best way to learn.

---

### Post by Zachx65 on 2009-03-30
I think you want to do something like this..

1.) Assuming you've got a nice icon theme([_Gnome-Noble_]("http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562") for me) installed somewhere like /home/username/.icons, go to Cairo's advanced configuring menu. There you want to remove the local theme as fabounet said. Then add the folders from the icon theme(I added all the folder seen in the second screenshot just to be safe). You'll want a theme with scalable icons so they don't get blurry when they magnify on mouse over.

2.) Check "Overwrite X icons with launchers' one."

Hope this helps, it fixed the firefox icon problem for me. Unfortunately I'm still having some trouble, as seen in the last screen shot. I don't know where it's getting the ugly VLC or Cairo icons. I'd like to replace them. Sorry for the jumbled post. The screen shots are in order of the instructions.

---

### Post by fabounet on 2009-03-30
how did you create the VLC launcher?
there is a class mismatch between the launcher and the appli.
you should drop the actual launcher out of the dock, then add it again from the Applications Menu.

---

### Post by Zachx65 on 2009-03-30
> **fabounet said:**
> how did you create the VLC launcher?
there is a class mismatch between the launcher and the appli.
you should drop the actual launcher out of the dock, then add it again from the Applications Menu.

The first time I clicked add manual launcher. I also just tried the way you explained but ended with the same results.

Edit: The Cairo theme I'm using now doesn't add another icon to the dock, instead adding a halo underneath the icon if the application is running(except for VLC!) Any ideas on how this could be done?

---

### Post by andrea000 on 2009-03-30
I thank your trying to stop the original icons from replaceing the ones you have set?am i right?If so there is a check box somewhere in the settings for that.

---

### Post by vickoxy on 2009-04-29
Hi,
i have 2 Problems (use clear theme)
1) how/where to activate these notification area in cairo-dock (this extra icons that pop up on the right side)-i noticed that sometimes i have it (bei different themes but with this i do not)
2) how to add documents/donloads  folders in cairo? Per drag and drop it won´t go.

Thanks

---

### Post by vickoxy on 2009-04-29
Ok, problem 2. solved:
[http://ubuntuforums.org/showthread.php?t=932832&page=2](http://ubuntuforums.org/showthread.php?t=932832&page=2)
This does the trick:
nautilus --browser /path/to/your/folder

---

### Post by vickoxy on 2009-04-29
But these folders are buggy: i add 4-5 folders in cairo-dock (documents, downloads...) everything works fine untill i minimize it-then all 4 folders have the same launcher (usually the lattest one activated and minimized). So, does anyone knows what the problem should be?

---

### Post by fabounet on 2009-05-01
how did you make these icons ?
if they are common nautilus launcher, then it's perfectly normal
a possible way is to use the shortcuts applet, where you can add bookmarks (the same as Nautilus)
another way is to directly drag and drop the folder into the dock.
you may probably use the Stack applet to achieve your goal too.

---

### Post by vickoxy on 2009-05-01
Actually, after reinstallation of my system i didn´t try to put folders back on dock (really do not need them-now i have some problems with plug ins...but that is some oder issue...)
*another way is to directly drag and drop the folder into the dock.* tried that, but no go...

I added the folders with nautilus -browse...

---

