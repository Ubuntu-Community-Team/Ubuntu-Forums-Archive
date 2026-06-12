---
title: "How do I keep my Desktop Wallpaper + Icons on OEM Install"
date: 2009-01-02
forum: General Help
---

### Post by badmelon on 2009-01-02
I installed Ubuntu 8.10 with the OEM install because I wanna give it to a few friends. I set a few shortcuts on the apps bar across the top and changed the wallpaper but when I hit the "prepare for  shipping to end user" and reboot it has reverted to the default Ubuntu theme ( I wanna use clearlooks) and wallpaper with no shortcuts. Is there any way to stop this?

---

### Post by DavidPcs on 2009-01-03
I have the same problem, I am testing Ubuntu in a project to develop our own preinstallation for new PCs , I had updated the system and installed some programs, and created a user account, also changed, wallpaper, and wanted to use clearlooks, the updates and programs were installed fine and technically it worked perfectly, the other changes are preferences for each user account, the changes made as user oem won't be saved for new users anymore than any other account. Obviously somewhere there is a config file for what the default desktop for a new user will be, thats what I'm looking for now, if anyone has any ideas I'm all ears..

Thanks..

David

Serinfo
Santiago de Chile.

---

### Post by loomsen on 2009-01-04
The folder /etc/skel is what you're looking for.

If you create a new user it will have a copy of this folder as its home folder.

---

### Post by DavidPcs on 2009-01-04
Thanks so much, I do see the hidden config files for bash shell, and that one can create a folder named Desktop if it does not already exist  

/etc/skel/Desktop 

and any icons placed inside the folder desktop will appear on the desktop of any new user added to the system. The one thing that it lacked was the default desktop wallpaper.
I was looking at the directory  

/usr/share/backgrounds

where the default background is called 

warty-ubuntu-final.png   

in the file manager, nautilus, I could see the preview of the file in icon mode, along with some other files of .jpg and .png,  
I am not currently ocupying the default background image, I had changed to another for my desktop in particular.  But the curious thing was that when I clicked on each file I could preview them in the default file viewer for images in nautilus,  all except for the warty-final-ubuntu.png file. An error occured when I clicked on it, said that it was not a graphic file PNG, sorry I don't have the exact quote, all my sistems are in spanish, including the error messages. But in short, nautilus said it is not file type .png and refused to open in Eye of Gnome 2.24.1 but it did open fine in Gimp, I opened Dolphin, again saw the preview of the file and it opened fine with the f-spot 0.5.0.3 of Dolphin.  
Experimentally I made a copy of the file  warty-ubuntu-final.png in a temp dir, changed the file extension from .png to .jpg and it opens in all including nautilus with previews in the file manager., weird, is png and jpg actually the same thing?????? or is it that Linux can see the file type regardless of the Windows like extension of .jpg o .png.??

Back on track to my initial objective, to change the default background in Ubuntu I renamed another graphic file of .jpg type  to  warty-ubuntu-final.png  and copied it into the directory 
/usr/share/backgrounds overwriting the original graphic file of the same name,  
now every new user gets this desktop background image for their default.

There are also many interesting config files in /etc/default 

I know this is a backdoor amatuer method to make this change, please don't get me wrong, 
I would love to know where the config file is that specifies that   /usr/share/backgrounds/warty-ubuntu-final.png is the default desktop background file.

I'm a recent convert from the world of Windows to Linux, as well as a recent convert from the english speaking world to the spanish speaking world as I live in South America now. I now use Ubuntu Intrepid on my laptop and desktop and have an external drive loaded with a version that works for me between the office and home and whereever else, I'm proud to say that I have not booted my computers into “Windows” of any kind for a couple of months now.  I mentioned before  that I'm testing Ubuntu for preinstallation in new Pcs, one of the things I am most impressed with is the amount of support and help within the community of Linux in general and Ubuntu specificially,
Thanks and sorry for posting so long...


David

---

### Post by loomsen on 2009-01-04
Sry, a lil bit on a hurry atm, maybe i'll find some time later.

Easiest way would probably be to simply configure your desktop using the gconf-editor

type the same to open it up.
[color=red]DON'T[/color] use sudo.

Just configure it how you'd want it to be.

When done, copy the folder ~/.gconf into the /etc/skel folder and you're done.

Basically every application is configurable, that's open source. You get the base and then configure it to your needs, with the benefit to never have to do it again afterwards. 

Your OS stores user specific configurations in your home folder as hidden files or folders.
Files are usually named after the app they configure appended a rc.

~/.foobarrc or ~/.foo_barrc could be such files.

Your bashrc configures how your shell behaves, you might want to add your custom bash_aliases file. I'd be pretty lost if I'd lose mine somehow.

Basically, what I want to say, just take some time and browse through your /etc folder.

In this folder the whole configuration of your system is done, and the config files are usually very well explained. just open them up and have a look, if you arent sure, close it and take the next one.

Enjoy the ride :)


*edit*

Just to make some things clearer, there are basically different levels of configuration.
The first level is what the system admin specified to be mandatory for all users.

Then, every user should be able to set his own wallpaper and dont have it reset by another user.
Bear in mind unix is a multi user OS.

And this user specific configuration (userspace config) is done in everbodys home folders.

Btw, items which are userspace configurable are placed in /usr/share :)

---

### Post by loomsen on 2009-01-04
> 
 weird, is png and jpg actually the same thing?


No it is not. Probably there was just a buggy install script that renamed the file to png tho it was jpg. Changing the extension should fix this.

You can find the key for the desired wallpaper in your gconf-editor.

```
gconf-editor
```

Then navigate to:

[[img]http://www.ubuntu-pics.de/thumb/7948/screenshot_23_80ILpc.png[/img]](http://www.ubuntu-pics.de/bild/7948/screenshot_23_80ILpc.png)

You can chose any file you want here. This will be written to a .xml file, which is placed in ~/.gconf as I wrote above.

---

