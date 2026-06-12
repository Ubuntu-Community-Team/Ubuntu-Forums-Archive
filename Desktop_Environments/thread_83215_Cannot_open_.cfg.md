---
title: "Cannot open *.cfg"
date: 2005-10-28
forum: Desktop Environments
---

### Post by .Danny on 2005-10-28
> Cannot open *.cfg

The filename "*.cfg" indicates that this file is of type "cfg document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

:rolleyes:

I just uploaded a cfg file via nautilus to my ftp and this started poping out every time now when I try to open a file with cfg at the end.

This is really annoying and didn't happen before, I work with a lot of cfg's so is there a way to turn this off again?

---

### Post by .Danny on 2005-10-29
Bump.. :(

---

### Post by abou on 2005-10-29
Did you try to open it through the terminal with sudo gedit /file destination?

---

### Post by psychicdragon on 2005-10-29
I think you have to create a mime type for a cfg file.

Open **~/.local/share/mime/packages/Override.xml** (or create it if it's not there).

Paste this into the file, or just add the bold part if the file already exists.
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

[B]<mime-type type="text/x-extension-cfg">
	<comment>cfg document</comment>
	<glob pattern="*.cfg"/>
</mime-type>[/B]

</mime-info>
```
Then run this command:
**update-mime-database ~/.local/share/mime**

You should now be able to tell nautilus what application to open cfg files with and it won't complain anymore.

---

### Post by .Danny on 2005-10-29
Thanks that worked. The file was already there, and the same entry as well. Just except the text/x-extension-cfg it was application/x-extension-cfg.

[edit] I actually just deleted the file now and it works as it did before and with the nice text icon as well. :)

---

