---
title: "Change Mimetype icons in Gnome/Nautilus"
date: 2008-02-18
forum: Desktop Environments
---

### Post by spamking2000 on 2008-02-18
Hey - Quick question,

I installed Lotus Symphony and it took over my icons for OpenDoc formats from OpenOffice. OpenOffice icons are still what are shown for MS Office extensions however. I'd like to have all these be the same and would like the OpenDoc formats to revert back to OpenOffice based icons (basically what they were before Lotus Symphony hijacked the mimetype).

I don't want to create a custom theme or anything like that... not looking for a work around. I want to know how to change them all back (not one individual ODT or ODS doc at a time) based on the type of file so that if another theme doesn't have a setting for that it won't matter.

Using Gnome and 7.10...

There has to be a simple way to do this, but I'm just not finding it.

Thanks,
spamking2000

---

### Post by Vivian-Synecdoche on 2008-03-15
anyone can bump this? I'm looking for the same answers but to no avail? This is really a problem - please help. :D

---

### Post by erichgamba on 2008-04-23
I got the same problem.
Placing an png image file into the home directories .icon folder seems not to work anymore in nautilus 2.22.2.
Any solutions out there?

---

### Post by arsenic23 on 2008-04-23
I'm not sure if this will work, but it should.  A while ago I found out how to manually add mime types in Gnome, here's the post:

[http://ubuntuforums.org/showthread.php?t=574586](http://ubuntuforums.org/showthread.php?t=574586)

I asume all you will have to do is edit the xml file(s) for you mimetype instead of making a new one.

Here's a quote of the original incase you don't want to be bothered with that thread:

> **arsenic23 said:**
> Ok !  I figured it out.  Here's how to add a new mime type in Gnome for anyone else who wants to know.

Go to the main mime dir and create a new mimefile for your filetype ( I'm doing .mdf here ):
```
cd /usr/share/mime/packages
gksudo gedit [COLOR="#8b0000"]mdf[/COLOR].xml 
```

Paste the following into your text editor window and save it:
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/[COLOR="DarkRed"]x-cd-image[/COLOR]">
        <comment>[COLOR="DarkRed"]MDF[/COLOR]</comment>
        <glob pattern="*[COLOR="DarkRed"].mdf[/COLOR]"/>
  </mime-type>
</mime-info>
```

Now just update your mime database with this command :
```
update-mime-database ..
```

Note that the *"application/x-cd-image"* part makes the correct icon file the ./mimetypes/application-x-cd-image.svg(png) in your icon theme directory.   Simply change the red parts and you can add any mimetype you wish.

Of course you'll need to know the default name of the icon you want to use - but that shouldn't be too hard to find out rooting about in any icon theme that contains them.

---

### Post by HuckleSmothered on 2008-04-25
Ouch, that's a pretty rough procedure for a newbie. That can be quite cumbersome for all the OpenOffice extensions. Plus the txt's files I want to change, plus the .ram files, and all the Microsoft ones too, you know.

Any other suggestions that are more along the lines of "right click here and change the icon there?"

---

### Post by arsenic23 on 2008-04-29
I'm no expert on this matter, but you may just be able to remove the lotus notes file in */usr/share/mime/packages*.  Or you may just be able to remove the filetypes you want from just one xml document.

What do you get when you type ```
ls /usr/share/mime/packages
```

If there is a lotus.xml then you MIGHT be able to get your icons back to normal by remove a little form it and then updating the mime database.  I'd back the file up before I tried it though.

---

### Post by grip82 on 2008-05-01
I bumped into this one as well. Too bad there isn't a simple solution. 

Off course, manually editing the .xml will probably work just fine, but that's not something you want to do as a user.

---

### Post by spamking2000 on 2008-05-04
Not sitting at that computer at the moment, but thought I'd comment on this. I did end up just doing a work around. I found the default icon set for OpenOffice and just copied the Writer/Calc/Impress icons over the Symphony icons.

Took about 10 minutes to find them and get through the process.

Hope that helps!

---

