---
title: "New to Gnome, couple of questions."
date: 2007-09-26
forum: Desktop Environments
---

### Post by Freddy on 2007-09-26
Hi all.

I just recently bought myself a new computer and after seeing Gavintgolds youtube movies with Compiz-Fusion I decided that it was time for me to learn and use Gnome for a while. I have used KDE for years and the last 6 months I have spend inside Enlightenment17 (which I will never ever leave).

My qustions:

1) I compiled some applications and added them to the menu but how in earth do I change the icons of them? I browsed to the folder with my custom icons but the config menu didn't see anything inside it.

2) Is there a way to change permissions (recessively) of a mounted hdd with nautilus? the only way seemed to be with a terminal which of course will do fine, I just wondered if there was a gui way?

3) How can I delete icons on the desktop? and how can I make them unsticky? now they stick to some sort of a grid, which I despise =).

4) How can I change places in the places top menu?

5) If I install the 64 bit version of Ubuntu Gutsy Gibbon, will I be able to install and play UT3 and Quake "whatever" when they finally goes gold for GNU/Linux?

And finally a Compiz-Fusion question.

6) Since Gutsy Gibbon is soon to be released and I installed WinXP on this machine I decided to install Gutsy Gibbon to try out before the final release. Gutsy will bring Compiz-Fusion to our desktops and I decided to install compizconfig to bring me all of them nice little effects. I poked around with it and messed thing up royally, so I went up to Gavintgolds fusioncast blog and snatched his [config file]("http://fusioncast.fsckr.net/misc/gavintlgold.ini") but how do I add it to Compiz-Fusion?

I know that these are plenty of questions but bare with me =).

/Freddy

Edit:
Okey, I solved question 6 (sort of), I moved his .ini file to ~/.config/compiz and loaded up "Advanced Desktop Effects" went into preferences, changed the way CF loads config files to flat-file and choose Gavintgolds .ini file but Compiz-Fusion keeps crashing with this and with that I don't see any effects at all =(.

---

### Post by Skerit on 2007-09-26
Bear with ME while I make an attempt at helping you :P


1) Every application should have a .desktop file somewhere, in there you can edit the icons... Haven't done it much, though, not a big help here... 

2) Changing the permissions *should* be easy (even though I still prefer the terminal)

When you go to the properties of a folder, go to the "permissions" tab => Set all the permissions you want and then click the button "apply permissions to files and folders" at the bottom left corner
(Well, it's called something like that, I'm on a Dutch ubuntu here)

3) What do you mean with "deleting icons"?

To be honest, if you don't want your HDDs to show up, you'll have to google that, I don't bother with the desktop much (it's always a mess anyways) 

**However, to get rid of the grid,** you just need to right-click the desktop and untick (err, what's it called...) Untick the only thing that IS ticked, by default, it should be below the "sorty by name" option, something like "align by grid")

4) What places do you want to replace?

5) I don't have a 64 bit processor, I'm not a big gamer and chroot scares the living daylights out of me :P However, let's make a bold assumption here, if it works under kde, it should work here, too! :)

---

### Post by mcduck on 2007-09-26
> **Freddy said:**
> Hi all.

I just recently bought myself a new computer and after seeing Gavintgolds youtube movies with Compiz-Fusion I decided that it was time for me to learn and use Gnome for a while. I have used KDE for years and the last 6 months I have spend inside Enlightenment17 (which I will never ever leave).

My qustions:

1) I compiled some applications and added them to the menu but how in earth do I change the icons of them? I browsed to the folder with my custom icons but the config menu didn't see anything inside it.

2) Is there a way to change permissions (recessively) of a mounted hdd with nautilus? the only way seemed to be with a terminal which of course will do fine, I just wondered if there was a gui way?

3) How can I delete icons on the desktop? and how can I make them unsticky? now they stick to some sort of a grid, which I despise =).

4) How can I change places in the places top menu?

5) If I install the 64 bit version of Ubuntu Gutsy Gibbon, will I be able to install and play UT3 and Quake "whatever" when they finally goes gold for GNU/Linux?

And finally a Compiz-Fusion question.

6) Since Gutsy Gibbon is soon to be released and I installed WinXP on this machine I decided to install Gutsy Gibbon to try out before the final release. Gutsy will bring Compiz-Fusion to our desktops and I decided to install compizconfig to bring me all of them nice little effects. I poked around with it and messed thing up royally, so I went up to Gavintgolds fusioncast blog and snatched his [config file]("http://fusioncast.fsckr.net/misc/gavintlgold.ini") but how do I add it to Compiz-Fusion?
.

1. After browsing to correct directory you actually need to press Enter before all the icons will appear. Then you can just select the icon you want. You can also just drag&drop any iimage from desktop or file manager window to use it as icon.

2. Permissions of partitions should be configured when mounting them, in /etc/fstab, not afterwards. In case of Ext2/3 partitions you can just right-click on the mounted partition, select properties and change the permissions there. On the bottom of the window there's a checkbox that allows you to change permissions of all contained directories & files.

3. What icons are you talking about? Mounted drives? You can disable showing mounted partitions on desktop completely with gconf-editor, but that means that CD's and removable drives won't show on desktop either. To do that press Alt-F2 and run 'gconf-editor', browse to apps/nautilus/desktop and you'll find the option there.

The other way is to just mount those partitions anywhere else than inside /media.  I recommend mounting them inside /mnt. This way you can still get CD's and removable drives to show on desktop.

The option for icon alignment is in the right-click menu if I remember right.

4. The Places-menu isn't fully editable, but you can add new places & remove them through the 'bookmarks' menu in Nautilus. These bookmarks will show in Places-menu and also in the left panel of both Nautilus and the file selection dialog.

---

### Post by Freddy on 2007-09-26
> 1) Every application should have a .desktop file somewhere, in there you can edit the icons... Haven't done it much, though, not a big help here...

I meant the icon that shows up inside the Gnome menu, not the application icon itself.

> 2) Changing the permissions *should* be easy (even though I still prefer the terminal)

When you go to the properties of a folder, go to the "permissions" tab => Set all the permissions you want and then click the button "apply permissions to files and folders" at the bottom left corner
(Well, it's called something like that, I'm on a Dutch ubuntu here)

It didn't change them recessively for me. I guess this just goes smoother with KDE, it's not a biggie though.

> 3) What do you mean with "deleting icons"?

I should have written "remove" instead. Gnome places two icons on my desktop "Storage" and "Windows", I want to get rid of the Windows one. I know that I can make Nautilus to not make desktop icons but that's not what I want.

> However, to get rid of the grid, you just need to right-click the desktop and untick (err, what's it called...) Untick the only thing that IS ticked, by default, it should be below the "sorty by name" option, something like "align by grid")

Thanks, I can't understand how I could miss that =).

> 4) What places do you want to replace?

Document, Music, Pictures and Video, I doesn't use my /home for storing these kind of files so the premade folder is no use to me, I use a Storage drive and link them to /home.

> 5) I don't have a 64 bit processor, I'm not a big gamer and chroot scares the living daylights out of me :P However, let's make a bold assumption here, if it works under kde, it should work here, too! 

Yeah I know that, but does it work under a 64 bit KDE? =). This wasn't a Gnome related question, rather a GNU/Linux related one. Will UT3 and Quake "whatever" work under a 64 bit environment?

/Freddy

---

### Post by Freddy on 2007-09-26
> **mcduck said:**
> 1. After browsing to correct directory you actually need to press Enter before all the icons will appear. Then you can just select the icon you want. You can also just drag&drop any iimage from desktop or file manager window to use it as icon.

2. Permissions of partitions should be configured when mounting them, in /etc/fstab, not afterwards. In case of Ext2/3 partitions you can just right-click on the mounted partition, select properties and change the permissions there. On the bottom of the window there's a checkbox that allows you to change permissions of all contained directories & files.


3. What icons are you talking about? Mounted drives? You can disable showing mounted partitions on desktop completely with gconf-editor, but that means that CD's and removable drives won't show on desktop either. To do that press Alt-F2 and run 'gconf-editor', browse to apps/nautilus/desktop and you'll find the option there.


The other way is to just mount those partitions anywhere else than inside /media.  I recommend mounting them inside /mnt. This way you can still get CD's and removable drives to show on desktop.

The option for icon alignment is in the right-click menu if I remember right.

4. The Places-menu isn't fully editable, but you can add new places & remove them through the 'bookmarks' menu in Nautilus. These bookmarks will show in Places-menu and also in the left panel of both Nautilus and the file selection dialog.

Thanks I got a bunch of questions answered here, for that I thank you. 

1) Okey, that worked like a charm. Kind of weird though (the enter thingie before icons show I mean).

2) I know that the "right" way to mount with permissions is through /etc/fstab, I just want to learn the quirks of Gnome =).

3) Yeah my question was about my mounted drives. that was kind of a ugly solution, but absolutely not a deal breaker =).

4) Great, I could change everything I wanted to change inside the places menu, thanks.


Now it's just a couple of questions left I believe =). 

Is there a way to make "flat file" configuration to work within Gutsys Compiz-Fusion? and do 32 bit games work inside a 64 bit environment? 

/Freddan

---

