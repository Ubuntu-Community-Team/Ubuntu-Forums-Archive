---
title: "Grub splash Images help"
date: 2007-05-12
forum: Desktop Environments
---

### Post by jazzman84116 on 2007-05-12
Does anyone know how to create a grub splash image, I want to make one out of a pic I have?

---

### Post by Herman on 2007-05-13
Hello jazzman84116,

First make a copy of your original picture. Don't work on the original picture because we're going to ruin it . The reason we have to ruin it is because we have to make it simple enough and small enough for the computer's BIOS to be able to display it. Remember the operating system won't be booted yet, so no nice video drivers will not be working yet. Most BIOSes only have VGA mode, and so can't handle a good quality image.

Open your copy of the original picture with GIMP Image Editor and scale and/or crop your image until it's cut down to 640x480 pixels.

First, we'll crop it. Press shift+c for the crop tool in GIMP. You may need to use a calculator or spreadsheet to work out how high to crop the image for it's width. If it happens to be 2560 pixels wide for example you'll need to crop it to (2560/4)x3= 1920 pixels high.  Or something like that, you might decide to keep the height but change the width instead. 

Then you can scale the image down to 640 x 480 without too much trouble after that. Press 'Image'-->'Scale Image' for scaling.
 It might take a couple of tries until you end up with something you're happy with, another good reason never to work on the original. You will also maybe want the main subject in the picture off center to the right a bit and maybe down a little so it won't be covered up by the Grub Menu's lines of text too much. Consider where the Grub menu's rectangle will be too.

When you have that done, then go 'Image'-->'Mode'-->'Indexed', and set 14 colours as the Maximum number of colours, and set the 'colour dithering' spinbox to 'None', and click 'OK'.  
That will reduce the quality of the image even more. Some images are not suitable for this type of treatment and they just won't make good grub splashimages. Other images are fine. You need to experiment until you learn how to choose suitable images for this. Simple images seem to work best in my opinion. For example a drawing or cartoon type of image or a simple photo often works better than a high quality photo. Some people convert their photos to black and white first and then use GIMP to add simple colour to them later too. That way you don't ruin the picture as much when you convert it to 14 colors.

                                    Then go 'File'--> 'Save as' and make up your own file name. Be sure to add an .xpm filename extension after it, and you're all done. It's easy!

Finally, just right-click on your new .xpm file and click 'create archive' (from your right-click menu), and click the spinbox over in the right of the 'Create Archive' window. Select .gz and hit 'Create'.

Now all you need to do is 'sudo cp' it to your /boot or /boot/grub directory and add your splashimage command for it in menu.lst. Actually it can be left anywhere. As long as your splashmiage command has the right file path it will still work even if it's in your /home/username folder or wherever. It's just tidier to keep it in your /boot directory or somewhere out of the way like that. 

Regards, Herman :)

---

