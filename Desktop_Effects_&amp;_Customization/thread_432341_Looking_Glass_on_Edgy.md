---
title: "Looking Glass on Edgy"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by kystorms on 2007-05-03
I have seen this Looking glass, and I am interested in putting it on, seems it maybe easier to do than beryl? When I tried to see ( not sure I did it correctly tho) if i have the right drivers for 3D, this is what i get

 glxinfo | grep version
libGL warning: 3D driver claims to not support visual 0x4b
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.3 Mesa 6.5.1
glu version: 1.3
lisac@lisac-desktop:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
What does this mean I need to do inorder to have 3D of any kind? I have an ATI 7000ve , 160 GB hard drive, 1.15 Ghz motherboard, 1.5 GB ram.
Also, in the how to of doing Looking Glass, it says to :

"add the following lines to /etc/apt/sources.list and then comment/uncomment the appropriate line(s)."
The lines are :

## LG3D repsoitories
 deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
 # deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
 # deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib 

Now, I am not sure what I am supposed to do to "add" to the /etc/apt/sources.list, can someone point me to a step by step on what I need to do to accomplish this?

Thanks
:confused:

---

### Post by PrivatePickle on 2007-05-04
There are two ways that I know to add repositories.

1st way:  Using the terminal

Open a terminal and type

    ```
sudo gedit /etc/apt/sources.list
```

    scroll to the bottom then copy and paste the following.

    ```
## LG3D repsoitories
deb http://javadesktop.org/lg3d/debian stable contrib
# deb http://javadesktop.org/lg3d/debian testing contrib
# deb http://javadesktop.org/lg3d/debian unstable contrib
        
```

    Save the file and close gedit.

    Type each of the following into the terminal and hit enter after each.
```
sudo aptitude update
```
```
sudo aptitude install lg3d-core
```

2nd way:  Using Synaptic

     Open Synaptic Package Manager, click on settings then repositories.

     Go to the Third-Party Software tab and click on the Add button at the bottom left.

     Copy and past one of the entries from above depending on whether you wish to
       use the stable, testing or unstable repository.

     Click on Add Repository then on Close.

     Reload Synaptic then search for and install lg3d-core.

This is my first attempt at giving instructions so sorry if it doesn't actually make sense.:)

---

### Post by blackened on 2007-05-04
Looking Glass is still in very early alpha, and isn't really a usable environment yet. I found a live cd of it quite a while ago, so maybe that would work better for you, as well as give you a chance to see if you really want to go through the trouble of installing it.

---

### Post by kystorms on 2007-05-04
Okay, followed the sudo gedit /etc/apt/sources.list         instructions, but the weird thing is the list was completely empty!???

Should there not be a ton of files inside it?

:confused:

---

### Post by blackened on 2007-05-04
There should be a list of all of your current package repositories. You likely made a typo in the filename.

Copy and paste:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kystorms on 2007-05-04
I know this is not supposed to be happening, but this is what I get when i copied and pasted that last code -

$ gksudo gedit /etc/apt/sources.list
(gedit:26853): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and then the box comes up, with nothing in it at all! Completely white pages
I am a newbie but I do know that is not supposed to happen, i know there should be files in there, should i fix something first? if so, what?

thank you very much for all your help
:(

---

### Post by PrivatePickle on 2007-05-05
> (gedit:26853): GnomeUI-WARNING **: While connecting to session manager:

As for that error, I get it whenever I use gksudo to open gedit so I just use sudo and it works fine.
For the best explanation for the difference that I can find check the following link.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


For your problem with the repositories I would go to ubuntuguide.org for edgy at the following link and
follow the instructions for adding extra repositories to make sure that everything is as it should be
to start with then also add the one for looking glass at the bottom.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories)

You will need to run sudo aptitude update or click on reload in synaptic after saving and closing
your sources.list file.

I hope this gets it sorted out.

---

