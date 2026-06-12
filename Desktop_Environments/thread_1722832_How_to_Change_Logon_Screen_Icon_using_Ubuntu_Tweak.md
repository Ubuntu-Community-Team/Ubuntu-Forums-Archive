---
title: "How to Change Logon Screen Icon using Ubuntu Tweak??"
date: 2011-04-06
forum: Desktop Environments
---

### Post by plenthoz on 2011-04-06
How to Change Logon Screen Icon using Ubuntu Tweak??

i've only able to change the login screen background, but if i change the icon it won't change...i've already used png images with 64x64 pixel but it doesn't have any effect...can you helpp me sir??

---

### Post by Frogs Hair on 2011-04-06
Hello plenthoz. 

Try placing the image in File system / usr / share / pixmaps /faces . You may have to use gksudo nautilus from the terminal to add to this folder .  Then migrate to that folder from Ubuntu Tweak and see if your able to open it.

I have tried to change this icon with Ubuntu Tweak  by using an image from my home folder , but it doesn't  seem to work even if the image is the correct size.

---

### Post by Krytarik on 2011-04-06
I just yet tested that with Ubuntu Tweak, and it worked out of the box, actually it was much harder to revert it to the default. ;-)

I had to take a look into its code to figure what it eventually does: It places a copy of your chosen icon into "/var/lib/gdm/.icons/CURRENT_ICONTHEME/apps/64". Those icon then overrides the default one of CURRENT_ICONTHEME.

CURRENT_ICONTHEME is usually "LoginIcons".

So check the state of those location, note that it is only readable by root.

Greetings.

---

### Post by Copper Bezel on 2011-04-06
Installing xubuntu-default-settings (or gdm2-setup ... or, in my case, both) will change those paths, and Ubuntu-Tweak won't be able to change anything. My login screen logo icon has, inexplicably, been replaced by the Faenza computer icon. I'm okay with this because it's cute, but I have no idea how it got there.

Edit: Incidentally, I thought I understood Linux filesystem organization until just now. Why are there hidden files in a folder that can only be viewed by root?

---

### Post by Krytarik on 2011-04-06
> **Copper Bezel said:**
> Incidentally, I thought I understood Linux filesystem organization until just now. Why are there hidden files in a folder that can only be viewed by root?
Yeah, I know what you mean. I had a hard time just recently to figure where the "gconf" directory of GDM is, because of that. But, actually, it follows the same policy like the "root" directory being only accessible by root, because it's actually the home directory of GDM, and those directory and its content are in fact owned by "gdm".

Also, I don't believe that the tools you mentioned affect the general policy of GDM regarding the login icon. I'm quite sure that, if you place an image with the proper format, with a name according to the Gconf key "logo_icon_name", and with a path according to the set icon theme into "/var/lib/gdm/.icons", the chosen image will be displayed.

Do you know how those tools actually work? (I'm not eager to screw up my GDM settings once more with GDM2Setup. ;-))

---

### Post by Copper Bezel on 2011-04-06
I don't have any idea how they work, but they are changing the default paths.

While I had Xubuntu-Desktop installed, the file was in /usr/share/pixmaps and called xubuntu-logo.png. GDM2 Setup allows you to set from an icon theme, and it literally looks in /usr/share/icons while needing a .svg specifically. I just set the theme in GDM2 to Login Icons, then replaced computer.svg in LoginIcons, and it changed the logo.

Those settings override /var/lib/gdm/.icons. Those folders were empty for me, and putting images in made no difference. Pointing GDM2 Setup to a nonexistent file even with icons in the gdm folder displayed the not-found icon.

---

### Post by Krytarik on 2011-04-07
Maybe because it changes the value of the Gconf key "/apps/gdm/simple-greeter/logo_icon_name"?

If the set icon name is neither present in GDM's ".icons", nor in the set icon theme or in one of its "Inherits", that results of course in an invalid icon.

---

### Post by Copper Bezel on 2011-04-07
Hey, I *was* paying attention to your post. = ) That's the first thing I checked, and I used the name from the gconf key when I put the image into the (empty) ...gdm/.icons/Faenza/apps/64 folder. (Admittedly, there *was* no LoginIcons folder in ...gdm/.icons.) Incidentally, the key value was "computer" - is that the default, too? If not, gdm2-setup changed that, as well.

I kind of *prefer* this, though, as it means that the icon is in a sane place. Admittedly, I *would* like to know just where the new path is being set, but I don't know the guts the way you do, anyway.

But I'm glad this came up, because now my login screen is just that much more Pony.

---

### Post by Krytarik on 2011-04-07
I just yet dared to run GDM2Setup once more (immediately restored my backup of "custom.conf" afterwards) and it actually turned out, that you can't even set the login icon with it! And yeah, by default it's "computer".

Upon running gconf-editor one more time, something came to my mind: Do you run it as the user "gdm", like this?:
```
gksudo -u gdm dbus-launch gconf-editor
```

---

### Post by plenthoz on 2011-04-07
> **Krytarik said:**
> I just yet tested that with Ubuntu Tweak, and it worked out of the box, actually it was much harder to revert it to the default. ;-)

I had to take a look into its code to figure what it eventually does: It places a copy of your chosen icon into "/var/lib/gdm/.icons/CURRENT_ICONTHEME/apps/64". Those icon then overrides the default one of CURRENT_ICONTHEME.

CURRENT_ICONTHEME is usually "LoginIcons".

So check the state of those location, note that it is only readable by root.

Greetings.


i've already checked it sir, and in that folder, my icon was change..but when i logout it still the same as usual (computer icon)..

---

### Post by Krytarik on 2011-04-07
> **plenthoz said:**
> i've already checked it sir, and in that folder, my icon was change..but when i logout it still the same as usual (computer icon)..
Obviously, I need more details. Please check the current state with the stated command/location, and post the details, thanks.

---

### Post by Copper Bezel on 2011-04-07
Krytarik, that didn't even occur to me - you're right, that's likely my problem. I'll try your command next time I'm using Gnome (it didn't work under Compiz Standlone and just gave me a "could not open display" error.)

---

### Post by Krytarik on 2011-04-07
> **Copper Bezel said:**
> (it didn't work under Compiz Standlone and just gave me a "could not open display" error.)
Then just try it this way:
```
DISPLAY=:0.0 gksudo -u gdm dbus-launch gconf-editor
```Assuming your display variable here, but you can check it with:
```
echo $DISPLAY
```You may also need to run this before, since it seems to be necessary in 10.10:
```
xhost +SI:localuser:gdm
```

---

### Post by Copper Bezel on 2011-04-07
Okay, added the user and ran it - thanks for the help! The same key was still "computer", so that hadn't been changed.

Do you know anything about these "schema" keys, and whether or not the path could be stored in there?

> and it actually turned out, that you can't even set the login icon with it! And yeah, by default it's "computer".

No, it just uses icon themes instead. But yeah, while I had it set to Faenza, it literally displayed the "computer" icon you'd see in your Nautilus sidebar straight from /usr/share/themes. It wasn't a copy of that file, it was *that file* - renaming it produced the not-found icon.

---

### Post by Krytarik on 2011-04-07
> **Copper Bezel said:**
> 
Do you know anything about these "schema" keys, and whether or not the path could be stored in there?
Apparently, those keys, as you see them in gconf-editor, are a by-product of the schemas, which hold the specifications of keys and their default values. Also see here:
[http://library.gnome.org/admin/system-admin-guide/stable/gconf-24.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-24.html.en)
> **Copper Bezel said:**
> 
But yeah, while I had it set to Faenza, it literally displayed the "computer" icon you'd see in your Nautilus sidebar straight from /usr/share/themes. It wasn't a copy of that file, it was *that file* - renaming it produced the not-found icon.
Sure, as is the case with any other icon theme, unless you set an icon to override these.

So, if you place a custom image file with 64x64 pixels, svg or png, into "/var/lib/gdm/.icons/Faenza/apps/64", assuming that it corresponds to the location of the default "computer."svg/png, it doesn't work?

---

### Post by Copper Bezel on 2011-04-07
Okay, excellent - I forgot the /devices/ layer in the folder tree. That worked. = ) So the icons in the gdm folder *will* ultimately override other settings, so long as the paths match up.

---

### Post by Krytarik on 2011-04-07
> **Copper Bezel said:**
> Okay, excellent - I forgot the /devices/ layer in the folder tree. That worked. = )
Great then!

---

### Post by Krytarik on 2011-04-07
I just yet took another look into the code of Ubuntu Tweak, to figure that it's only set up to handle icon themes with a directory structure similar to those of "LoginIcons".

If you set an icon theme with a different directory structure,
- it will first display the correct default icon
- let you choose your custom icon
- create the fixed directory structure in "/var/lib/.icons" and copy your custom icon there
- display the custom icon in its settings (even after relaunch)

But it will not work, because the directory structure doesn't match those of the set icon theme, like in your case, Copper.

May it be that you lost your custom icon because you only switched from "LoginIcons" to "Faenza" upon using GDM2Setup? And therefore falsely identifying GDM2Setup as the cause of the loss?

---

### Post by Copper Bezel on 2011-04-07
Yes, that would be a more accurate way of describing the situation, and my experience was the same (Ubuntu Tweak still retained its setting.) So in reality, the gconf key and the icon theme index set the path that's going to be called in the gdm folder, and if nothing is found, the icon reverts to the icon name key in the selected icon theme in /usr/share. Ubuntu Tweak can't get the middle part of that path.

Of course, they're really the last two applications meant to be used in conjunction with one another, since GDM2 for Ubuntu doesn't exist. = D

---

### Post by Krytarik on 2011-04-07
> **Copper Bezel said:**
> Ubuntu Tweak can't get the middle part of that path.

At least it doesn't try it. I guess it would need a search routine.

---

### Post by rtimai on 2011-05-29
I came across this thread by accident. I don't know if others have encountered this scenario, but I have found that in some cases when a custom icon would not be displayed, when I checked it in EOG or some other viewer, I got an error such as "not a PNG file." I found that when downloading some graphic files, sometimes they were saved as with a default .png extension even if they were a .bmp or .jpg, etc. format. Simply renaming the file or converting it to the target format enabled the icon to display. This is probably a different issue from what you're encountering in the login screen, but I thought I'd throw it in just FYI.

---

### Post by Frogs Hair on 2011-05-29
I have no problem with my latest version of Ubuntu Tweak ( 0.5.13 ) as long as the file is 64x64 .svg and you don't move the file once saved it works great . I'm not sure why I had a problem with earlier versions.

---

