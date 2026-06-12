---
title: "How to stick icons on the desktop??"
date: 2009-02-18
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-02-18
This is a silly question i know..... but i need a solution to this... 

[COLOR="DeepSkyBlue"]On my desktop i manually kept some icons (computer, firefox, etc.,). when i mount a drive from computer, the mounted  drive is shown on the desktop but when i choose "clean up by name" option from right clicking the desktop....... Then the mounted drive comes first and then the order what i previously arranged for icons..... But i need the order what i kept not to change and the mounted drives to come after those icons[/COLOR]

Plz any one ... any ideas ???

---

### Post by cosine352 on 2009-02-18
just drag and drop

---

### Post by chinmaya_n on 2009-02-18
no....... i dont mean how to create a desktop icon !!! 

I wanted to stick icons on the desktop even when a drive is mounted ..... I mean the mounted drive icon is  overlapping on the other icons i kept.......... then i use the option "clean up by name" by right clicking on the desktop....... Then the order changes from what i kept previously!!:( 

( i mean the order i preferd First: computer, Second: Home, Third: Firefox, etc., Last: the mounted drives)

The order it is showing is (First: the drives mounted, Second: the order of its preference from the remaining icons)

---

### Post by Therion on 2009-02-18
I think I understand what you're asking and I'm not sure there's an easy way to do what you want.

Would it help if the mounted drive icon simply did NOT show on the desktop?  That's do-able and it sounds like it would solve your problem.  The mounted drive would still show under your Places menu of course, just not on the desktop.

---

### Post by mcduck on 2009-02-18
If you enable the computer, home etc. icons from gconf-editor instead of making them as desktop links they will be automatically arranged before mounted drives.

However I don't think there's any way to get application launchers to be arranged before drives and system icons. (It's not very common to even have program launchers on desktop in Linux).

Anyway, to enable the built-in desktop icons for computer, home etc. press Alt-F2 and run "gconf-editor". Use that to browse to apps/nautilus/desktop and enable the icons you want.

---

### Post by cosine352 on 2009-02-18
or you can disable the volume to be seen on the desktop. This way desktop can be kept cleen. 

In terminal
> gconf-editor

than

> apps --> nautilus --> desktop 

In the right uncheck the box for 'volumes_visible'

---

### Post by chinmaya_n on 2009-02-19
Its working but it is only for the default icons given in "gconf-editor"...... for the other icons cant we do it ??????

and now i've got another problem ....... i thought of checking what happens if the value given for "computer_icon_name" is changed to 1 from "no value" ....... i changed then it showed the error below:: 
(( NOW I COULD NOT SEE ANYTHING ON DESKTOP....... I CANT EVEN RIGHTCLICK ON IT !!!!!)) i could not change that to novalue again so i kept 0 but no use!!??

It is showing in a window:
"An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly." 

and when i click details it is showing:
```
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
```

any one plz help ????????

---

### Post by chinmaya_n on 2009-02-19
I could find a similar problem in the thread here
([http://ubuntuforums.org/showthread.php?t=663179](http://ubuntuforums.org/showthread.php?t=663179))

But i could understand nothing!!!! what does he mean by creating a new account??

---

### Post by chinmaya_n on 2009-02-19
I tried this from seeing the thread here:
[http://ubuntuforums.org/showthread.php?t=215060](http://ubuntuforums.org/showthread.php?t=215060)

```
gconftool-2 --recursive-unset /apps/nautilus/desktop
```
```
gconftool-2 --recursive-unset /apps/nautilus
```

All the values were reset to "no value" but The desktop is not working !!??

plz help!!

---

### Post by chinmaya_n on 2009-02-19
I restarted my computer ....... everything solved!!!!! :popcorn:

Now back to my home question....... how can i fix the icons which are not listed in the gconf-editor...????

plz anyone help~!!

---

### Post by chinmaya_n on 2009-02-20
Yes i got what i wanted to some extent .......... i mean the icons present in the gconf-editor. But what ab't the other icons ???

plz help me...!!!;)

---

### Post by mcduck on 2009-02-21
I don't think there's any way to do that. Program launchers are just files in the desktop directory, just like every other file you put on your desktop, and there's no way to manage them in a different way from other files.

Changing this would require changing the application responsible of managing the desktop, Nautilus. If you are good with programming, you can do that yourself. Otherwise, the only way would be to make a request to the program's developers, but I highly doubt that they'd actually do anything about it.

---

### Post by tristancarrington on 2009-02-21
Hi you might be able to help me I have my skype file in file system and if I want to load skype I have to search can this be put onto desktop I am using Linux and it wont let me drag and drop please help this is all new to me.  Many Thanks Tristan

---

### Post by chinmaya_n on 2009-02-21
Hello Tristen 

Where is the file Skype in ur hard disk... I mean in ur /(root) directory or other partitions(NTFS, FAT32 etc.,)....Linux itself mounts the root file system but the other file systems (i mean other partitions) should be manually mounted.

So first copy ur Skype file to ur /home/USER directory then copy directly on to the desktop. If it is a independent file u can directly copy on to the desktop. If it is dependent on other files then copy all the folder(contents related to that....)Then make a copy of that.

---

### Post by blackened on 2009-02-21
> **tristancarrington said:**
> Hi you might be able to help me I have my skype file in file system and if I want to load skype I have to search can this be put onto desktop I am using Linux and it wont let me drag and drop please help this is all new to me.  Many Thanks Tristan

Please don't thread-hijack. Start a new thread with a clear title describing your problem.

> **chinmaya_n said:**
> Yes i got what i wanted to some extent .......... i mean the icons present in the gconf-editor. But what ab't the other icons ???

plz help me...!!!;)

This is not possible with the current incarnation of Nautilus. The functionality simply isn't there. You could always file it as a wish on Launchpad, but I wouldn't get my hopes up if I were you.

---

### Post by chinmaya_n on 2009-02-21
> **blackened said:**
> 
This is not possible with the current incarnation of Nautilus. The functionality simply isn't there. [COLOR="DarkOrchid"]You could always file it as a wish on Launchpad[/COLOR], but I wouldn't get my hopes up if I were you.

I didnt understand what do u mean by "You could always file it as a wish on Launchpad" ???

---

### Post by blackened on 2009-02-21
> **chinmaya_n said:**
> I didnt understand what do u mean by "You could always file it as a wish on Launchpad" ???

I meant that you could file a bug report on launchpad, and that would inevitably be tagged as a wishlist item and passed upstream, but will likely not be implemented any time in the near future. It's worth a shot though.

---

### Post by chinmaya_n on 2009-09-10
There is a lot of mess here i'm going to start a new thread !!

New thread:: [http://ubuntuforums.org/showthread.php?p=7927075#post7927075](http://ubuntuforums.org/showthread.php?p=7927075#post7927075)

---

