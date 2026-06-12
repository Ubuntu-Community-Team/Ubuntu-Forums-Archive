---
title: "Mapping a File Extension to a MIME Type"
date: 2008-12-17
forum: General Help
---

### Post by Jesdisciple on 2008-12-17
[haXe]("http://haxe.org/") uses .hxml files (essentially) as makefiles, and apparently they are automatically opened by the compiler when double-clicked in Windows.  But in Ubuntu, they are labeled as text/plain so a right-click is necessary to compile.  While they do occasionally need to be edited, more often the source to be compiled has been, so editing should require the right-click.

So, how can I add an extension criterion for MIME type detection?  Thanks!

P.S.  Maybe you can also answer [this related question]("http://www.backports.ubuntuforums.org/showthread.php?t=930758").

---

### Post by mc4man on 2008-12-17
If what your asking is how to change the double left click on .hxml files, then change it in the properties of any .hxml file.

As in r.click -> properties -> 'open with'.
If needed contine on to 'open with other application' and or 'use a custom command'.

The custom command can be whatever achieves the desired result.

In some cases a script is better suited than a straight command, in that case the 'custom command' used would be the script location.

---

### Post by Jesdisciple on 2008-12-20
Sorry for taking so long to reply...

Because the type is detected as text/plain, the same program must be used for .hxml and all other text files.  I want to change the MIME for .hxml, but until someone can tell me how this script will make a suitable workaround:```
#!/bin/bash

if [ `expr "$1" : '.*\(\.hxml\)'` == ".hxml" ]
    then
        haxe "$1"
    else
        gedit "$1"
fi
```

---

### Post by mc4man on 2008-12-20
I don't have any .hxml files but did test your script as far as calling gedit.

Created a new text file in home, named it test1.
pasted your script inside and saved, opened a terminal and went
```
chmod +x test1
```

Then right clicked on a text file -> properties -> open with -> open with other application -> use a custom command. For the command used 
```
./test1
```

Double clicking on a text file opens gedit, so that part works, otherwise nothing would've happen.


Edit : this will work for opening certainly from left or even r. click but I'm not sure about your usage
The line changed can be seen in ~/.local/share/applications/mimeapps.list
(text/plain=userapp-test1-H6H5LU.desktop;gedit.desktop;

there is another line available to edit or insert (by default is

text/x-makefile=gedit.desktop;

so maybe 
text/x-makefile=userapp-test1-H6H5LU.desktop;gedit.desktop;

note : H6H5LU will be different for you

@nd edit : I'd also think there should be a way to add to or edit mimetypes, have to look into. There is on my install in .local/share a mime folder with a packages folder and a globs file. There is a package installed called shared-mime-info with an exec called update-mime-database, maybe something there.

---

### Post by Jesdisciple on 2008-12-20
EDIT: mc4man, I don't understand what you're confused about with my usage.

I also didn't understand what you were saying about mimeapps.list...  How does that differ from the below?

I found these...
[http://linux.seindal.dk/2004/07/01/nautilus-2-6-and-mime-types/](http://linux.seindal.dk/2004/07/01/nautilus-2-6-and-mime-types/) - This got the types properly separated.  I went to the source...
[http://www.freedesktop.org/wiki/Specifications/AddingMIMETutor](http://www.freedesktop.org/wiki/Specifications/AddingMIMETutor) - I asked Google what the MAGIC and MATCH elements were about...
[http://kapo-cpp.blogspot.com/2008/02/register-your-own-mime-type-on-free.html](http://kapo-cpp.blogspot.com/2008/02/register-your-own-mime-type-on-free.html) - OK, that makes more sense.  They specify the name of an XML document's root element.
[http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html](http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html) - The specification for all this stuff.
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="text/x-hxml">
        <comment xml:lang="en">haXe makefile</comment>
        <glob pattern="*.hxml" />
    </mime-type>
    <mime-type type="text/x-hx">
        <comment xml:lang="en">haXe source file</comment>
        <glob pattern="*.hx" />
    </mime-type>
</mime-info>
```

---

### Post by mc4man on 2008-12-21
> I don't understand what you're confused about with my usage.

I wasn't sure if your were initiating the opening of .hxml or your app was.
> 
I also didn't understand what you were saying about mimeapps.list... How does that differ from the below?

Mimeapps.list is more reflective of actions taken elsewhere though you can use it to add lines and or .desktops manually. Lines available are generally what's found in /etc/gnome/defaults.list.

What you posted above can be used I believe to add the mimetype.

What I'll try is this (still don't have a hxml to test, screenshots are easier than describing

In screen one I opened ~/.local/share/mime/packages and created a new .xml named user-extension-hxml.xml

Then I opened it in a text editor and pasted in your code. (screen2

In a terminal I ran this command with the result.

 ```
update-mime-database -V /home/doug/.local/share/mime/
```

> doug@doug-desktop:~$ update-mime-database -V /home/doug/.local/share/mime/
Updating MIME database in /home/doug/.local/share/mime...

Wrote 8 strings at 20 - e8

Wrote aliases at e8 - ec

Wrote parents at ec - f0

Wrote literal globs at f0 - f4

Wrote suffix globs at f4 - 28c

Wrote full globs at 28c - 290

Wrote magic at 290 - 29c


Now when I click on a text file I named test.hxml nothing happens which is good.
So I give it a r. click association and this line shows up in mimeapps.list (I used firefox to try to open

> text/x-hxml=firefox.desktop;

So I think this may do it

If you don't have a mime folder with a package folder inside we can probaby force it's creation or maybe just go ahead and create them

---

### Post by Jesdisciple on 2008-12-21
Here's an archive with the necessary files, but you'll also need to install haXe to see it work.  The expected behavior is that it creates test.swf.

And it did add the MIME; I was able to associate haXe with .hxml separate from text files.

I do have a MIME folder and its packages subfolder; that's where I saved my XML file (as haXe.xml).

---

