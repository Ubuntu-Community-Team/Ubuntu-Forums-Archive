---
title: "Save as gif in KDE"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Peter Mount on 2006-07-23
Hello

I'm using Kubuntu 6.06. I'm saving images as gif files into my home directory but I'm having to use OpenOffice to do it. It works but it's seems like a work around.

I've tried using Krita but it crashes. I tried KolourPaint but it doesn't let me save or export as gif. 

Is there a plugin for KolourPaint that will let me save as gif or is there a better KDE app I should use?

I was using The Gimp in Fedora Core 5. If I install the Gimp in Kubuntu would I use the kdesu prefix (even though it's a gnome app) to have it save to the /var/www directory? This is for images I'm using on web sites

Thanks

---

### Post by mssever on 2006-07-23
I'm not a regular KDE user, so I don't know about KDE-specific programs, but I'd use The GIMP for the task. I suppose you could start The GIMP with kdesu, but since it sounds like this is something you'll be doing regularly, I'd instead make your DocumentRoot writable. The simplest way to accomplish this would be to change the ownership of the directory: ```
sudo chown -r <your_username> /var/www/<your_document_root> # substitute as appropriate for the values in <>
```
Now, you can edit the files there to your heart's content.

On my system, I've taken this a step further and moved Apache's DocumentRoot to ~/webmaster (could also symlink it). This makes the files more convenient to access.

---

### Post by Jucato on 2006-07-23
If you only need to convert an image into GIF, without any form of editing (just straight conversion), just right-click on the image, choose Actions > Convert To > GIF.

---

### Post by Peter Mount on 2006-07-23
Thanks for the replies.

Have fun

---

