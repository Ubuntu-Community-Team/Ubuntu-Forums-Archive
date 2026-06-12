---
title: "How do I use downloaded themes??"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Ingla on 2005-10-30
Hello.

I've been looking all over to try to find out how to use the themes that were downloaded by Update Manager. Nothing works.

Trying to "install" a theme is madness. It apparently needs a tar.gz file...which doesn't exist except inside the downloaded deb package. Any path I try to give it returns an error message "Invalid file format".

Isn't there some "normal" way to do this?

Just want to try out some other themes, but it's getting crazy.

Anybody know ***exactly*** how to do this? :confused: 

Many thanks.

---

### Post by manicka on 2005-10-30
System-->Preferences-->Themes

If you click on a theme in this panel and then click on 'Theme details' You can play with the different metacity/gtk and icon themes. This is where you'll see the extra themes that you've installed with synaptic.

Also, you can download more themes at gnome-look.org

Just download the tar.gz files to your desktop or home folder, then either drop them onto the theme control panel window or use the install button and navigate to where you downloaded then tar.gz theme file to.

HTH

---

### Post by Ingla on 2005-10-31
Thanks for the reply.

*[COLOR="Red"]"Just download the tar.gz files to your desktop or home folder, then either drop them onto the theme control panel window or use the install button and navigate to where you downloaded then tar.gz theme file to."[/COLOR]*

The problem seems to be a bug or something. Neither navigating nor clicking and dragging works. In both cases, I get an error message "Invalid file format" after clicking "Install"...and (although I sometimes get "false alarm" error notices) the Theme is not, in fact, installed.

Is there a command line way to install a theme or any other advice?

Thanks.

---

### Post by 23meg on 2005-10-31
Some theme packages have multiple themes in them. Double click the archive and see if there are multiple archive files in it. If so, extract those and drag&drop them onto theme manager.

---

### Post by Ingla on 2005-10-31
Thanks for the reply.

The tar.gz file does not contain any other compressed files.

Any ideas?

---

### Post by 23meg on 2005-10-31
Then you have a faulty theme, probably. Does this happen with all theme files you download, or just a specific one?

---

### Post by Ingla on 2005-10-31
So far, it's happened with several. I havne't tried to many, but all bring the same response.

This particular one was downloaded from this forum and other people have said it was good. I got it from:

[http://ubuntuforums.org/showthread.php?t=83009](http://ubuntuforums.org/showthread.php?t=83009)

I'm new to Ubuntu and to Linux, but have noticed that sometimes something in the GUI doesn't work where a command will ***and*** vice versa.

---

### Post by 23meg on 2005-10-31
Which theme is it exactly? Maybe you need a different version of a theme engine such as Clearlooks for it to work.

---

### Post by Ingla on 2005-10-31
The file is called Ubluentu.tar.gz. You can download it from the forum at the URL I gave in the previous post, if you like.

---

### Post by 23meg on 2005-10-31
Checked it out; that's a GDM (login screen) theme. Theme manager only lets you change GTK, Metacity an icon themes. You can change GDM themes in System / Administration / Login Screen Setup.

---

### Post by Ingla on 2005-10-31
Thanks. I'll check it out. I thought he had a whole theme.
How do you recognize these types? How many types are there?

---

### Post by 23meg on 2005-10-31
Metacity themes: These are window decorations, and have a "Metacity-1" subfolder inside the archive.

GTK Themes: These are themes for all widgets in your applications, basically everything except window frames themselves. Inside the archives you find a "gtk-2.0" folder.

Icon themes: These contain icons for most mimetypes, apps, etc. They have subfolders corresponding to icon sizes and an index.theme file.

GDM themes: These are themes for the Gnome login screen. You'll see image files, a .desktop file and an .xml file inside the archives.

These should be a last resort though; you should already be able to figure out what theme it is by looking at the filename or the web page you've downloaded the theme from.

---

