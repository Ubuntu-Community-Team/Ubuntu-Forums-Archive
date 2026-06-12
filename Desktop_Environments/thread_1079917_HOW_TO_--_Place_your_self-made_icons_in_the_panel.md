---
title: "HOW TO -- Place your self-made icons in the panel"
date: 2009-02-24
forum: Desktop Environments
---

### Post by sERAPHIM_newbie_at_linux on 2009-02-24
Hi,

This is my first HOW TO. 

This HOW TO describes how to make a *single* new icon available for use on the panel bar. This HOW TO avoids the need for removing already implemented icons or downloading themes etc. This is *just* for if you want to place a new app/launcher on your panel, and want a custom icon to appear.

SCENARIO -- I wanted a Launcher in the panel that opened a page straight to Google Reader. I did not like the default launcher icon, and I wanted the Google Reader icon to appear on the panel.

---STEP ONE---
Find an image you want to use as your icon. Naturally, try to get one that looks like an icon - a photo or some intricate picture will not look good when shrunk to 24 pixels!!

This is the image I found online for Google Reader:
[IMG]http://lh6.ggpht.com/_A7cEXPbHU6M/SaSoLvx3aMI/AAAAAAAAAHM/_DoAaXqqlEM/original%20google%20reader%20icon.jpg[/IMG]

---STEP TWO---
The next few steps assume that your image is similar in nature to mine (ie, has black border etc).
Open your image in GIMP and use the fuzzy select tool to highlight the border. Then delete that border (ctrl-X)

Highlight it:
[IMG]http://lh3.ggpht.com/_A7cEXPbHU6M/SaSoLuakNQI/AAAAAAAAAHU/JVOoCCmRndM/s800/step2.jpg[/IMG]

And, delete it:
[IMG]http://lh4.ggpht.com/_A7cEXPbHU6M/SaSoL1Y8vmI/AAAAAAAAAHc/Y3t9cRclP3Q/s800/step3.jpg][/IMG]

---STEP THREE---
Use the eraser to remove the rest of the border.

Result:
[IMG]http://lh6.ggpht.com/_A7cEXPbHU6M/SaSoMbE803I/AAAAAAAAAHs/hABxw8luhjk/s800/step5.jpg[/IMG]

---STEP FOUR---
Now we make the background transparent so the icon looks nice on the desktop and panel. This is very important, because otherwise your icon will have an ugly white box around it!

Use the fuzzy select tool again and click on the white background. Then go to the menu Layer > Transparency and select 'Color to Alpha'. Click OK on the preview box.

The result should look like this:
[IMG]http://lh5.ggpht.com/_A7cEXPbHU6M/SaSooZOPeLI/AAAAAAAAAH0/JCEhf2ssbTc/s800/step6.jpg[/IMG]

---STEP FIVE---
This step is optional. Some images, such as mine, do not shrink very well. The image we have built so far works beautifully on the desktop, but looks pretty bad when shrunk to 24 pixels for the panel (ie, its angled lines look jagged). Thus, to ensure a pretty icon on the panel, it is best to shrink your image now, as opposed to letting GNOME shrink it itself.

Highlight your image with the regular rectangle select tool. Then push Shift-T (Scale Object). In the box that appears click the chain icon so that the image scales proportionately, and select 'pixels' from the adjacent drop down menu. Then type in a size in width or height - for use on the panel it should be around 24 to 45 pixels. I chose 32 pixels for no particular reason :)

Scale:
[IMG]http://lh5.ggpht.com/_A7cEXPbHU6M/SaSoo-tVVoI/AAAAAAAAAH8/308yq3SmEXc/s800/step7.jpg[/IMG]

---STEP SIX---
Open a new GIMP window (Ctrl-N) and when the 'Create a New Image' box appears, chose an 'Image Size' the same size as your scaled icon (ie, i chose 32x32 pixels). IMPORTANTLY, make sure you choose 'Advanced Options' and Fill With 'Background Colour' (so the background remains transparent).

Then cut your scaled icon and paste it into the new, small, image window.

[IMG]http://lh4.ggpht.com/_A7cEXPbHU6M/SaSoo8Foy5I/AAAAAAAAAIE/bIYLcM_D1k4/s800/step8.jpg[/IMG]

---STEP SEVEN---
Save your image as a .png file to the Desktop.

NOTE - it seems many people believe the GNOME panel will only accept .svg images. This thought is probably brought about because if you try to select a new image for a panel launcher, it opens a browser to /usr/share/icons/hicolor/scalable/apps which is filled with .svg images. HOWEVER, it is not true - the GNOME panel happily accepts .png files.

---STEP EIGHT---
Almost done! Now we place the icon within a suitable icon folder (ie, where GNOME goes to for its icon images). There are a number of folders to choose from, and they are organised according to size (in pixels) and purpose. 

---EDIT---
I have since found that the launcher on the panel will disappear after reboot if the .png is placed in the folder I originally suggested. Therefore, the following folder (which uses .png by default) is preferred.

Open a terminal and type the following:
sudo cp ~/Desktop/[insert file name].png /usr/share/icons/hicolor/48x48/apps

Enter your sudo password.

---STEP NINE---
Although you can now see your icon in that folder if you use a file browser, GNOME does not yet register it as an available icon. 

You must REBOOT.

---STEP TEN---
Once rebooted and logged back in, create your launcher on the panel. Then right click it, choose Properties and click on the image. This will open a browser straight to the folder we placed your icon. Find your icon, select it, and click OK.

YOU'RE DONE! The icon should appear on your panel and, assuming it scaled well, it should look smooth and pretty!

---

### Post by Danno2468 on 2009-03-05
Thanks for the Info it was exactly what i was looking for!

---

### Post by sERAPHIM_newbie_at_linux on 2009-03-08
Hi.

Glad you found it useful!

As a note, you may find it difficult to select your new icon initially. For some reason the browse button shows the .png icon folders as empty. 

To fix this, simply choose the gnome-tetravex.png icon from the first set of icons that ubuntu shows you. Then close re-click on the change icon button (ie, the icon picture in the properties) and the icons now shown will be .png and the directory listed will be /usr/share/icons/hicolor/48x48/apps. 

Thus, if you're having trouble getting your icon, put it in the aforementioned folder, and it will appear after following these steps.

Cheers

---

### Post by heitjer on 2009-05-03
Great tutorial - just what I needed. 

Here is my tip for all others that are still struggling to get the *png files recognised.

Browse to the file in the **File Browser** window, copy the path and the file name, i.e.

```
/usr/share/icons/hicolor/64x64/apps/jalbum-icon.png
```

Then after you click on the icon in the **Launcher Properties** paste this in the top line.

For some reason it will not show the icon at first. Close the window again and then reopen the **Launcher Properties** again. Then you should see all *.png files. 

Hope this helps.

---

