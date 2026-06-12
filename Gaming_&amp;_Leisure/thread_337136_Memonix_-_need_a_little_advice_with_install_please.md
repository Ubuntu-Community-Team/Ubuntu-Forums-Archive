---
title: "Memonix - need a little advice with install please."
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by stoer on 2007-01-12
Hi all,
I found this gem nestling in the 'Native games' list.  And my son, aged 4, adores it!
Now, i've installed this game into my /home folder.  My son normally plays using my account so not a prolem.  However, yesterday i set him up with his own account - he can't write yet but he can 'type' his name and hit the 'enter' key...
Which would be a better folder choice when installing games for more than one user?
And can anyone help me with adding this game to the 'Applications/Games' menu and/or adding a shortcut to his desktop.
I tried creating a launcher, it doesn't work from his account or from my own account, i'm afraid i don't know why... ](*,)  
The readme that comes with the game tries to explain a few things, but is just giving me a headache after an hour of trying to sort this out myself, sorry but I'm as green as the grass arround linux.
Any help or tips will be very greatly appreciated, now let me go and find the paracetamols...

README

Memonix

Brain teasers, puzzle and memory games for kid's in one pack!

------------------------------------------



Runtime dependencies:



libSDL (ver 1.2.6+), libsdl-image (ver 1.2.4+), libsdl-mixer (ver 1.2.6+), libogg (ver 1.1+), libvorbis (ver 1.1+), libvorbisfile (ver 1.1+), libjpeg (ver 6b+).





Requirements:



CPU 300+ Mhz, 64 MB RAM, 3D acceleration video card with OpenGL, mouse.

Recommended: sound card.





Game launch and addons installation:



Installation:

- unpack the game files into your favorite folder

- launch the game:

   /game/bin/folder/Memonix [optional parameters]

   where,   

   /game/bin/folder/Memonix - the game executable file

  optional parameters:
    --dir=/game/data/folder/ - folder with gamedata.vfs file

Addons:

- download additional game addons [http://www.viewizard.com/memonix/addons.php](http://www.viewizard.com/memonix/addons.php)

- copy this files into folder whit gamedata.vfs file



Note: game settings file stored in the "$HOME/.memonix" folder.










--------------------------------------------

Viewizard Web Site [http://www.viewizard.com/](http://www.viewizard.com/)

---

### Post by MontanaMax on 2007-01-12
I'm not an "expert", but my strategy for this so far as been to install the applications under the /OPT directory, and then use chgrp to grant permissions to all the files in the /OPT directory the the users group. Then each users menu can be created with items pointing to the binaries in the /OPT directories, or use ln -s to create symbolic links in the /usr/sbin directory to the real executables

There is probably a more elegant way of doing this, but this is the best I've come up with so far. :)

(and as I read this again, I can see I've somehow become one of those confusing people that I didn't understand 6 months ago, and sometimes don't understand now. If you still have any questions, please let me know and I'll try to come up with a few scripts to help you out).

Good luck!

---

### Post by stoer on 2007-01-12
> **MontanaMax said:**
> I'm not an "expert", but my strategy for this so far as been to install the applications under the /OPT directory, and then use chgrp to grant permissions to all the files in the /OPT directory the the users group. Then each users menu can be created with items pointing to the binaries in the /OPT directories, or use ln -s to create symbolic links in the /usr/sbin directory to the real executables

There is probably a more elegant way of doing this, but this is the best I've come up with so far. :)

(and as I read this again, I can see I've somehow become one of those confusing people that I didn't understand 6 months ago, and sometimes don't understand now. If you still have any questions, please let me know and I'll try to come up with a few scripts to help you out).

Good luck!

Thanks for the reply.
ok. I've moved the folder Memonix from my home dir to /opt
I changed the permissions, but used sudo chmod -R 0777 /opt/Memonix  - something i've used before (or is this not the right way???). Afraid i didn't know the syntax for using chgrp](*,) 

A symlink:
ln -s /path/to/real/file /path/to/non-existant/file

<path to real  file> = /opt/Memonix/Memonix

<path to 'non existant file>'?????? = what the heck is non existant file and where does it go?

---

### Post by MontanaMax on 2007-01-12
Once again, I'm not an expert - but I did just try this on my machine and it worked just fine.

I downloaded the file memx16.tar.gz to my home directory

The I entered these commands to switch into and install the program into the /OPT directory:

```
 

cd /opt
sudo tar -xzvf ~/memx16.tar.gz


```

After doing this, I was able to double-click to execute the program using a file manager in both my account and my daughter's and it ran. Looks pretty cool too - I'm going to show it to her tomorow :)

Next I created a shortcut on my daugher's desktop by right-clicking and picking "create new... Link to application"

The four key items on the "short cut" link creation were:

1. Click on the default icon to change it to one in the /opt/Memonix directory
2. On the permissions tab, check the 'executable" box
3. On the Application tab, set the "command" to be '/opt/Memonix/Memonix'
4. On the Application tab, set the "work path" to be '/opt/Memonix'

This avoided the messy group stuff I was doing before. I think the situation you're in now is avoided by using the "sudo tar" command directly into the /opt directory. I think that makes it inherit permissions from the /opt directory, which is already setup correctly. By doing the first into into your home directory, the file permissions were origionally set to your user, and I'm not sure what the secret number code would be on the chown command to get them set correctly for the type of multi-user access you're looking for. My 2 cents would be to delete the current directory entirely and start the install over - hopefully that will reduce your frustration level. :)

Good luck!

---

### Post by stoer on 2007-01-13
> **MontanaMax said:**
> Once again, I'm not an expert - but I did just try this on my machine and it worked just fine.

I downloaded the file memx16.tar.gz to my home directory

The I entered these commands to switch into and install the program into the /OPT directory:

```
 

cd /opt
sudo tar -xzvf ~/memx16.tar.gz


```

After doing this, I was able to double-click to execute the program using a file manager in both my account and my daughter's and it ran. Looks pretty cool too - I'm going to show it to her tomorow :)

Next I created a shortcut on my daugher's desktop by right-clicking and picking "create new... Link to application"

The four key items on the "short cut" link creation were:

1. Click on the default icon to change it to one in the /opt/Memonix directory
2. On the permissions tab, check the 'executable" box
3. On the Application tab, set the "command" to be '/opt/Memonix/Memonix'
4. On the Application tab, set the "work path" to be '/opt/Memonix'

This avoided the messy group stuff I was doing before. I think the situation you're in now is avoided by using the "sudo tar" command directly into the /opt directory. I think that makes it inherit permissions from the /opt directory, which is already setup correctly. By doing the first into into your home directory, the file permissions were origionally set to your user, and I'm not sure what the secret number code would be on the chown command to get them set correctly for the type of multi-user access you're looking for. My 2 cents would be to delete the current directory entirely and start the install over - hopefully that will reduce your frustration level. :)

Good luck!

Many thaks for this, works a treat! 
Had me scratching my a head for a while until i realised you were using KDE and  Edgy.
In Gnome i miss this command, "create new... Link to application"
Fortunately, i have both Gnome and KDE to play with ;) 
After that it was just as easy as you said.
Cheers!

---

