---
title: "A few gnome related questions"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dave9191 on 2005-10-17
Hey guys, 

Ive been using kde and fluxbox for the better part of my linux life, but gnome has won me back. But I'm slowly working up a list of things I can't quite figure out. A few things for now:

1)[SOLVED] How do I move files from one place to another? In kde you left click drag and when you release it gives you a menu to choose your action from (move, copy, link).  In gnome left click dragging sometimes moves and most of the time copies. And from the documentation I get the impression that dragging moves and crtl + dragging copies. Even in windows I can right click drag to get a menu with options. I'm sure that there must be a key modifier I can hold to force moving or a way to bring up the menu. And how would I link files?

2) When I connect to a server using the link in the places menu, how long does the connection stay open for ? I dont want to remain permently connected, and the only option on the link it creates on the desktop is to unmount the location. But then to get it back I have to create a new connection and enter my details. Am I missing something here ?

3) Windows key + another key shortcuts. Not all of them work. I have things like Win + T for terminal and Win + X for maximising. But then Win + L does nothing even tho its set up for locking the screen. 

4) [SOLVED] How do I remove all the shortcuts from my desktop? I like having all the partions and connections listed in the places menu, but I prefer having a clean desktop with nothing on it. 

5)[SOLVED] How can I get the system monitor appearing with a keyboard shortcut, say Ctrl + Esc?

Thanks guys, 

Im sure there will be more on the way. 

Dave

---

### Post by bluck on 2005-10-17
[QUOTE=dave9191]
1) How do I move files from one place to another? In kde you left click drag and when you release it gives you a menu to choose your action from (move, copy, link).  In gnome left click dragging sometimes moves and most of the time copies. And from the documentation I get the impression that dragging moves and crtl + dragging copies. Even in windows I can right click drag to get a menu with options. I'm sure that there must be a key modifier I can hold to force moving or a way to bring up the menu. And how would I link files?
[/QUOTE]

ill answer this one...

you can cut n paste if you like (ctrl-x, ctrl-v) to move files.  i believe the default behaviour is to move files if the destination you're dragging to is on the same filesystem, and copy if the destination is a different filesystem. 

to link ctrl+shift+drag
you will see two linked circles on your cursor as you do it.

---

### Post by bluck on 2005-10-17
[QUOTE=dave9191]
4) How do I remove all the shortcuts from my desktop? I like having all the partions and connections listed in the places menu, but I prefer having a clean desktop with nothing on it. 
[/QUOTE]

and this one..  heh.

you should be able to highlight them and hit your delete key.

---

### Post by afonic on 2005-10-17
[QUOTE=bluck]and this one..  heh.

you should be able to highlight them and hit your delete key.[/QUOTE]

I think he asked about the partitions that appear as in the Desktop when mounted (ex. windows partitions).

This is really I pain, I rarely access them, so I don't want them on my Desktop or even in the places menu, if I discover I need I file I can just browse to where I mounted them.

Anyone figured out how to remove them?

---

### Post by dave9191 on 2005-10-17
[QUOTE=bluck]ill answer this one...

you can cut n paste if you like (ctrl-x, ctrl-v) to move files.  i believe the default behaviour is to move files if the destination you're dragging to is on the same filesystem, and copy if the destination is a different filesystem. 

to link ctrl+shift+drag
you will see two linked circles on your cursor as you do it.[/QUOTE]

I was aware of the cut and paste method, but its a bit fiddley. I was moving between file systems when I was getting the copying. Isnt there a way I can force it to move like hitting Ctrl while dragging? 

As for the linking, thanks :)

---

### Post by dave9191 on 2005-10-17
[QUOTE=bluck]and this one..  heh.

you should be able to highlight them and hit your delete key.[/QUOTE]

I tried that, it tells me that if I want to get rid of it I have to unmount it. But I dont want it unmounted, just off my desktop and in the places menu. 

Dave

---

### Post by dave9191 on 2005-10-17
[QUOTE=afonic]I think he asked about the partitions that appear as in the Desktop when mounted (ex. windows partitions).

This is really I pain, I rarely access them, so I don't want them on my Desktop or even in the places menu, if I discover I need I file I can just browse to where I mounted them.

Anyone figured out how to remove them?[/QUOTE]

They are defined in your /etc/fstab file. Just put a # infront of each line with a partion you dont want mounted to comment it out and it wont appear next time you boot. 

Dave

---

### Post by dbott67 on 2005-10-17
[QUOTE=dave9191]I tried that, it tells me that if I want to get rid of it I have to unmount it. But I dont want it unmounted, just off my desktop and in the places menu. 

Dave[/QUOTE]

To get it off the desktop, you need to use the Configuration Editor and uncheck the following key:
**/apps/nautilus/desktop/volumes_visible**

It does not appear to remove it from the "Places" menu, but it definitely removes it from the desktop.

See attached image.

-Dave

---

### Post by dave9191 on 2005-10-17
[QUOTE=dbott67]To get it off the desktop, you need to use the Configuration Editor and uncheck the following key:
**/apps/nautilus/desktop/volumes_visible**

It does not appear to remove it from the "Places" menu, but it definitely removes it from the desktop.

See attached image.

-Dave[/QUOTE]

Fantastic... exacly what i wanted, cheers. 

Dave

---

### Post by dbott67 on 2005-10-17
Glad to help.

-Dave

---

### Post by doclivingston on 2005-10-17
[QUOTE=dave9191]1) How do I move files from one place to another? In kde you left click drag and when you release it gives you a menu to choose your action from (move, copy, link).  In gnome left click dragging sometimes moves and most of the time copies. And from the documentation I get the impression that dragging moves and crtl + dragging copies. Even in windows I can right click drag to get a menu with options. I'm sure that there must be a key modifier I can hold to force moving or a way to bring up the menu. And how would I link files?[/quote]

You can get the menu by dragging with the third mouse button (the scrollwherl if you have one).


> 5) How can I get the system monitor appearing with a keyboard shortcut, say Ctrl + Esc?

You can set a keyboard shortcut to run any program, but you have to use gconf-editor to do it.

1) Open gconf-editor, via Applications->System Tools->Configuration Editor
2) Using the expanders, go to apps->Metacity->global_keybindings
3) set run_command_1 (or a different one) to "<Control>Escape" (the windows key is "<Super>", and the arrow keys are "Left" etc.)
4) go to apps->Metacity->keybinding_commands
5) set command_1 (or whichever you used in 3) to the command to run, in your example use "gnome-system-monitor"

---

### Post by dave9191 on 2005-10-17
[QUOTE=doclivingston]You can get the menu by dragging with the third mouse button (the scrollwherl if you have one).[/QUOTE]

I could have sworn I tried that, but cheers, fantastic !

[QUOTE=doclivingston]
You can set a keyboard shortcut to run any program, but you have to use gconf-editor to do it.
[/QUOTE]
Easy as pie, I should spend some time going thru the options in there :) Gnome is turning out to be pretty slick. 

Thanks 

Dave

---

### Post by afonic on 2005-10-18
[QUOTE=dbott67]To get it off the desktop, you need to use the Configuration Editor and uncheck the following key:
**/apps/nautilus/desktop/volumes_visible**

It does not appear to remove it from the "Places" menu, but it definitely removes it from the desktop.

See attached image.

-Dave[/QUOTE]

Yeah that was what I was looking for too, thanks.

---

### Post by jead on 2005-12-09
[QUOTE=dbott67]To get it off the desktop, you need to use the Configuration Editor and uncheck the following key:
**/apps/nautilus/desktop/volumes_visible**

It does not appear to remove it from the "Places" menu, but it definitely removes it from the desktop.

See attached image.

-Dave[/QUOTE]

But AFAIK this will also remove the CD-ROM and Floppies icons from the desktop. Thoses are handy icons to me.

What's have a mount point under /media is showed on the desktop.

What I did is just edit the /etc/fstab file to mount my FAT32 and NTFS partitions under /mnt instead of /media.

You have to edit the "mount point" (2nd column) option for the partition you don't want showing on the desktop.

sudo vi /etc/fstab
(or maybe gksudo gedit /etc/fstab)

Before
```

/dev/hda15      /media/veryfat  vfat    defaults        0       0
/dev/hda3       /media/xp       ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

After
```

/dev/hda15      /mnt/veryfat  vfat    defaults        0       0
/dev/hda3       /mnt/xp       ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Now only mounted CD-ROMS and Floppies are showing on my destop.

Hope that helps.

(hey, my first post! woo! :D)

---

### Post by Zonkle on 2005-12-10
Cool jead :) I think this is what I've been looking for.
I will try it as soon as I get to my computer :)

I think USB Disk will still show right ?

And what about the "Places" menu ? the still show in there?
I don't want the mounted FAT parts to show in the "Places" menu, I want them only in the Computer place .... 

Thanks.

---

### Post by jead on 2005-12-10
[QUOTE=Zonkle]Cool jead :) I think this is what I've been looking for.
I will try it as soon as I get to my computer :)

I think USB Disk will still show right ?

And what about the "Places" menu ? the still show in there?
I don't want the mounted FAT parts to show in the "Places" menu, I want them only in the Computer place .... 

Thanks.[/QUOTE]

My USB drive shows on the desktop too, yes. Nothing under /mnt shows in the "places" menu. They dont show in the "Computer" folder either. You'll have to access them by clicking on "filesystem", then navigating to /mnt to find 'em.

Wish we could create links under "Computer", would be handy.

---

### Post by Zonkle on 2005-12-11
Yes jead it worked like you said. Thanks.

And I was going to say if we could put it in "computer" place it would be very nice.

Cya ;)

---

