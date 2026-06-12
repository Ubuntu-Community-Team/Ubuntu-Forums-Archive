---
title: "Custom icon size into a GTK's open file dialog."
date: 2010-12-25
forum: Desktop Environments
---

### Post by negora on 2010-12-25
Hello to you all:

I'm wondering if it's possible to change the icon size of the typical GTK open file dialog (i.e. in Firefox), just like it's possible with Nautilus or other file explorers.

I need this to be able to preview several images at the same time, since there's no possibility to change the kind of view to something like thumbnails's mode (or at least that's the conclusion which I got after reading many older threads in these boards).

Obviously the preview widget it's not useful because I need to check many files at a single glance.

Is there any kind of configuration file to change that? Or is it defined by the programmers into every program's code?

Thank you for your help :) .

---

### Post by andreselsuave on 2011-09-20
I have the same issue. Did you find any solution yet?

---

### Post by negora on 2011-09-20
Unfortunately I never was able to find a solution. The only workaround which came to my mind was to use Nautilus and drag the wanted files into the application. At least in those programs in which it's possible, of course.

The problem seems to have to do with something called GtkFileChooser, which is the widget which GTK applications use to allow you to open files.

Here there's a short thread where it's discussed why it has not been fixed yet: [http://lists-archives.org/gtk-devel/06075-gtkfilechooser-thumbnails-history.html](http://lists-archives.org/gtk-devel/06075-gtkfilechooser-thumbnails-history.html) .

---

### Post by andreselsuave on 2011-09-20
I found a pretty nice solution with your answer. You can right click on a folder and click properties and instead of clicking on the icon for browsing, you open a nautilus window (which will display the thumbnails) and drag the image to the current icon of the properties window.

For me it solves the problem, what do you think?

---

### Post by negora on 2011-09-21
**andreselsuave:** I'm not sure if I understood it, he he he. Could you post a screen capture?

Thinking about the days when I posted this message, I've remembered that it occurred to me another and better solution. I've a relative who asked (ordered XD ) for a better solution than dragging icons, since he's using a laptop and using a touchpad for this task may be frustrating some times.

What I did was to make a shell script for the context menu of Nautilus which allowed me to copy the full path of the file. This way, I can use Nautilus to check the thumbnails, choose the desired file, right click on it, choose the option to copy the path, and then, I only have to paste it into the application which I'm using. It may sound complex, but once you get used to it, it's comfortable.

---

### Post by negora on 2012-06-03
Has anyone any news about this issue? The most recent information which I got is from this Ask Ubuntu thread: [http://askubuntu.com/questions/14785/how-can-i-see-large-thumbnails-of-the-files-i-want-to-attach-to-an-e-mail](http://askubuntu.com/questions/14785/how-can-i-see-large-thumbnails-of-the-files-i-want-to-attach-to-an-e-mail) .

It's really shocking that Gnome and GTK have advanced so much in other areas, but still keep such an ancient dialog window :S . This one and the impossibility to directly edit the destination path in the printing dialog window (plus the fact that it does not remember the last one that was used), contrast a lot with the modern look of Ubuntu.

Why does not Canonical help the GTK developers to improve these 2 dialogs? Thank you.

---

