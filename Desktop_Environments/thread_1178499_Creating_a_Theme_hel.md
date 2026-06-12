---
title: "Creating a Theme hel"
date: 2009-06-04
forum: Desktop Environments
---

### Post by Ac1ds0ld13r on 2009-06-04
I know there's a thread for this somewhere, I was looking at it last night on another computer, but for the life of me, I can't find it.


So, I'll ask for help and I hope this is the place for it:

I DLed a bunch of window borders, icons, etc... last night and it seems I need to turn them into a theme (?) before I can use them? I'm using Jaunty and everything has been easy enough so far. 

I just cant figure out where I need to install / put the items to pack them into a theme or how to be able to use them. I've tried drag-n-drop that I've seen suggested elsewhere, and it worked with my Login screen.

Please help. I've been looking for hours and I feel like a dolt :(

---

### Post by mcduck on 2009-06-04
No, you don't need to turn the individual theme components into a theme to use them.

Just go to System/Preferences/Appearance, and on the Theme-tab click the Customize-button. Now you can select from all available theme components.

..of course you *can* save the resulting combination as a theme, if you want.

(to install different theme components just drop the archives to the Theme window. Alternatively you can extract the theme files by hand, GTK2- and Metacity themes into ~/.themes directory, and icons into ~/.icons directory.)

---

### Post by Ac1ds0ld13r on 2009-06-04
Thanks!

That definitely got me closer to what I was going for. 

Some of the images aren't showing up the way they should though :(

Mainly my icons. I DLed some cool looking sketchy ones and they're showing the defaults. I'm going to check the file again and make sure the package actually had what it said. 

Any idea why I would get an error telling me one is an invalid theme? Its some window borders, but all of them are .tar.gz files 

Thanks again for the help. Been dealing with windows for so long I feel like a newb all over again.

---

### Post by Sarai the Geek on 2009-06-04
> **Ac1ds0ld13r said:**
> 
Some of the images aren't showing up the way they should though :(

Mainly my icons. I DLed some cool looking sketchy ones and they're showing the defaults. I'm going to check the file again and make sure the package actually had what it said. 

Try copying them to the ~/.icons folder- you may need to create it if you've never installed icons before. 
Also, where did you get them from? They could have been packaged for another distro, which often makes them display strangely because they're not named correctly.


> **Ac1ds0ld13r said:**
> Any idea why I would get an error telling me one is an invalid theme? Its some window borders, but all of them are .tar.gz files 

Thanks again for the help. Been dealing with windows for so long I feel like a newb all over again.

Maybe it's an emerald theme? Unpack the file and take a look inside: and if it's a single file ending with .emerald, it's an emerald theme. Installation is different for said themes- check out here for more information:

[Compiz-Fusion/Emerald]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

---

### Post by Ac1ds0ld13r on 2009-06-04
I got them from art.gnome.org 

Kreski lines: [http://art.gnome.org/themes/icon?page=2](http://art.gnome.org/themes/icon?page=2)

everything else I've DLed came from there as well. 

No .emerald files either. 

~/.icons folder-   <- I'm not sure what the tilde means there. Any idea where that folder needs to go? I'm going to do a search as soon as I post this, but figured I'd go ahead and ask since I'm already in here.

---

### Post by mcduck on 2009-06-04
> **Ac1ds0ld13r said:**
> I got them from art.gnome.org 

Kreski lines: [http://art.gnome.org/themes/icon?page=2](http://art.gnome.org/themes/icon?page=2)

everything else I've DLed came from there as well. 

No .emerald files either. 

~/.icons folder-   <- I'm not sure what the tilde means there. Any idea where that folder needs to go? I'm going to do a search as soon as I post this, but figured I'd go ahead and ask since I'm already in here.

"~" means your home directory. For example my user name is mcduck, so "~/" is the same as /home/mcduck/". Both ~/.themes and ~/.icons are hidden directories so you need to set the file manager to show hidden files tos ee them(shortcut is Ctrl-H).

---

### Post by Ac1ds0ld13r on 2009-06-04
Awesome thanks everyone.

And after getting in there and looking around I think it's just a bad batch of images or something in that particular icon set. I just tried another and everything is fine.

---

### Post by Sarai the Geek on 2009-06-04
> **Ac1ds0ld13r said:**
> Awesome thanks everyone.

And after getting in there and looking around I think it's just a bad batch of images or something in that particular icon set. I just tried another and everything is fine.

Indeed, you are correct, and not the first person to have trouble with that particular icon set. All the icons are named incorrectly- presumably for a different distribution and that's why they don't show up correctly in Ubuntu.


As for your window decoration problem, why don't you upload it here or link to exactly where you downloaded it so we can see what kind of theme it is. Then we can instruct you on how to properly install it.

---

### Post by Ac1ds0ld13r on 2009-06-04
Thanks, but I got it sorted. For some reason they weren't showing up right away as a viable option. Not sure what that was about, but they're in there now and I'm using them. :D

---

### Post by Sarai the Geek on 2009-06-04
> **Ac1ds0ld13r said:**
> Thanks, but I got it sorted. For some reason they weren't showing up right away as a viable option. Not sure what that was about, but they're in there now and I'm using them. :D

Must have been a gtk theme. Glad you got it sorted out!

Cheers-

---

