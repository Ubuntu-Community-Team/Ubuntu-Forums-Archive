---
title: "Display Problem"
date: 2005-08-10
forum: Desktop Environments
---

### Post by Jack Ouzzi on 2005-08-10
I have similar problems (I think) to the 'Monitor Refresh Rate' thread.

Just loaded Kumbutu today on a dual boot XP machine in it's own partition.

ALL works fine .... both dual boots work, as does Kumbutu BUT - I can only get the default 640x480 resolution with no alternative in the settings. I have been advised by others to edit the config files (fine) but one states XF86Config-4 and the (above mentioned) thread says xorg.conf none of which I can find to edit ..... where are they and how to edit please  ](*,) 

Dell E173FP monitor - integrated (is this the problem?) Intel 82865G graphics card running at 1024x768 refresh @ 75Hz in Windoze XP  :neutral:

---

### Post by heimo on 2005-08-10
I believe you should edit /etc/X11/xorg.conf file. I've collected some instuctions on this post:

[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

If you get any problems, don't hesitate to ask.

And welcome on Ubuntuforums!

---

### Post by Jack Ouzzi on 2005-08-10
Thanks for the welcome heimo. I have tried the sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf_backup  line but got a message saying 'unable to find file' HOWEVER, being an old fart I will try once again and report back ;-)

---

### Post by heimo on 2005-08-10
Remember that unix filesystems are casesensitive (upper and lowercase characters do matter). So X11 and x11 are two different names.

---

### Post by Jack Ouzzi on 2005-08-10
[QUOTE=heimo]Remember that unix filesystems are casesensitive (upper and lowercase characters do matter). So X11 and x11 are two different names.[/QUOTE]

Oh come on heimo ..... I KNEW that ... :---)    :roll: 

Er right, now that I have got to the file AND edited it, how do I save it. I am using the Konsole Terminal Program and GNU nano .... (not the best editor in the world) how do I save the flaming changes  ](*,)

---

### Post by heimo on 2005-08-10
I have to admit, I never use nano... ;) Erhm... but those are my instructions... So let's see... (I wish I were on a Linux computer at the moment) ... I'd try ctrl+x, if file is not yet saved, it probably asks if you want to save. Something like that. On vim (my favourite editor), I'd enter :wq to write and quit.

EDIT: online help in nano: ctrl+g (ctrl+x exits)

---

### Post by Jack Ouzzi on 2005-08-10
[QUOTE=heimo]I have to admit, I never use nano... ;) Erhm... but those are my instructions... So let's see... (I wish I were on a Linux computer at the moment) ... I'd try ctrl+x, if file is not yet saved, it probably asks if you want to save. Something like that. On vim (my favourite editor), I'd enter :wq to write and quit.

EDIT: online help in nano: ctrl+g (ctrl+x exits)[/QUOTE]
 OK so how to I save it in Vim?? It appears as a read only file ..... and you can't change read only files ..... can you?

---

### Post by heimo on 2005-08-10
I can't recommend vim for this purpose, unless you already know how it works. Don't get me wrong, I love this editor, but it just has a steep learning curve. But you would hit esc to enter normal mode, and type *:wq* [enter]. That's it. But ... use nano or pico or kedit or gedit... or joe.

You need to use sudo or run editor otherwise with root privileges to be able to save. *sudo nano /etc/X11/xorg.conf* prompts for your password and runs editor with root privileges. Now you can save over the original file.

Oh, and if I were you, I'd train how to do this in console (hit ctrl+alt+F1 and ctrl+alt+F7 to change between first virtual console and X), so if you run into problems, you can do it without graphical user interface. Mainly you want to be able to copy the backup file over the current configuration file and restart kdm (in Gnome environments this is gdm). *sudo /etc/init.d/kdm restart*

---

### Post by BArS on 2005-08-10
Try this [http://www.x.org/X11R6.8.2/doc/i810.html](http://www.x.org/X11R6.8.2/doc/i810.html)

---

