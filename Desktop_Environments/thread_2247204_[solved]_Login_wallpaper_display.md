---
title: "[solved] Login wallpaper display"
date: 2014-10-06
forum: Desktop Environments
---

### Post by ciryon03 on 2014-10-06
Hello

I've already a post on the french official ubuntu community forum :  [http://forum.ubuntu-fr.org/viewtopic.php?pid=18218441#p18218441](http://forum.ubuntu-fr.org/viewtopic.php?pid=18218441#p18218441) but had no answer so far.

I'm using Ubuntu 14.04 64 bits.

When I change my desktop wallpaper, the login wallpaper default to the default one (the orange background wallpaper) and I don't know how to change this.

I looked at the ubuntu software and lightdm is already installed.

Lauching lightdm from the console told me Root was needed so I used the command with sudo and got this : 
```

yann@yann-desktop:~$ sudo lightdm
[sudo] password for yann: 

** (lightdm:20045): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed

** (lightdm:20045): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
```

I tried to install simple-lightdm-manager from the PPA but the PPA is not reachable and I contacted the PPA creator.

I tried several others things : 
- gksudo gedit /etc/lightdm/unity-greeter.conf : a blank file appears
- I tried install ubuntu-tweak but it seems to not exist anymore on the Ubuntu repository

Thanks for your help !

---

### Post by deadflowr on 2014-10-06
Lightdm is a service, so you would want to start it with
```
sudo start lightdm
```
(or restart, or stop; depending on which you would be incline to need to do)

Lightdm changed, the old version would have files such and /etc/lightdm/unity-greeter.conf. But the new version used in 14.04 uses a different approach.
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

For the wallpaper, are these wallpapers you set personal, from within your Pictures folder, or are they system wallpapers?
If from within your own Pictures folder you need to set the permissions of the folder/file to access for everybody(owner,group,and others; I believe "others" is what the system needs set to be able to see the image).

if they are system wallpapers, then a setting needs adjusting, which at the moment I cannot remember...
(I think it's the setting in dconf: org.gnome.desktop.Background show-background, or something like that, but I'm not so sure)


edit: Adding: I don't think Ubuntu Tweak has ever been in the repos...

---

### Post by ciryon03 on 2014-10-06
Thanks for your reply

I looked at [https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper](https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper)

I tried to edit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override but gedit open a blank file so I don't know if it still applies.

The wall paper is from the steam directory : personal folder\.local\share\Steam\userdata\184051923\760\remote\313730\screenshots

The permission of that folder is for me "create and delete files" for my user's group the same thing and for others "acces to files".

---

### Post by grahammechanical on 2014-10-06
We can find Ubuntu wallpapers at /usr/share/backgrounds.

The default wallpaper is called warty-final-ubuntu.png. It will be the default desktop wallpaper and the default background image at the login screen.  Unless we select another wallpaper using the Appearance utility. The wallpaper we select for a background image then becomes the background image for the log in screen.

If we choose the wallpaper slide show to have a rotating desktop background then the login screen background becomes warty-final-ubuntu.png again.

This is how it should work. Is it not working like this on your OS?

I suggest that with 14.04 it is better to use Unity Tweak Tool instead of Ubuntu Tweak Tool. 

unity-greeter.conf is not in /etc/lightdm/. So, by running that command you are telling Gedit to create a new file called unity-greeter.conf at /etc/lightdm/ which will of course be an empty file.

And that is all the information that I can offer.

Regards.

P.S. Gedit will open a file at a location that we specify if, and only if, the file is present at that location. If Gedit opens an empty file, then the file specified is not at that location and we have just created a new file at the location. It is best to always check to see if the file actually exists at that location or use the Gedit open>browse feature to locate the file. Especially when we are editing system files.

---

### Post by deadflowr on 2014-10-06
> **ciryon03 said:**
> Thanks for your reply

I looked at [https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper](https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper)

I tried to edit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override but gedit open a blank file so I don't know if it still applies.

The wall paper is from the steam directory : personal folder\.local\share\Steam\userdata\184051923\760\remote\313730\screenshots

The permission of that folder is for me "create and delete files" for my user's group the same thing and for others "acces to files".

copy the image into your pictures folder.

---

### Post by ciryon03 on 2014-10-06
The wallpaper I have choosen appears in the Appearance utility but still not on the log in screen.

---

### Post by ciryon03 on 2014-10-06
> **deadflowr said:**
> copy the image into your pictures folder.
Done, its did nothing until I selected the copy to be the wallpaper and this time it worked, thank you.

---

