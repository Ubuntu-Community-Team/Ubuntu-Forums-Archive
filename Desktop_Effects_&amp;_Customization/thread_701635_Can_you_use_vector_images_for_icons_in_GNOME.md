---
title: "Can you use vector images for icons in GNOME?"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by gohanssjn on 2008-02-19
Looking to update a few icons in a pack I downloaded that look messy when blown up.

Is there a way to do this?  And what format would this be?  I installed InkScape, but am at a bit of a loss on what to do here...

---

### Post by FuturePilot on 2008-02-19
Yes. They need to be in the .svg format. You need to find the icon that needs replacing (which could take some time since the structure of an icon theme has tons of places it could be hiding.) Then you need to replace the icon making sure it has the same name. Be careful that you find the actual image. In an icon theme there are tons of links pointing back to one image. So you have to find the actual image.

---

### Post by gohanssjn on 2008-02-19
Hmm, the one I am looking at is named stock_bluetooth.png....so using the theme, how do I use a .svg since it is going to look for a .png of that name?

---

### Post by FuturePilot on 2008-02-19
You might have to recreate all the links so they point back to the .svg. Since it's only a link you might be able to just change the extension, though I've never tried that so I don't know if that will work or not.

---

### Post by gohanssjn on 2008-02-19
Do I do that in the theme.index or whatever that file is called in the icon package?

---

### Post by FuturePilot on 2008-02-19
No, the theme.index is just a file that makes it show up in the Appearance Properties. Just replace the existing icon with the new one and fix any links (if there are any) so they link back to the new one.

---

### Post by gohanssjn on 2008-02-19
Right, but how would I fix those links?

For instance, when I right click my BT icon, I only get Open or Remove, not properties where I can change the icon there.  That's why I am replaceing the files to beguin with instead of just changing the notification icons.

BTW, thanks for all the help so far :D

---

### Post by FuturePilot on 2008-02-19
You can middle click on the actual image and then just drag it somewhere in the same directory and drop it and you will get an option to "Link Here" Just name the link the same as the one you are replacing. You might have to delete the old one first.

---

### Post by gohanssjn on 2008-02-19
Cool, I finally got it to work.

Now, one more question.  The icon I made and then renamed to .png has a transparent background on my desktop, but when it is in the notification area, there is a white background that I can see (since the bar is gradient).  Any way to fix that issue?

Below is a screen shot of what I mean

---

