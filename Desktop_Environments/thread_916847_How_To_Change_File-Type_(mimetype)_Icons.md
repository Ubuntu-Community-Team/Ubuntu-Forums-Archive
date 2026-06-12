---
title: "How To Change File-Type (mimetype) Icons"
date: 2008-09-11
forum: Desktop Environments
---

### Post by dangermouse28 on 2008-09-11
[SIZE="4"][FONT="Arial Black"]How To Change File-Type (mimetype) Icons[/FONT][/SIZE]

[SIZE="3"][FONT="Arial"]This how-to is based on wanting to change icons which have been downloaded from Gnome-look or some other source. As an example, I'll show how to change the icons associated with .doc and .odt files. Exactly same method applies to other file types.

(If you're using the icons supplied with Ubuntu, you'll find them in /usr/share/icons. Also, if the iconset you're modifying is based on scalable .svg icons, the procedure will differ - find the icon to change in the "scalable" folder and replace with new .svg image)


[LIST=1]
[*]Open up a folder containing files with icons you want to change.

[*]Right-click on an icon and select Properties

[*]Look for the MIME type entry and make a note of it:
	e.g. application/msword (for .doc file)
	or   application/vnd.oasis.opendocument.text  (for .odt file)


[*]Navigate to ~/.icons folder. You'll see all the custom icon sets you've installed.

[*]Open up the icon folder you're using and you'll see that there are several folders containing the same icons at different sizes. In the Nautilus file manager, you can zoom in or out, increasing or decreasing the size of the icons displayed - these folders of icons make that possible. The size of icon vs zoom level is as follows:

	400% - 128x128
	200% - 96x96
	150% - 72x72
	100% - 48x48
	67%  - 32x32
	50%  - 24x24
	33%  - 16x16

	(There are also icon folders 64x64 and 24x24 - not sure what they're used for!)

[*]Make seven versions of the image you want to use in the sizes listed above and copy into each folder.

[*]You'll have to repeat the next bit for each size:

	Open folder
	Look for file corresponding to mimetype entry you noted down earlier
		e.g. application/msword = application-msword.png
		or   application/vnd.oasis.opendocument.text = application-vnd.oasis.opendocument.text.png
	Delete existing file
	Find the image file you copied in here earlier, right-click, Properties, Permissions tab.
	Click on the "Execute" tick box and "OK"
	Right-click on image file, Make link to to create a new link file.
	Rename the link to replace the file you deleted.

Repeat for each icon size.


[*]When you've finished replacing icons, delete the "icon-theme.cache" file.

[*]Open a terminal and do:
	# cd .icons
	# gtk-update-icon-cache *ICONSET NAME*
	This will re-generate the icon-theme.cache file using your new icons.

That's about it. Open up a new Nautilus window and enjoy icon nirvana!!!

Someone who's done a bit of script writing could easily use this method, add a little front end via Nautilus-extensions to select an image, auto-rescale to the different sizes, apply, regenerate files and we'd all have an easy way to change file-type icons from the GUI. Anyone fancy a go?[/FONT]
[/LIST][/SIZE]

---

### Post by pharrell on 2008-10-10
thanks

sorry... but theres an error, the line
> # gtk-icon-cache-update ICONSET NAME

should be:
> # gtk-update-icon-cache ICONSET NAME

;)

---

### Post by dangermouse28 on 2008-10-13
Thanks - my deliberate mistake has now been corrected!

Well noticed :wink:

---

### Post by fcastillo on 2008-11-25
Thanks for it, but I can't make it work. I don't want to replace the icon for an extension. I want to add icon for a new extension. I'm using the UbuntuStudio icon set, and after running the command:
> # gtk-update-icon-cache ICONSET NAME
I get this error
> gtk-update-icon-cache: No theme index file.
I've checked and the iconset name is correct. I don't know what's going on. Any help will be appreciated

---

### Post by dangermouse28 on 2008-11-26
Hmm - I haven't tried to add a new icon for a new extension, although I have a feeling it's a bit more complicated than just adding a new icon - you'd have to create the rule under which that icon is displayed, give it a specific system name etc etc.

As to your other problem, you need to be in the icon set folder (where the index file is located) before using that command.

---

### Post by scientibuntu on 2009-02-19
Use assogiate instead - download with synaptic.

---

### Post by adamlau on 2009-02-19
I prefer editing the desktop files located at:

```

/usr/share/applications
/usr/local/share/applications
```

before updating the databases:

```
update-mime-database /usr/share/mime
update-mime-database /usr/local/share/mime
update-desktop-database /usr/share/applications
update-desktop-database /usr/local/share/applications
```

---

### Post by wolterh on 2009-02-24
Assogiate doesn't work for me...I make the mimes and everything and it doesn't work.

For example, I made a TODO mimetype, with a TODO* file pattern and a custom icon. I closed assogiate and afterwards created an empty TODO file. No icon was assigned, but at least the mimetype was detected. I right-clicked on properties and it said it was, as I asigned it, an x-todo file.

---

### Post by romuald_geo on 2009-03-21
I have similar issu that woil.Can anyone assist?

---

### Post by MathUHenry on 2009-07-07
I'm having trouble with the last step: 
cd .icons
gtk-update-icon-cache ICONSET NAME

It's telling me "No theme index file"

I copied a theme index file from /usr/share/icons/gnome to .icons, but that didn't help.

Could someone tell me what I'm doing wrong?

---

### Post by wolterh on 2009-07-07
This bug should have been fixed a long time ago...

---

### Post by leorolla on 2009-11-16
I agree.

This is awful...

Did anyone file this bug?

---

