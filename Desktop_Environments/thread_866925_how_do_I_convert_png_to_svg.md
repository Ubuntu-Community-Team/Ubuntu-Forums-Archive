---
title: "how do I convert png to svg?"
date: 2008-07-22
forum: Desktop Environments
---

### Post by StMaus on 2008-07-22
I'm trying to add an app icon to the menu but it seems that Gnome wants the icon in svg format. I've never heard of it.
Can anyone tell me how to convert a png to an svg?

Also I'm wondering how do you go about getting an application Ubuntu installer approved? I'm a big fan of the Celtx script writing app and if it could be an Ubuntu package I wouldn't have to go through the headache of trying to make icons and such. Also, I know that my ham-handed attempt to install the app makes it run, but I'm sure I don't organize the files in the most Ubuntu correct manner.

Please be patient, I'm new to all things linux.

Thanks,
StMaus

---

### Post by Kevbert on 2008-07-22
You can do this via Inkscape (in the repos via Synaptic or Add/Remove).  Import the png file and save the file as .svg (scalable vector graphic).  You may need to adjust your page properties via File - Document Properties to your required icon size.

---

### Post by pmlxuser on 2008-07-22
have you tried opening with GIMP and saving as svg. (just to be sure)
I usually change the file extension is am sure its the right dimension.

ie. 
```

move file.png file.svg

```

---

### Post by S3loth on 2008-07-22
This might let you do it without converting to SVG.
Go to System>Preferences>Main Menu. In the left bar, navigate to where your program is (Games, Graphics, Internet, ect.) Then in the right bar, right click your application and choose Properties. Click the picture of the current icon, then in the top right window that pops-up click Browse.Navigate to the folder where you icon is, and click Open. Select your icon from the list that comes up.
SVG stands for Scalable Vector Graphics and means you can keep zooming in without getting lower quality. Did you download Celtx from their site in a package? If so, check out [this]("http://monkeyblog.org/ubuntu/installing/") to install it. Most things you can install with Synapitic Package Manager, but somethings (like Celtx) aren't in there.

---

### Post by StMaus on 2008-07-22
> **S3loth said:**
> This might let you do it without converting to SVG.
Go to System>Preferences>Main Menu. In the left bar, navigate to where your program is (Games, Graphics, Internet, ect.) Then in the right bar, right click your application and choose Properties. Click the picture of the current icon, then in the top right window that pops-up click Browse.Navigate to the folder where you icon is, and click Open. Select your icon from the list that comes up.
SVG stands for Scalable Vector Graphics and means you can keep zooming in without getting lower quality. Did you download Celtx from their site in a package? If so, check out [this]("http://monkeyblog.org/ubuntu/installing/") to install it. Most things you can install with Synapitic Package Manager, but somethings (like Celtx) aren't in there.

This is where my trouble started. I've succeeded in making the svg file but when I browse to the folder that has the icon in it the menu program refuses to see the files so I can't select them.

StMaus

---

### Post by S3loth on 2008-07-22
You should see a blank folder when navigating to it. When you click "Open" it will show the icons in the selector.

---

### Post by StMaus on 2008-07-23
> **S3loth said:**
> You should see a blank folder when navigating to it. When you click "Open" it will show the icons in the selector.

Thanks, that solved it for me. I opened the icon folder thinking I needed to select the actual file from there. Turns out you select the icon folder and then click open, duh!

Thanks for the help.

---

