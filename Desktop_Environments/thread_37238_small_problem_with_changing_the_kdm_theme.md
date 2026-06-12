---
title: "small problem with changing the kdm theme"
date: 2005-05-26
forum: Desktop Environments
---

### Post by F for Fragging on 2005-05-26
[http://kde-look.org/content/show.php?content=24582](http://kde-look.org/content/show.php?content=24582)

I installed this theme the following way:

I extracted the simbiose dir to /usr/share/apps/kdm/themes
I edited the kdmrc file in /etc/kde3/kdm to use the simbiose theme (Theme=/usr/share/apps/kdm/themes/simbiose)

And this works. However, before it loads the kdm login screen, it still displays the kubuntu default kdm theme during a few secs that it's loading. When it finishes loading, I can see the simbiose kdm theme. And when I enter my password and press the Enter key, it displays the default kubuntu kdm theme again when it displays the splash screen.

What could be wrong? Should I delete the kubuntu dir in /usr/share/apps/kdm/themes to stop this from happening? Or do I need to edit something else in my kdmrc or another config file?

---

### Post by F for Fragging on 2005-05-26
Trashing the kubuntu dir in /usr/share/apps/kdm/themes partially worked. When I start up my PC it immediatly shows my custom KDM theme, but when I type in my password and press Enter, it shows such a default Kubuntu image again just a few secs before it shows the splash screen...

---

### Post by ludi on 2005-05-26
[QUOTE=F for Fragging]Trashing the kubuntu dir in /usr/share/apps/kdm/themes partially worked. When I start up my PC it immediatly shows my custom KDM theme, but when I type in my password and press Enter, it shows such a default Kubuntu image again just a few secs before it shows the splash screen...[/QUOTE]
 You have to disable the background option. Go to Control Center > System Admin > Login Manager > Background.
If you get in problems trying to use the admin option, close the control center and press alt+F2 then type kdesu kcontrol [ENTER], and you won't have problems.

Note: KDM support themes now, so you have to comment the theme line on kdmrc or put the path to your own theme.

> 
StdFont=Bitstream Vera Sans,10,-1,5,50,0,0,0,0,0
Theme=/home/ludi/Download/Krystal
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true


---

### Post by F for Fragging on 2005-05-26
Thank you for your help, that solved it.

---

