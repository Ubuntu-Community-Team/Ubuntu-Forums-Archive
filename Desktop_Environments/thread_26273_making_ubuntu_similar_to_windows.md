---
title: "making ubuntu similar to windows"
date: 2005-04-12
forum: Desktop Environments
---

### Post by jordanau on 2005-04-12
Ack!! I am going to get some crazy responses about this. Just read my entire post :-)

My family's laptop hard drive went out so i took it back to the university with me and have put ubuntu on it instead of windows ME. There is just no comparison in quality. Ubuntu is SO much better. The computer will require less maintance, be more secure, etc. No viruses, spyware, malware. I have done the "hard" part of setting it up, they will just be users. 

Unfortunately, I am the only one in the family that is good with technology. Nobody else can handle a switch from windows to linux. (Even worse, I live 2 hours away so i can't troubleshoot all problems). 

I already have gotten the laptop up and running smoothly, (which involved putting in the ubuntu cd and hitting enter every once and a while :smile: )

What I need is tips from y'all about making things look and feel like windows on the surface while having ubuntu under the hood. 
-I have moved my gnome menubar to bottom of screen 
-I will change the theme to be like windows

Does anyone know how to 
-place a computer icon on the desktop
-put the trash bin on the desktop
-disable workspaces <--- trust me it is too much for them  :roll: 

Also anymore suggestion on how to do this will be greatly appreciated. 

By the way I run ubuntu on my computer and it looks and feels 100% linux, I love gnome, I just dont think that the family can handle it.

Final question, can i download packages from apt-get and not install them but store the packages themselves in a folder to be burned to CD. I can't connect the laptop to the internet presently.

BTW, if this is in the wrong forum, feel free to move it mods. 

Thank you
Jordan

---

### Post by Xgkkp on 2005-04-12
Here are a few suggestions:

I havn't tried it myself, but [http://www.xpde.com/](http://www.xpde.com/) is a window manager which tries to look and fell exactly like windows. However you will lose a lot of the gnome ubuntu enhancements.

apt-get has the option -d which just downloads the packages, doesn't install them (apt-get --help)

You can disable workspaces by removing the workspace switcher, as far as I know. right click on it and say "remove from panel"

also if they have the internet you could always configure the machine to be able to be administered remotely.

---

### Post by shakin on 2005-04-12
-place a computer icon on the desktop

Right-click on desktop and select Create Launcher. Type 'My Computer' for the name and 'nautilus computer:///' for the command. Select the icon... there are a few default icons that look a lot like the Windows My Computer icon.


-put the trash bin on the desktop

ln -s ~/.Trash/ ~/Desktop/Recycle\ Bin

Now right-click on the desktop link to get to properties and select a custom icon to make it look like a trash bin. Actually, this only works for viewing the trash because you can't right-click and empty it. You can still empty it after you click the icon by going to the File menu, so if they never emptied via right-click on Windows this shouldn't be a problem.

-disable workspace

Right-click on the workspace switcher then go into preferences to reduce the number to one workspace. Then right click the workspace switcher again and click 'remove from panel'.


You may also want to consider installing kubuntu-desktop. KDE is a bit more like Windows.

---

### Post by pip on 2005-04-12
It's probably better to add the trash and computer icon in the way it is shown here:

[http://www.ubuntuguide.org/#showdesktopicons](http://www.ubuntuguide.org/#showdesktopicons)

---

### Post by idn on 2005-04-12
Yeah I was going to try out XPde just out of curiousity more than anything, however I am sure gnome would be easier as XPde hasnt released an entirley stable version 

-place a computer icon on the desktop
-put the trash bin on the desktop
This can be done in Applications ->System -> Config editor

then goto apps -> natilus -> desktop 

you can add a home and tash icon, even change the name to recycle bin if you want to :)

-disable workspaces <--- trust me it is too much for them
just get rid of the widget from the gnome panel, this should solve the problem

---

### Post by shakin on 2005-04-12
[QUOTE=Xgkkp]also if they have the internet you could always configure the machine to be able to be administered remotely.[/QUOTE]

As someone who admins my mother's machine remotely, I highly recommend running sshd and vnc so you can go in and fix things when necessary. I even take remote backups of my mother's documents and email using rsync (with --rsh=ssh option). She just pays for a $20/month 'Lite' cable internet connection instead of the $15/month she was paying for dial-up. The extra $5 is worth it for not tying up the phone line and the extra speed anyway.

---

### Post by shakin on 2005-04-12
[QUOTE=pip]It's probably better to add the trash and computer icon in the way it is shown here:

[http://www.ubuntuguide.org/#showdesktopicons](http://www.ubuntuguide.org/#showdesktopicons)[/QUOTE]


Yep, that's definitely better for trash. No difference for the computer icon, though, exept it's easier to understand how to do it for people not familiar with links.

---

### Post by jordanau on 2005-04-12
I appreciate the suggestions, 
I especially like the remote administration, I will definately read into that. 
I will also look into VNC. I have done it with windows, so I am sure I can handle it with my linux boxes. 

About the workspace switcher, I should have been more clear, I know how to remove it from the panel. I need to get it out of the right click menus and everything. The thought of dozens of programs running in workspaces 2, 3, and 4 because "the window just suddenly disappeared" just scares me.

---

### Post by jonny on 2005-04-12
Right-click on the switcher and select preferences.  Reduce the number of workspaces in the dialogue.

---

### Post by shakin on 2005-04-12
[QUOTE=jonny]Right-click on the switcher and select preferences.  Reduce the number of workspaces in the dialogue.[/QUOTE]

Yep, I just tested this. When you reduce the number of workspaces down to 1 before removing it from the panel, the menu items disappear.

---

