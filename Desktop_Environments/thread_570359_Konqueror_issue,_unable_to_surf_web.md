---
title: "Konqueror issue, unable to surf web"
date: 2007-10-08
forum: Desktop Environments
---

### Post by Architeuthis on 2007-10-08
Hello all,

I have a strange issue with Konqueror. I am unable to use Konqueror as a web browser, because whenever I click on a link (in any website) Konqueror asks me if I want to save the link as (a file).  Because of this I am completely unable to surf the web with Konqueror, I still have firefox of course. But I am interested to explore Konqueror's webbrowser functionality.
So does anyone know how to solve this problem?

---

### Post by matigol on 2007-10-08
I don't know.
have you look after the preferences ? 

I sincerely think there is a problem of configuration... You can choice to save the link, maybe open it in a new tab or other ? 

I am not sure, i am a gnome user.

:)

---

### Post by Architeuthis on 2007-10-08
I had already checked the preferences dozens of times before I made this post, but I haven't found anything which solves the problem thus far. 

I am a gnome user too but I am curious to check out konqueror.

---

### Post by GeneralZod on 2007-10-08
Sounds like a misconfiguration to me.  Try opening konqueror via the command-line with e.g.

```

konqueror http://ubuntuforums.org/forumdisplay.php?f=11

```

and browse around for a bit like that.  If it still doesn't work, post here again.

---

### Post by Architeuthis on 2007-10-08
Here's the output:

```
konqueror http://ubuntuforums.org/forumdisplay.php?f=11
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.6/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.6/./libkonq/konq_pixmapprovider.cc (81)

```

The problem is, I don't get any new output when I try to click on a link. Only the "Save file as" menu popsup. When I do save the link I get this output. But I think this is just the normal output for saving files.


```
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by GeneralZod on 2007-10-08
Ok, something weird going on there.

Go into Settings -> Configure Konqueror -> File Associations, type html into the search box, and make sure text/html opens embedded via khtml, as shown here:

[http://etotheipiplusone.com/konqueror-html.png](http://etotheipiplusone.com/konqueror-html.png)

---

### Post by Architeuthis on 2007-10-08
Thanks a lot! That solved the problem! The option "show file in separate viewer" was selected in stead of "show file in embedded viewer".

---

### Post by GeneralZod on 2007-10-08
> **Architeuthis said:**
> Thanks a lot! That solved the problem! The option "show file in separate viewer" was selected in stead of "show file in embedded viewer".

Great! No idea how that happened, but I'm glad it's working now :)

---

### Post by ludomatic on 2008-01-16
Good job General, I just solved the same problem with your help, THANKX!!!!

---

