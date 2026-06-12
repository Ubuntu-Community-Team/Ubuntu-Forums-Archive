---
title: "how do i get rid of the logo on the menu?"
date: 2009-10-25
forum: Desktop Environments
---

### Post by andrew_D14 on 2009-10-25
[IMG]http://i36.tinypic.com/2vvjpkk.png[/IMG]

where the red part is circled, how do i get rid of that? i tried to edit the menu but it doesnt appear to have that option.

---

### Post by martrn on 2009-10-25
> where the red part is circled, how do i get rid of that? i tried to edit the menu but it doesnt appear to have that option.

I do not know if there is an option to remove the gnome menu, because it's linked to your applications/places/system menu, however if you remove the gnome menu, (right click on applications then click "remove from panel") it will remove the icon, but remove the Applications/Places/System menu also.

The icon is stored at /usr/share/pixmaps or /usr/share/icons/themename and is called start-here.png and you could change the icon of the feet (YUK!), and put a different icon there !

What is the other icon next to it ? (The white ubuntu glossy one ?).

---

### Post by andrew_D14 on 2009-10-25
> **martrn said:**
> 
What is the other icon next to it ? (The white ubuntu glossy one ?).

its the linux mint menu button, i just changed it

and i might just change the image of the gnome foot and make it all black or something, thanks!
but if anyone knows how to get rid of it id love to know

---

### Post by martrn on 2009-10-25
I don't know how to get rid of it.

If you have trouble finding it,  type :

sudo find / -name distributor-logo.png
sudo find / -name start-here.png

..and make them completely transparent .png's.

---

### Post by andrew_D14 on 2009-10-25
ok ill do that, how do i make them completely transparent?

---

### Post by gnuisancev3 on 2009-10-25
> **andrew_D14 said:**
> ok ill do that, how do i make them completely transparent?

first off, to make his find command a bit faster, you can run it like so:

sudo find /usr/share/icons -name distributor-logo.png
sudo find /usr/share/icons -name start-here.png

(the path can be changed to /home/<username>/.icons if the theme you are using was installed locally by a non-root user.

Open the file in gimp, notice the dimensions in pixels of the image.  Create another image (saved as the same file name.. and you might want to back up the originals fist), that's a transparent png. 

YOu can do this by File --> New --> Make sure the dimensions are the same then go below to  Advanced --> Fill With "Transparency" and then hit Ok.  THen save the file as a PNG

---

### Post by andrew_D14 on 2009-10-25
hmm i can't seem to find the picture of the foot. Its part of a theme, so should i be looking somewhere else? cause it only lists the ubuntu logos and themes when i search them up.

---

### Post by gitboxgreg on 2009-10-27
You might want to try using ubuntu tweak [http://www.getdeb.net/release.php?id=4775](http://www.getdeb.net/release.php?id=4775) it has an option to replace the main menu icon.

---

