---
title: "RDP file extensions and plain text File Types"
date: 2010-07-15
forum: Desktop Environments
---

### Post by eimhin85 on 2010-07-15
Hi all,

Sorry if this is a mundane question, but i could not find a solution. 
Basically, I have a selection of .rdp shortcuts to various machines, but they are considered the file type "plain text document (text/plain)" so if i change it to open with to tsclient, all of that file type opens with tsclient. and if i change it to gedit, all the rdp files open with gedit.

Is there a way to create a custom file type dependant on the extension rdp, or is there a way to set tsclient to open by extension rather than filetype?

cheers

---

### Post by sirctseb on 2010-09-17
Did you ever figure this out? I am trying to achieve the same thing

---

### Post by eimhin85 on 2010-09-17
Hi, yeah, as a matter of fact, i did. 

Basically, I had to add a mime type for it, which went something like this:-

do:
```
sudo gedit /usr/share/mime/packages/Overrides.xml
```I think its a new empty file so add this:-
```
<?xml version='1.0' encoding='utf-8'?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
[COLOR=Blue]  <mime-type type="[COLOR=Red]text/RDP details file[/COLOR]"><comment>[COLOR=Red]RDP[/COLOR]</comment><glob pattern="*.[COLOR=Red]rdp[/COLOR]"/></mime-type>[/COLOR]
</mime-info>
```save and close.
this creates the mime type exception based on what the extension is.
(of course, the blue line you can repeat as many times as you like for other extension types that you want excepted too. 
The red parts are the variables. The first two are what the 'file type' will be called, and the third one is the extension pattern that it looks for.)

This updates the mime database so the changes take effect.:-
```
sudo update-mime-database /usr/share/mime
```then just right click on your rdp file and go to the "properties" -> "open with" -> "add" - "use custom command" and type in "tsclient"

then that should do it.


This can come in handy too. it just reports what the mime type is of whatever file you want to check (in red again) (im a sucker for colour coding :p)
```
gnomevfs-info [COLOR=Red]so2.rdp[/COLOR] | grep MIME
```

---

