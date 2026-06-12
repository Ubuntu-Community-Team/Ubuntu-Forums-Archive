---
title: "Installing apps outside synaptic"
date: 2009-04-22
forum: General Help
---

### Post by David C. on 2009-04-22
I've downloaded PySoy and want to install it, problem is I don't how to do this on a linux system. I am VERY new to linux, having switched over during this passed weekend. Most everyone knows w/Windows you unzip and extract the set up file or .exe and off it goes. But with linux I don't know what to do with the tar.gz. 

I've saved it to the desktop and extracted the the files to the desktop, thinking that's what needs to be done. Entered $sudo apt-get install pysoy 
only to get an error stating couldn't find package, yet it's sitting on the desktop. I deleted the extracted files and tried again...same error. I delete the tar.gz file and redownloaded. Tried again...same error. 


According to the install instructions:

> You'll want to make sure these are installed before proceeding:
  Python    >=2.3
  OpenGL    >=1.2
  GLEW      >=1.4
  ODE       >=0.8
  GLib      >=2.0
  Cairo     >=1.4
  Ogg       >=1.1.2
  Vorbis    >=1.1.2
  Theora    >=beta2

If you're using a binary-based distribution (such as Ubuntu, Fedora, etc) make sure you install the -dev versions of these dependencies.

You will also need a working C compiler environment for building Python 
modules (same as your Python version was built with) and, when compiling 
from Trunk, you'll need Pyrex 0.9.6.4 or above.

Compiling
---------
If you're reading this you've already downloaded PySoy.  If you have all 
the dependencies installed you should, now, be able to type:
  python setup.py build

and watch it compile.  When building from Trunk (svn) it'll first build 
the .c files from Pyrex sources.  Any compile errors not linked to a 
missing dependency should be reported to our bug tracker (below).

If everything has gone well you can now install the PySoy module with:
python setup.py install

I don't know if I have all the dependencies, though Python and OpenGL I do. 

I entered python setup.py build into the terminal but got an error saying it can't open the file because no file or directory exists. It does, I've opened it and read through the code. I'm at a lost as how I should proceed. I've read through the documentation at pysoy.org and there is only one source file to download for linux users. There's got to be an easier way of doing this. So any assistance would be appreciated. Thanks.

---

### Post by James_Lochhead on 2009-04-22
Well my first suggestion to you would be to try and find a .deb if you can. Debs in Ubuntu are (kind of) like exes in Windows. If there is a deb available it will be much easier for you.

If there is not a deb available you need to do the following:

[LIST]
[*]Go to System > Administration > Synaptic Package Manager.
[*]Search and install all the packages listed as dependencies (the ones on the list in your post).
[*]In addition to those packages you will also need packages of that end with dev and have the same name. For example, if you had to install firefox you also need firefox-dev.
[*]Please note that some packages might have lib in front of their name. If you cannot find the right packages try searching for the packages with lib in front of the name.
[*]Once everything is installed you need to execute the python script.
[*]Open a terminal.
[*]Type sudo apt-get install build-essential 
[*]Type cd ~/Desktop
[*]Type ls
[*]The name of the directory that you extracted to will now be listed.
[*]Type cd <put name of directory here>
[*]Now type python setup.py build
[/LIST]

That should do it (as far as I can tell). 

This is not a process for a beginner really.

---

### Post by Peter09 on 2009-04-22
When running any task not in the path directive you need to be specific about where it is.

If you are in the same directory as the task you will need to run it like

./<task name>

./ means 'this directory'

---

### Post by David C. on 2009-04-22
James - Thanks, I'll give it a go.

Peter09 - Thanks.

---

### Post by Ms_Angel_D on 2009-04-22
Nevermind wrong thread ;)

---

### Post by Sef on 2009-04-22
Read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by David C. on 2009-04-22
Sef - Thanks!

---

