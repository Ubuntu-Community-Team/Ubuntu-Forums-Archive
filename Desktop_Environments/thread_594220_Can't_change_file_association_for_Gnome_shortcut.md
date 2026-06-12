---
title: "Can't change file association for Gnome shortcut"
date: 2007-10-27
forum: Desktop Environments
---

### Post by richi on 2007-10-27
Hi all

I created a shortcut (.desktop file) to a Web page on my Gnome desktop by drag & drop from Firefox. Now when I double click it, it opens in Quanta plus (the HTML editor) instead of in Firefox (my Web browser).

I can't figure out a way to change this association. The usual way to do this for files in Nautilus  (right click on file ->Properties->Open With) doesn't apply to these shortcuts since there is no "Open With" option tab in the Properties dialog.

Any help would be greatly appreciated.

Richard

---

### Post by richi on 2007-10-28
Finally I **solved** my concrete problem by editing my [FONT="Courier New"]~/.local/share/applications/mimeinfo.cache[/FONT] file, locating the faulty application (quanta) and removing it.  It remains a mystery how Gnome/Nautilus determines which file to use on double-clicking a shortcut, but hey, it worked. It seems that deleting the [FONT="Courier New"]mimeinfo.cache[/FONT] file often fixes problems.

I wrote a little **summary of my (limited) understanding** of how Gnome handles file associations (not guaranteed to be accurate ;). Here it is, in case it might be of some help to others:

--------------------------------------------------------------------
Usually you change file associations in Gnome/Nautilus by right-clicking on a file -> Properties -> "Opens With" tab. However, in some occasions, it does not work (eg. HTML shortcuts dragged to the desktop have no such tab). It is also interesting to know where the corresponding files are located.

Gnome (2.18.1) defines file associations at both a **global** level (common for all users) and a **local** (per user) level.

**Global level:**
    
    [FONT="Courier New"]/usr/share/applications/<application>.desktop[/FONT] -  Description of one application. KDE apps are in a subfolder kde/.  MIME types supported by an aplication are declared in the MimeType  property, e.g.  [FONT="Courier New"]MimeType=text/html;text/css;[/FONT]
    
    [FONT="Courier New"]/usr/share/applications/defaults.list[/FONT] -  Defines which applications (described by their .desktop file) to use  when double-clicking (=default open) on files, depending on their MIME-type, e.g.  [FONT="Courier New"]text/html=firefox.desktop[/FONT]
 ...will start firefox when double-clicking a HTML file.
    
    [FONT="Courier New"]/usr/share/mimeinfo.cache[/FONT] -  This file has the same format as defaults.list, but it defines the list of applications that can open each MIME type. It is built (when?) by Gnome from the .desktop files. Excerpt:  [FONT="Courier New"]text/html=firefox.desktop;bluefish.desktop;kde-quanta.desktop;kde-kimagemapeditor.desktop;[/FONT]
        
**Local level**
    
    Each user override/merge with global definitions by defining the same files in their [FONT="Courier New"]~/.local/share/applications/[/FONT] folder:
    
    [FONT="Courier New"]~/.local/share/applications/<application>.desktop[/FONT] - Description of applications. Overrides the global def for each application if it exists.
    
    [FONT="Courier New"]~/.local/share/applications/defaults.list[/FONT] - Behavior on double-click (default open). Override the global definition, e.g.:  [FONT="Courier New"]text/html=dreamweaver-usercreated.desktop[/FONT] ...will open an HTML with dreamweaver on double-click (in Nautilus) for the current user only (while the global default was to start firefox)
    
    [FONT="Courier New"]~/.local/share/applications/mimeinfo.cache[/FONT] - Same as global [FONT="Courier New"]mimeinfo.cache[/FONT]. Lists the application to use for each MIME-type. This list, merged in alpha order with the global one, is the list displayed by Nautilus in the "open with" listbox. Example: [FONT="Courier New"]text/html=dreamweaver-usercreated.desktop;kde-quanta.desktop;[/FONT]

I**n case of strange behavior (**e.g. the file doesn't open whith the expected application on double click), try to **edit [FONT="Courier New"]mimeinfo.cache[/FONT] and remove the faulty application from the list **(starting with the local version of the file). If this is not enough, try **removing the entire [FONT="Courier New"]mimeinfo.cache[/FONT] file**.

**Resources**
    - [Good article (albeit old) on the topic]("http://www.ces.clemson.edu/linux/fc4_desktop.shtml#gmime") (in particular the section on [file association]("http://www.ces.clemson.edu/linux/fc4_desktop.shtml#gfass")).
    - A Gnome file association editor: [assogiate]("http://www.kdau.com/projects/assogiate/"): distributed as source. Also available in Ubuntu Gutsy  (Universe) as a package.

---

### Post by kdau on 2007-10-29
Hello, I'm the author of assoGiate. Your summary is mostly accurate. If you want a detailed description of GNOME's file type process, see section 5 ("MIME Types") of the System Administration Guide in GNOME help.

You should know, however, that editing [font=monospace]mimeinfo.cache[/font] is not reliable. That file, in either [font=monospace]/usr[/font] or [font=monospace]~[/font], will be replaced whenever other programs make changes to .desktop files. Deleting it is fine, as it will be created again.

If errors persist, [font=monospace]~/.local/share/applications/defaults.list[/font] should be edited to fix the problem MIME type. This is what the Nautilus "Open With" dialog does. Unfortunately, .desktop files involve two MIME types: the .desktop file itself ([font=monospace]application/x-desktop[/font]); and the file it is pointing to (in your case, an HTML file). Nautilus won't change the association for .desktop files, so it doesn't offer to change anything.

The upcoming 0.4.0 release of assoGiate will include "open with" selection. Since assoGiate works with MIME types instead of individual files, you will be able to choose a program for the [font=monospace]text/html[/font] type directly.

---

### Post by richi on 2007-10-29
Kdau,

Thanks for your reply and savvy advice.

I wish I could use your editor assoGiate, but I'm afraid I'll have to wait until I upgrade to Gutsy and get the package, since I was unable to compile your source - actually, I gave up on the first unsatisfied dependencies :(

I do think that file associations should be easier to manage in Gnome. Probably your program will help, thanks for doing it.

---

### Post by dustinharriman on 2007-10-31
I have Ubuntu Gutsy installed, and I just installed and tried "assogiate" (ver 0.2.1-0ubuntu1)  It crashes dumps it's core:

```
:~$ assogiate 
terminate called after throwing an instance of 'Glib::FileError'
Aborted (core dumped)
```

---

