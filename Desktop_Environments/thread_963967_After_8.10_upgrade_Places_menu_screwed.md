---
title: "After 8.10 upgrade Places menu screwed"
date: 2008-10-30
forum: Desktop Environments
---

### Post by xhero0 on 2008-10-30
I just upgraded my 8.04 to 8.10 thios morning,but now when I use the places menu everything from Home folder to videos brings up totem player....

FRIGGIN' Weird....any clues? Cos I dont have any

Thanx!

Joe M

---

### Post by kneewax on 2008-10-30
I have the same problem!  Except it is VLC that runs on my laptop when I try to use the Places Menu...

---

### Post by mikewhatever on 2008-10-30
In my case, it was Archive Manager :confused:, and here's how I solved it.
Call out Nautilus with alt+f2 --> naulilus, which should open your home folder. Now, right click on any of the folders (Video, Pictures, whatever) and get to the 'Open with' tab. Check the button next to 'Open Folder', that should be it. In my case, the default application was the Archive Manager, so that it would always come up.

---

### Post by kneewax on 2008-10-30
seriously what's with that!!! :confused Thanks Mike!

---

### Post by mikewhatever on 2008-10-30
> **kneewax said:**
> seriously what's with that!!! :confused Thanks Mike!

Welcome. I was so freaked out, you wouldn't believe.:confused:

---

### Post by verhage on 2008-10-30
I had the exact same thing. Not VLC, Totem or Archive manager though, but Rhythmbox...

---

### Post by babuu on 2008-10-31
> **verhage said:**
> I had the exact same thing. Not VLC, Totem or Archive manager though, but Rhythmbox...

And for me it was F-spot... :guitar:

---

### Post by ricardisimo on 2008-10-31
F-Spot as well, and "Open Folder" was already selected, so who knows what was up? It's working now, though. Thanks.

---

### Post by kaivalagi on 2008-11-01
There is a launchpad bug for this: [https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492](https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492)

In summary, the best fix is to edit ~/.local/share/applications/mimeapps.list removing the offending ?.desktop entries against the inode/directory entry.

e.g. from:
```

inode/directory=userapp-baobab-OO53FU.desktop;nautilus-folder-handler.desktop;nautilus.desktop;userapp-nautilus-XXZ2JU.desktop;
```

to:

```
inode/directory=nautilus-folder-handler.desktop;
```

There is no need to go through all the places bookmarked changing the "open with" options

---

### Post by Misat on 2008-11-01
Maybe I'm just an idiot, but it didn't work for me.

---

### Post by Misat on 2008-11-01
I did the whole alt + f2 thing, but I don't understand the directions past that.  What is Nautilus?

---

### Post by mikewhatever on 2008-11-01
> **Misat said:**
> I did the whole alt + f2 thing, but I don't understand the directions past that.  What is Nautilus?

Hi Misat, Nautilus is a file browser program that allows you to graphically access files and folders. If you press alt+f2 and type 'nautilus', the program will open your home folder in a window. Hope that's a bit clearer now.

---

### Post by Quisling on 2008-11-04
And then once Nautilus is open, you want to right-click --> Properties --> Open With Tab --> select "Open Folder" action.

Also, thanks a bunch Mike, I was lost as well (Archive Manager).  Definitely tons of fun relearning all this operating-system specifc stuff :-D

---

### Post by majoda on 2010-08-27
no computer expert, just cut & paste
copy below into terminal

gksudo gedit cat ~/.local/share/applications/mimeapps.list

 below list came...

 Added Associations]
 message/rfc822=gedit.desktop;openoffice.org-writer.desktop;thunderbird.desktop;
 application/octet-stream=eog.desktop;
 application/vnd.ms-powerpoint=openoffice.org-impress.desktop;openoffice.org-writer.desktop;nautilus-browser.desktop;
 application/x-ole-storage=openoffice.org-draw.desktop;
 inode/socket=f-spot-view.desktop;
 application/x-extension-part=vlc.desktop;
 inode/directory=vlc.desktop;nautilus-folder-handler.desktop;transmission.desktop;nautilus-browser.desktop;
 application/x-executable=gedit.desktop;
 application/x-extension-drive=nautilus-browser.desktop;
 application/x-extension-link=nautilus-browser.desktop;
 image/png=eog.desktop;f-spot-view.desktop;gimp.desktop;firefox.desktop;nautilus-browser.desktop;
 text/x-ldif=gedit.desktop;openoffice.org-writer.desktop;thunderbird.desktop;


 after ..
inode/directory=
delete ( vlc.desktop)
should read..
inode/directory=nautilus-folder-handler.desktop;transmission.desktop;nautilus-browser.desktop;
 worked for me!!!!

---

### Post by majoda on 2011-03-05
after a upgrade and also having home under separate partition 
/home/USERNAME/.local/share/applications/mimeapps.list
I had to change file

see below

[Added Associations]
message/rfc822=gedit.desktop;openoffice.org-writer.desktop;thunderbird.desktop;
application/octet-stream=eog.desktop;
application/vnd.ms-powerpoint=openoffice.org-impress.desktop;openoffice.org-writer.desktop;nautilus-browser.desktop;
inode/socket=f-spot-view.desktop;
application/x-extension-part=vlc.desktop;
application/x-executable=gedit.desktop;
application/x-extension-drive=nautilus-folder-handler.desktop;nautilus-browser.desktop;mount-archive.desktop;file-roller.desktop;vlc.desktop;
application/x-extension-link=nautilus-browser.desktop;
image/png=eog.desktop;f-spot-view.desktop;gimp.desktop;firefox.desktop;nautilus-browser.desktop;
text/x-ldif=gedit.desktop;openoffice.org-writer.desktop;thunderbird.desktop;
x-content/image-dcf=f-spot-import.desktop;eog.desktop;
application/x-ole-storage=openoffice.org-writer.desktop;openoffice.org-impress.desktop;evince.desktop;gimp.desktop;
application/x-ms-dos-executable=shotwell-viewer.desktop;f-spot-view.desktop;file-roller.desktop;nautilus-autorun-software.desktop;eog.desktop;
application/rdf+xml=userapp-qcad-1KGZPV.desktop;
image/vnd.dwg=bricscadv11.desktop;qcad.desktop;userapp-qcad-1KGZPV.desktop;
video/mpeg=totem.desktop;
inode/directory=nautilus-folder-handler.desktop;

---

### Post by Krytarik on 2011-03-06
It seems to be a good idea to remove the file altogether from time to time! ;-) Because there are quite a lot inappropriate assignments in yours.

---

