---
title: "Equivalent Qt Creator for GTK"
date: 2009-04-09
forum: General Help
---

### Post by DavidDave on 2009-04-09
Hi all!
What is the equivalent Qt Creator program for GTK?
Sorry for my English and thanks!;)

---

### Post by mb_webguy on 2009-04-09
If you're talking about a user interface builder, then [Glade]("http://glade.gnome.org/") is probably your best bet, though you could also try [Enveria]("http://enveria.sourceforge.net/") or [Gazpacho]("http://gazpacho.sicem.biz/").

If you're talking about IDEs for developing GTK applications, there's [Anjuta]("http://www.anjuta.org/") (for C/C++), [MonoDevelop]("http://monodevelop.com") (primarily for C#, but supports a number of other languages including C/C++, Java, Python, and Visual Basic.NET), and [Geany]("http://www.geany.org/") (which leans more toward being a text editor specialized for programming rather than a true IDE, and supports several languages including C/C++, Java, PHP, and Python).  I've also seen [Eclipse]("http://www.eclipse.org") suggested, but it doesn't seem to be as oriented toward developing GTK applications as much as the others.

---

### Post by dozy on 2011-01-27
[B]You can use QT Creator to write GTK apps !

Here's how:[/B]
1. Create an 'Empty QT Project' to hold your new GTK project.
2. Create a custom makefile for your GTK project.
3. Go into the new project's Settings and remove the 'QMake' step under 'Build Steps' using the 'Remove build step' drop-down; We don't want to use QT's Make process.
4. You should be left with one 'Make' step under 'Build Steps' (if there isn't one, add it using the 'Add build step' drop-down. You want to add a 'Make' step, ***NOT*** a 'QTMake' step). Click the 'Show Details' button beside the 'Make' step to access the 'Make arguments' box. Enter "-f [your custom gtk makefile name]" (without quotes) into the 'Make arguments' box. 
For example: I entered "-f custom_makefile" (without quotes).

You'll need to do the steps above for the 'Debug' and 'Release' configurations.

I've been using this with gtkmm. It works great, including code-completion and debugging.

**Note for code-completion:**
You'll have to add the gtk include path to the QT project file (.pro file) so QT can parse it for you. Your project will still compile correctly without it (providing that your makefile has the proper gtk include/lib paths), but code-completion will not work.
I added the following three lines to my .pro file to get code-completion working for gtkmm.
INCLUDEPATH += "/usr/include/gtkmm-2.4/"
INCLUDEPATH += "/usr/include/glibmm-2.4/"
INCLUDEPATH += "/usr/include/sigc++-2.0/"

For normal gtk i assume you would just add something like:
INCLUDEPATH += "/usr/include/gtk-2.0/"

After adding the include paths, you may have to restart QT Creator and then reopen your project for QT Creator to recognize and parse the files in the path.

**Note for debugging:**
Don't forget to add the -g compiler option in your makefile to enable debug symbols.

**That's It !**
Good Luck, and Happy GTK Coding in QT Creator!

---

### Post by carlos3000 on 2011-06-30
hi its my fist post :popcorn:

hello this is my first post.

 I have an idea for this simple problem, just put it in the file. pro
to uses gtk in c

```

SOURCES += \
    lol.cpp

CONFIG += link_pkgconfig
PKGCONFIG +=--cflags gtk+-2.0
PKGCONFIG +=--libs gtk+-2.0

```

---

