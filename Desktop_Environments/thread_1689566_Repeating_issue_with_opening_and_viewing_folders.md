---
title: "Repeating issue with opening and viewing folders"
date: 2011-02-17
forum: Desktop Environments
---

### Post by m3x1c0 on 2011-02-17
Hey all! Im new to the forums and kind of new to the whole linux deal. I must say I have solved many a problem just by lurking these forums in the past couple years and for that I thank y'all very much! I switched to ubuntu in 2008 dual booting it with windows vista. I loved ubuntu but I began to run into a few issues and eventually went to windows only for a while. well Im back into it as of november of 2010 since my windows Os was just ticking me off. I absolutely LOVE linux but ive run into the exact same issues I had before. 
the most pressing issue at the moment is the fact that for some reason when I click on anything in "places" such as documents, music, etc. nothing happens. this includes clicking on the HD on the desktop. I click and then menu goes away as if its going to open the folder but it doesnt. thankfully, going to computer works and I can go from there but I want to know why this has happened seemingly out of the blue and happened both times I installed ubuntu? When I typed sudo nautilus into terminal I get the folowing:

```
xavier@xavier-Vostro1510:~$ sudo nautilus
[sudo] password for xavier: 
Initializing nautilus-gdu extension

** (nautilus:19375): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '19375'

(nautilus:19375): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Im not sure exactly what this means but maybe it is a clue. Im actually planning on reinstalling linux at some point because i am dual booting and running out of room so im gonna kick windows to the curb (it wont load up anyway)but i want to resolve this since its happened twice and will again i am sure. thanks in advance!

---

### Post by Krytarik on 2011-02-17
Hi and welcome to the forums! :)

1. Your general issue is that you somehow inadvertedly chose another program (than nautilus) to handle folders. Check the below posted thread on more info about this.

To solve the issue open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```

[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

2. The error messages you get when launching nautilus as root are common and minor, I also get those, so don't care about it.

But you should never run a graphical app with "sudo", use "gksudo" instead, otherwise you might end up being unable to login, at worst:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Greetings.

---

### Post by m3x1c0 on 2011-02-17
thanks very much for the response! Heres what I have found 

```
xavier@xavier-Vostro1510:~/.local/share/applications$ cat mimeapps.list

[Added Associations]
audio/mpeg=rhythmbox.desktop;
application/x-ms-dos-executable=chromium-browser.desktop;wine.desktop;
application/pdf=libreoffice-writer.desktop;
inode/directory=libreoffice-writer.desktop;
xavier@xavier-Vostro1510:~/.local/share/applications$ 

```

It appears that libreoffice is in the inode/directory. I have no idea what this means or how to change it.. lol im quite the noob, I had to use cd individually on every layer to get to .local/share/applications! (idk why cd that whole thing didnt work)

anyways, how should i change this?

---

### Post by m3x1c0 on 2011-02-17
OH COOL! I forgot your link at the bottom of the post. The easy way to solve this is to right click on a file folder and select 'open with' and select 'file browser' and make sure the check at the bottom that says 'always use this' is checked and bam! back to normal. I'd still like to know how to do this in terminal if possible

---

### Post by Krytarik on 2011-02-17
You could have just opened it with the text-editor, and enter the code I posted. I would remove the libreoffice entry anyways that way. Sorry for the late reply.

EDIT: Command-line-only-solution
```
nano ~/.local/share/applications/mimeapps.list
```- simply enter the given value and remove the old one
- press Ctrl+O to save
- confirm by pressing return/enter
- press Ctrl+X to quit

---

### Post by m3x1c0 on 2011-02-17
That worked wonderfully! THank you very much! For those curious this is my output. 

```
xavier@xavier-Vostro1510:~$ cat .local/share/applications/mimeapps.list

[Added Associations]
audio/mpeg=rhythmbox.desktop;
application/x-ms-dos-executable=chromium-browser.desktop;wine.desktop;
application/pdf=libreoffice-writer.desktop;
inode/directory=nautilus-browser.desktop;

```

Is there anything else in there I need to worry about?

---

### Post by Krytarik on 2011-02-18
Yeah, the one I marked, just remove the entry. FYI, any mimetype not specified here is handled by the system-wide default program. So if you don't know if something specified is correct, just remove the line.
```
[Added Associations]
audio/mpeg=rhythmbox.desktop;
application/x-ms-dos-executable=[COLOR=Red]**chromium-browser.desktop;**[/COLOR]wine.desktop;
application/pdf=libreoffice-writer.desktop;
inode/directory=nautilus-browser.desktop;
```

---

