---
title: "Fonts - argh!"
date: 2006-01-06
forum: General Help
---

### Post by Optiker on 2006-01-06
Now that I have sound on my Kubuntu setup, the next step in my hoped-for transition to Linux is FONTS!

I have far more fonts in Windows than anybody in their right mind needs, but it's easier to leave them than to try to sort and remove those I don't use. However, I do enough creative graphics kinds of things that I like having a wide variety of fonts to select from.

I've tried to read some of the posts on various forums, as well as other resources, but so far, find it pretty confusing as to how I can have at least some of my Windows TT fonts available for use in Linux apps.

Can anybody either point me to a good "TT font to Linux for dummies" reference, or maybe better yet, walk me though an example of how to do this?

Thanks!
Optiker

---

### Post by matthew on 2006-01-06
Open the file browser.

In your home directory create a folder called ".fonts" (if it doesn't already exist)
* EDIT: for clarity...*the new folder/directory is */home/username/.fonts*

Copy all your ttf files into that folder

That's it. Now they should be available to OpenOffice, Gimp and pretty much everything else.

---

### Post by Optiker on 2006-01-06
Matthew...cool! That worked. Now, in Windows, I use FontGlancer as a font browser. What's a good Linux font browser - I realize that the font listing in each app will list the font in that font, but sometimes I like to browse more quickly than that.

Also, how do I access those fonts? I opened a new doc in Gimp - a place I often need a variety of fonts - and only had the default ones that came with the installation. Same was true of OpenOffice Writer. How do I set them up so in each app they are included in the font listing?

Thanks!
Optiker

---

### Post by GeneralZod on 2006-01-06
You can preview fonts in Konqueror - just enable thumbnail view, and make sure "Fonts" are checked in the preview section:

[http://etotheipiplusone.com/konqueror-font-preview.png](http://etotheipiplusone.com/konqueror-font-preview.png)
[http://etotheipiplusone.com/konqueror-font-preview2.png](http://etotheipiplusone.com/konqueror-font-preview2.png)

Also, not particularly helpful, but there is also a fonts kio_slave - just enter

```

fonts:/

```

as a URL in konqueror :)

---

### Post by Optiker on 2006-01-06
OK - I did see that Konqueror can be used when I was copying my fonts folder from Win to Kubuntu. That will work...just hadn't thought of it. Handy.

Now, howe do I get access to them in the font menu within apps?

Thanks!
Optiker

---

### Post by matthew on 2006-01-06
[quote=Optiker]Now, howe do I get access to them in the font menu within apps?[/quote]I didn't have to do anything special to get them to appear. I suppose you could log out and then log back in and see if perhaps KDE only reads that folder/directory once per login session? (I use Gnome most of the time, though I've occasionally used KDE as well.)

---

### Post by Optiker on 2006-01-06
Matthew...nope - logged out, restart, no change.

Other ideas?

Thanks!
Optiker

---

### Post by matthew on 2006-01-06
[quote=Optiker]Matthew...nope - logged out, restart, no change.

Other ideas?[/quote]Hmm...I'm not sure why that didn't work for you. Any KDE gurus out there able to jump in??

EDIT: I just checked again and as soon as I add a new font to that directory (/home/username/.font) it is immediately available on my computer to OpenOffice Writer and Gimp.

---

### Post by Optiker on 2006-01-06
What's the emoticon for a sheepish grin?

I was sloppy. I thought I'd be more efficient and just copy the ...\fonts folder from my Windows folder to my /home/name/ folder. I didn't notice that not only did your message indicate lowercase "f" in "fonts" but it had a period in front of it.

As soon as I renamed the folder .../.fonts, of course, it disappeared. When I thought it had somehow fallen into oblivion, I tried to create a .../.fonts folder and the error message said one already existed - but I couldn't see it. After another such try and stopping to think about it, I enabled "show hidden files" and there it was! 

Then, I opened The GIMP and there they were.

Thanks! My noob error.

Optiker

---

### Post by matthew on 2006-01-06
[quote=Optiker]Thanks! My noob error.

Optiker[/quote]No stress. I've made more than my share of errors. I'm just glad you figured it out. Congrats on a successful fix! Have fun with your new font library. :)

---

