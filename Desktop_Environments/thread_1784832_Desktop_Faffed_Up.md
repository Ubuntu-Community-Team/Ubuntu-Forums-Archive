---
title: "Desktop Faffed Up"
date: 2011-06-17
forum: Desktop Environments
---

### Post by Kodeine on 2011-06-17
Salutations!

So ive been editing my theme. I altered the gtkrc file in the home directory and also some changes in the /apps/gwd/ dir. Upon restarting neither panels show up and i cant do anything ( shortcut keys dont work ). Probably shouldnt hae touched those files. I can i reinstall the gnome desktop manager? Ill have to boot into safe mode. Not bothered about losing panels.

Written on iphone so sorry for any spelling mistskes or poor grammer.

---

### Post by BrandonC19 on 2011-06-17
Hello! Yes you can reinstall gnome. Boot into recovery mode and select "Root shell with Networking". After the shell has loaded issue the command "apt-get install --reinstall ubuntu-desktop". That should fix you right up.

---

### Post by Kodeine on 2011-06-17
> **BrandonC19 said:**
> Hello! Yes you can reinstall gnome. Boot into recovery mode and select "Root shell with Networking". After the shell has loaded issue the command "apt-get install --reinstall ubuntu-desktop". That should fix you right up.


It hasnt worked unfortuently. When i am at my desktop i can see my wallpaper but theres also something hogging up the cpu as the fan rsther quickly starts blowing like mad.

I did do some editing to metacity to make the title bars transparent. i bet thats the dillyo. How can i boot into compiz or another window manager. ill try reinstaling metacity in the mean time. When booting into ubuntu i dont go to the login menu so i cant change the session that way. I automaticlly go to the desktop.

**Just reinstalled both metacity and compiz. To no avail. If i uninstall ubuntu-desktop and metacity then i can see the icons on my desktop. i can also create new files and run them in termimal. how can i fix this from here guys?

---

### Post by wildmanne39 on 2011-06-18
> **Kodeine said:**
> It hasnt worked unfortuently. When i am at my desktop i can see my wallpaper but theres also something hogging up the cpu as the fan rsther quickly starts blowing like mad.

I did do some editing to metacity to make the title bars transparent. i bet thats the dillyo. How can i boot into compiz or another window manager. ill try reinstaling metacity in the mean time. When booting into ubuntu i dont go to the login menu so i cant change the session that way. I automaticlly go to the desktop.

**Just reinstalled both metacity and compiz. To no avail. If i uninstall ubuntu-desktop and metacity then i can see the icons on my desktop. i can also create new files and run them in termimal. how can i fix this from here guys?Hi, disable metacity and click on reset unity and compiz in my signature then follow the instructions and reset both, hopefully that will fix you up.

---

### Post by Kodeine on 2011-06-18
> **wildmanne39 said:**
> Hi, disable metacity and click on reset unity and compiz in my signature then follow the instructions and reset both, hopefully that will fix you up.

No that doesnt seem to have worked. I tried running compiz but in terminal it said it. couldnt load the ccp plugin. with meta city when i execute it the terminal window and any other window i had open (there without the window border of course) dissapears and the only thing i can do is shut the pc down

---

### Post by Kodeine on 2011-06-18
Fixed it! Turns out it was nothing to do with Metacity or Compiz. After I deleted the 'panel' folder in the ~/.gconf/apps/ directory everything came back fine. I do remember changing the panels a bit (moving widgets and changing the colour) but why did that faf things up?

Ow well glad to be off that iPod and back on my Ubuntu-PC. Now with new keyboard! (Backspace button is same size as all other buttons, Doh!).

---

### Post by wildmanne39 on 2011-06-18
> **Kodeine said:**
> Fixed it! Turns out it was nothing to do with Metacity or Compiz. After I deleted the 'panel' folder in the ~/.gconf/apps/ directory everything came back fine. I do remember changing the panels a bit (moving widgets and changing the colour) but why did that faf things up?

Ow well glad to be off that iPod and back on my Ubuntu-PC. Now with new keyboard! (Backspace button is same size as all other buttons, Doh!).
Hi, glad you figured it out.

---

