---
title: "SDL in Linux compiler?"
date: 2009-05-05
forum: General Help
---

### Post by Logank9k on 2009-05-05
Alright so first of all I'm not sure if I should be asking this here, so sorry if this is in the wrong place.



I am a very new Linux user just starting to get into coding, and I downloaded a program for editing code called "Geany". It's pretty simple and all, but I can't figure out how to use SDL with it.

How do I use SDL with Geany or the built in compiler in Ubuntu?

Thanks in advance, Logan.

---

### Post by 3Miro on 2009-05-05
Geany is not a development environment (such as Visual Studio or Borland C++/Delphi). Geany is code editor, meaning it is a version of gedit (text editor) tuned heavily for code development (and by heavily I mean it rocks big time). The issue is that you have to do some manual work yourself.

You have to make your own makefile for the project. Here is a tutorial that seems to cover the basics:

[http://www.opussoftware.com/tutorial/TutMakefile.htm](http://www.opussoftware.com/tutorial/TutMakefile.htm)

Then you can call the make command and compile your code from within Geany (with one of the shortcuts in the menus). You even get the compiler messages back and can automatically go to the lines with errors and such.

To do SDL, you need to install the appropriate SDL libraries (look for SDL devel). Then you need to correctly link to those (use something like -lSDL or whatever is appropriate, in 7.04 it was -lSDL, but I have not used it since). Here is another tutorial that I found:

[http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/index](http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/index)

Google SDL tutorials, there are tons of those.

---

