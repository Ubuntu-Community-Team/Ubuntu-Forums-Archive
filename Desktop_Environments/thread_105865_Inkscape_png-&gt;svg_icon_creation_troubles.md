---
title: "Inkscape png-&gt;svg icon creation troubles"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Cordate on 2005-12-19
[COLOR="DarkGreen"]I'm attempting to build my own icon theme from a hodgepodge of my favorite icons from various theme sets and also icons found on the web in different raster formats. 

I'm using an svg-based theme as my starting point, replacing the icons I don't care for with my new ones. 

So I'm using (well, *trying* to use) Inkscape 0.42 to convert the raster-based files into svgs, but that's where something's not working right. 

I bring the image (say, nifty-icon.png) into inkscape either with drag-n-drop or via File->Import and then it's in the program. But in the status bar it usually says something like "image with bad reference." Sometimes I can get that to go away via File->Vaccum Defs or Edit->Make a Bitmap Copy (and then delteting the original. 

Maybe the "bad reference" thing isn't something I need to worry about, but I try this because when I save the file as an .svg, it gives me an iconless file and the icon fails to appear when I use the theme (those filetypes have an invisible icon). This happens whether or not I am getting the "bad reference" message.

So it seems I'm doing something wrong, and possibly something basic and easy to fix, but I've looked through Inkscape's documentaion and I'm not finding an answer... so here I am! :) 

With all the eyecandy-loving customizers here, someone must know how to move from png to svg and have their icons work out![/COLOR]

Edit: some fiddling around has uncovered a bit more about what's going on. The "blank" icon is one where the bitmap simply is not showing up. If I put a vector graphic in a layer under the bitmap, it shows up fine. 

Annnd (this is the weird part) just now I imported a bitmap, saved the file as svg, and everything looks fine. Then, without running any other commands, I saved it under another filename. Result: blank icon. Very strange. I'm going to go reinstall the proggy and see if maybe that helps- seems like this behavior could be a glitch somewhere.

---

