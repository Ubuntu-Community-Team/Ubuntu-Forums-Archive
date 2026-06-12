---
title: "Cannot open file from a Nautilus double-click??"
date: 2008-02-02
forum: Desktop Environments
---

### Post by mlanza on 2008-02-02
I have been faced with a Linux annoyance of late, regarding trying to open files via Nautilus.  Certain text only files I wish to double-click and have them automatically open in GEdit.  Instead, I get an annoying dialog that says:

[INDENT]The filename "my file.rhtml" indicates that this file is of type "rhtml document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
[/INDENT]

The file was created by me and poses no security risk.  This happens with various file types.  It is completely annoying and brings to mind the recent Mac commercial where they poke fun at Vista's advanced security features.  

How can I turn this warning off and simply launch the file with a double-click?  Right now, I have to right click and use a context menu to open files.  For code development, this is annoying.

I'd appreciate any advice.  Thanks.

---

### Post by mlanza on 2008-02-02
By the way, in case you're wondering I did set the 'opens with' property to "Text Editor".  I also tried setting the File Associations.

---

### Post by SunnyRabbiera on 2008-02-02
yeh this is annoying, but i got a fix:
go into nautilus and then to the edit menu
then go to "preferences"
go to the "behavior" tab and in the "executable text files" section click on the box/circle.whatever next to the option that says "view executable text files when they are opened"
close the window and you are done.

This is feature that I think the nautilus folks built in for developers for configuration purposes and such but it has this annoying side effect.

---

### Post by FuturePilot on 2008-02-02
> **SunnyRabbiera said:**
> yeh this is annoying, but i got a fix:
go into nautilus and then to the edit menu
then go to "preferences"
go to the "behavior" tab and in the "executable text files" section click on the box/circle.whatever next to the option that says "view executable text files when they are opened"
close the window and you are done.

This is feature that I think the nautilus folks built in for developers for configuration purposes and such but it has this annoying side effect.

No this is a different problem. This usually results from a Nautilus problem where it looses the file association. Try a
```
killall nautilus
```
and see if that might fix it
Or it could be that the file is corrupted.

---

### Post by mlanza on 2008-02-02
Thanks to all for the feedback... I continued to work on the issue.  Here is what I did:

1. Updated ~/.local/share/mime/packages/Overrides.xml:

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="application/x-ruby">
    <alias type="application/ruby" />
    <comment xml:lang="en">Ruby Rake Tasks</comment>
    <glob pattern="*.rake"/>
  </mime-type>
  <mime-type type="application/x-ruby">
    <comment xml:lang="en">Rakefile</comment>
    <glob pattern="Rakefile"/>
  </mime-type>
  <mime-type type="text/html">
    <comment xml:lang="en">HTML Markup</comment>
    <glob pattern="*.html"/>
    <comment xml:lang="en">eRB HTML Markup</comment>
    <glob pattern="*.rhtml"/>
  </mime-type>
  <mime-type type="application/x-javascript">
    <comment xml:lang="en">eRB JavaScript</comment>
    <glob pattern="*.rjs"/>
  </mime-type>
  <mime-type type="text/xml">
    <comment xml:lang="en">eRB XML</comment>
    <glob pattern="*.rxml"/>
  </mime-type>
  <mime-type type="text/x-yaml">
    <comment xml:lang="en">YAML</comment>
    <glob pattern="*.yml"/>
  </mime-type>
  <mime-type type="application/x-extension-dat">
		<comment>dat document</comment>
		<glob pattern="*.dat"/>
	</mime-type>
	<mime-type type="application/x-extension-rake">
		<comment>Rakefile</comment>
		<glob pattern="*.rake"/>
	</mime-type>
</mime-info>

Note that rhtml and html are included together.

2. In console, entered

export XDG_DATA_DIRS="~/.local/share/:$XDG_DATA_DIRS"

in preparation for:

3. In console, entered:

sudo update-mime-database ~/.local/share/mime


The key to this solution I believe occurred in step 1.  Getting the file extensions mapped to the proper MIME types.

The post that got me on the right track was:
[http://snakesgemscoffee.blogspot.com/2007_04_01_archive.html](http://snakesgemscoffee.blogspot.com/2007_04_01_archive.html)

---

### Post by alecz20 on 2008-07-30
I have the same problem with .txt files.
Steps to reproduce:

1) right click -> create new file
2) give file name "xxx.txt"
3) double click (after having the options given by SunnyRabbiera)
4) write any simple text, for example your name
5) save and close
6) attempt another double-click

7) notice the error message given by nautilus.

I wanted to get rid of the prompt to choose display every time and now I got this annoying message popping up.

As for mlanza suggestion, I can't find:
/.local/share/mime/packages/Overrides.xml
[EDIT]
 NVM, I found the file it's actually in my home folder, however it seems a pain to update it because there already is a lot of stuff in there, any suggestions?"
[/EDIT]

actually there are no hidden folders in /

The only workaround I found to work is the following:
1) Open the file via Right click with gedit
2) save without an extension
3) rename the file from nautilus with the extension .txt

I don't how how this makes sense!

---

### Post by K.Mandla on 2008-07-30
Moved to Desktop Environments.

---

### Post by mcduck on 2008-07-31
I've had the same problem with HTML and XML documents, and it was solved by using a correct documet type declaration in the beginning of the document. Without one, the document is seen as a text file even though it has a .html as file name extension.

For example, for XHTML document, the first line needs to hacve following text:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```
Without that, it's not a proper XHTML document (based on it's contents).

---

