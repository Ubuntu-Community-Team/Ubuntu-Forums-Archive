---
title: "Srange space problems on my memroy stick"
date: 2006-01-03
forum: Desktop Environments
---

### Post by lgmdaniel on 2006-01-03
I was using my memory stick to transfer files (intel wireless driver) from my Ubuntu session to a laptop (XP) that hadn't had its network card drivers installed. The files copied over the first time just fine with Ubunta auto mounting the memory stick. But when I came to delete the files to put another one on (its only a little stick) it stuck it in the 'trash can' which was hidden. I cleared this out, but still the memory stick showed only half the space free. The trash can was empty and there where no hidden files using up the space. So I rebooted into XP and found that even then memory stick showed only half its space free. A format of the stick seemed to fix the problem, but it was a little odd. Has anyone else enountered this? Its was in Gnome, though I am now running KDE.

---

### Post by steve.horsley on 2006-01-03
Only one theory. Nautilus seems to have a bug whereby it won't show files ending in a tilde (~) even if you tell it to show hidden files. That could explain why you couldn't see it in nautilus, but doesn't explain not seeing it in windows, unless it was also in a folder that windows hides, like the recycler or (I'm not sure of the name) the "system info" folder.

---

### Post by lgmdaniel on 2006-01-04
The things is I always have hidden files shown.. It did seem very bizzare

---

### Post by mcduck on 2006-01-04
yes, but files with ~ are not hidden files but backup files.. And there's our problem..

In nautilus there's no option to show hidden _and_ backup files, but I remember seeing the setting for showing both somewhere, most likely in the configuration editor. I'll have a look at that when I get home :)

If you don't want to wait, open configuration editor (in Applications/System Tools/Configuration Editor) and browse to apps/nautilus/ and look if you find option to show them.

---

### Post by lgmdaniel on 2006-01-04
In that case how did those files end up hidden on my memory stick.. as all I did was put them on the stick. Then try to delete them and then empty the trash can. What part of these actions would have caused the file to end up as a hidden backup file?

---

