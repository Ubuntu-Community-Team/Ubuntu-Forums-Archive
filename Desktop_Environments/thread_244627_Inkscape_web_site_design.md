---
title: "Inkscape web site design"
date: 2006-08-26
forum: Desktop Environments
---

### Post by randomthings on 2006-08-26
Hi 
I wonder how to export a web template made with inkscape like this one :
[http://www.inkscape.org/showcase/web_design/index.php](http://www.inkscape.org/showcase/web_design/index.php)
into a html file .

---

### Post by randomthings on 2006-08-26
up

---

### Post by dyoung66 on 2006-08-27
You can save your image as a .bmp from inkscape.
Then import it into Gimp(no svg support) and cut/resize each individual component (save each component as a .png/.gif/.jpg).

Or you can use the Pyslice tool in gimp to cut up the pages (from guides you create) and save each component out. Pyslice generates html code for you. (A far as I know it only supports tables, it wont give you any nice css).
Hope this helps.

---

### Post by randomthings on 2006-08-27
Thanks , but can you explian more about Pyslice tool and where can i find it ? Because i don't use gimp too much and i don't know how to use it .

---

### Post by randomthings on 2006-08-27
up

---

### Post by randomthings on 2006-08-27
up

---

### Post by dyoung66 on 2006-08-29
sorry, was away from the computer for a while...

firstly, open the gimp and you will find pyslice at:
Filters->Web->Pyslice

but dont start it yet, first you will need to create guides that depict how you want to cut out your image.
to create a guide, enable rulers:
View->Show Rulers
Then click on the ruler and drag the mouse out onto the canvas. You will see that you have created a line(guide) on your image. Repeat this process to create multiple guides.
To move a guide:
Select the move tool (M) (make sure the Move tool is on "Pick a layer or guide") and select an existing guide to position it.

To delete a guide, drag it off the canvas.
Once you've placed all your guides, start pyslice and it will export all the areas into separate images, and write out some html code for you, using tables to layout the page.

Hope this helps.

---

