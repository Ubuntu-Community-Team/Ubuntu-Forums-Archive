---
title: "Ubuntu Applications Menu Icon"
date: 2007-04-04
forum: Desktop Environments
---

### Post by yt404 on 2007-04-04
Hello

I am relatively new to linux and have seen many distributions that have a different icon for the Applications menu, I mean that this icon is a gnome logo rather than a ubuntu logo.

Can anyone tell me how to change this?

I would appreciate it

Thanks

Chris

---

### Post by yt404 on 2007-04-04
hey i found the answer to this i think, Im gonna test it really soon after a reboot.

/usr/share/icons/hicolor/48x48/apps/

the image in there distributor logo

I replaced it with my own logo of the same dimensions (bit of gimping involved) and renamed it.

Thanks to anyone who looked.

---

### Post by yt404 on 2007-04-04
didn't work, oh well if anyone knows a way i can do this i would appreciate it

I have changed icons in

/usr/share/hwdb-client/ and /user/share/icons/48x48/apps/

no luck

Something so simple turns out to be so taxing

---

### Post by jenningsghv2 on 2007-04-04
Hi there. Do a search of the "start-here.png" files and change those to the image that you want. This would be quite tedious to do in user mode--as you'd get plenty of warnings about permission access--so I'd suggest that you do it as root. Once done, log out and then back in and your changes should be reflected. If not, find out if the supplementary (or main) iconsets that your chosen icon theme is accessing include those whose "start-here" image files you have modified. If not, just add the iconset/s to the list. All that information can be found in the index.theme file in your hidden .icon folder (which is easy to show via Nautilus). Hope this helps.

---

### Post by ComplexNumber on 2007-04-04
some icon themes have their own start-here icon, but some (eg OSX) have a start-here icon but which isn't used....for some unknown reason.

i would suggest that you change one of the following if the start-here icon isnt present in the icon theme that you're using:
/usr/share/icons/Tango/scalable/places/start-here.svg

/usr/share/icons/gnome/scalable/places/start-here.svg

---

### Post by yt404 on 2007-04-04
I somehow got it to work with one of my preinstalled icon packages, it doesn't work with some others, it just displays an image with a red cross, i suspect this is because i was lazy and didnt stick to the correct image resolutions and used a 48x48 image for all of the replacements, i replaced all of the start-here.svg files.

Thanks for your help :-)

---

### Post by ComplexNumber on 2007-04-04
> it just displays an image with a red cross
it should never do that unless there is no hicolor or gnome theme installed. another possibility is that the icon has somehow become read only for non-root owners. it does that sometimes. to get round that, just type in the following command in the terminal:
**sudo chmod -R 755 /usr/share/icons/***

---

### Post by yt404 on 2007-04-05
that doesn't solve it

I am using an icon pack from gnome look Dropline Neu is what its called.

I love it but it doesn't display the icon i want i have taken a screen shot right this second you can see it with this post

any ideas as to why its showing this? it used to display the ubuntu logo, I went through and replaced distributor-logo.png and start-here.svg could it the resolution?

some of the images had smaller resolutions or larger resolutions, any ideas as to how i can fix this?

Would appreciate it mate

Cheers again

Chris

---

### Post by ComplexNumber on 2007-04-05
this is what you should be seeing(2nd screenshot).

in most cases, the distributor log is just a link to the start-here icon. its not in all themes, but in many of the 'base'(eg Tango, gnome) ones it is. the Neu theme uses the start-here icon of Tango or gnome (i think). hwoever, i've just this minute gone into  /usr/share/icons/Neu/scalable/places and made a link from the start-here, calling it "distributor-logo". and the blue gnome appears as the application menu logo. see 1st screenshot.
i would hazard a guess that one of your links to the start-here icon in either gnome or tango is broken or wrongly named or whatever..

note that you need to be root, but you may already know.

---

### Post by yt404 on 2007-04-05
The problem is

I have no Neu directoy in my /usr/share/icons/ directory, have i installed this icon pack incorrectly or something?

I simply dragged the tar file from the desktop to the theme icon manager in gnome and it loaded successfully, shouldn't this have created the Neu directory in /usr/share/icons/ ??

---

### Post by ComplexNumber on 2007-04-05
> **yt404 said:**
> The problem is

I have no Neu directoy in my /usr/share/icons/ directory, have i installed this icon pack incorrectly or something?

I simply dragged the tar file from the desktop to the theme icon manager in gnome and it loaded successfully, shouldn't this have created the Neu directory in /usr/share/icons/ ??
dropline neu IS Neu. 
if you installed it via gnome-theme-manager, it goes in .icons in your home directory.....not in /usr/share/icons.


in your case, you should be looking for **/home/<your-username>/.icons/Neu/scalable/places**

---

### Post by yt404 on 2007-04-05
Im not sure what an SVG file is (im a bit of a linux newbie)

I edited the icon myself in the gimp and exported it as a PNG file and then renamed the PNG image to be start-here.svg however, when i search for start-here.svg i get results and they all display the expected image however the type column appears to say the images i replaced are PNG files

could this be an issue?

if so, how can i change the type of these png images to svg?

cheers again mate

---

### Post by yt404 on 2007-04-05
> **ComplexNumber said:**
> dropline neu IS Neu. 
if you installed it via gnome-theme-manager, it goes in .icons in your home directory.....not in /usr/share/themes.

There is no dropline neu or neu directory in my /usr/share/icons/ directory or in my home directory?

---

### Post by ComplexNumber on 2007-04-05
a few points:

SVG = scalable vector graphics. 

if i were you, i would delete the one you have now and download the theme from [here]("http://gnome-look.org/content/show.php/Dropline+Neu%21?content=38835"), then unzip it and place it in your .icons directory in your home directory.

if the image is an svg in a directory full of svgs, do not go and replace any of them with pngs.

if its a png graphic, then merely renaming the extension is not going to change it into an an svg. it will become corrupted, which is probably why your application menu icon is not showing up properly

---

### Post by yt404 on 2007-04-05
how can i save a file as an svg file then? the gimp didn't provide the option to save it as that type?

---

### Post by ComplexNumber on 2007-04-05
> **yt404 said:**
> how can i save a file as an svg file then? the gimp didn't provide the option to save it as that type?
make it in inskcape, not gimp. gimp is not for vector graphics, its for raster or bitmap graphics.

---

### Post by yt404 on 2007-04-05
I messed stuff up quite a bit before, it works now, i replaced the start-here.svg in .icons/Neu/... and it works now

I also used inkscape to change the png image into an svg image :-)

Thanks for your help mate its been appreciated.

Cya!!

---

