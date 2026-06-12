---
title: "Creating your own Mime type icon"
date: 2006-02-13
forum: Desktop Environments
---

### Post by WaterWalker on 2006-02-13
I have several files on my computer with a Mime-type without an icon. So I get a green feet for all the Mime-types without icon.
Can I change this, creating a custom icon for a specific Mime-type? And how do you do that?

---

### Post by heimo on 2006-02-13
Well... Don't know if [this]("http://gnomesupport.org/forums/viewtopic.php?t=9214&sid=59577c74a3a0a4e85537ba7001173a4a") will help, but it's something. I got an impression (from couple mailing list posts) that there's no easier way to customize it (unless you change whole icon theme).

---

### Post by WaterWalker on 2006-02-13
[QUOTE=heimo]Well... Don't know if [this]("http://gnomesupport.org/forums/viewtopic.php?t=9214&sid=59577c74a3a0a4e85537ba7001173a4a") will help, but it's something. I got an impression (from couple mailing list posts) that there's no easier way to customize it (unless you change whole icon theme).[/QUOTE]
Thank you.
But it doesn't really help, since I don't want to change my current Mime Icons. I want to add new icons for Mime types don't have any icon.

---

### Post by nalmeth on 2006-02-13
What kind of files are they? You can change icons individually if its only a launcher you want to change. But if its the icon for mp3's you don't like or something, and you want to change them across the board, then I wouldn't know what to do.

---

### Post by pmj on 2006-02-13
To create your own mime type, navigate to ~/.local/share/mime/applications and open (create if it doesn't exist) the file Override.xml.

It's here you add your own mime types, and the file should look like this when you're done (replace the newmime stuff with your own file info):

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="text/x-extension-newmime">
	<comment>NewMime File</comment>
	<glob pattern="*.newmime"/>
</mime-type>

</mime-info>
```

When you've added all new mime types, type "update-mime-database ~/.local/share/mime"

Now you need to create icons. Since I don't know if there is a place where you can put your own icons so that they will be used regardless of the theme you use, I just put them in them in the directory for my theme. For my NewMime file type, it should be named gnome-mime-text-x-extension-newmime.png.

I really don't know if you need to create an icon for every size or how any of that works. You'll probably notice if you do. :)

---

### Post by kevinlyfellow on 2006-05-17
I'm trying to create my own mime-type but it doesn't seem to work.  Override.xml vanishes after I do the update, and my documents are not identified any differently.

---

### Post by waffen on 2006-06-03
[QUOTE=WaterWalker]I have several files on my computer with a Mime-type without an icon. So I get a green feet for all the Mime-types without icon.
Can I change this, creating a custom icon for a specific Mime-type? And how do you do that?[/QUOTE]

Check this post: 

[http://www.ubuntuforums.org/showthread.php?t=150393&highlight=mime+icon]("http://www.ubuntuforums.org/showthread.php?t=150393&highlight=mime+icon")

---

