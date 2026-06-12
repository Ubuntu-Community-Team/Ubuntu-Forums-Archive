---
title: "Nautilus problems with opening media files"
date: 2004-12-07
forum: Desktop Environments
---

### Post by adamaster on 2004-12-07
Dear Ubuntu users,

I have a "little" problem with my nautilus. I can't open certain AVI files, and all of the  videos having "WMV" extension.

I got this error message:
> Cannot open anything.wmv
The filename "anything.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

I get also this errormsg when I want to open AVI files. It said, the file has MPG mim.

If i rename it to anything.asf, it works fine. BUT. I have a lot of mounted samba sharings, in which I couldnt rename files.  **How can I solve this problem?** :confused:
Is there any configurations about this?

I have Nautilus 2.8.1 in the 4.10 Warty release of Ubuntu.

Sorry for my horrible english.
Thanks a lot.

---

### Post by TravisNewman on 2004-12-07
Can you copy the videos to your home directory and then take ownership of them so that you can change the extension? 

Also, have you installed the package "w32codecs"?

---

### Post by adamaster on 2004-12-07
I have installed w32codecs, and my mplayer works fine with WMV files.. I have problem with Nautilus, which always checking extension and mime, before starting the default "Open With" program...

Yes, I can copy it to my home dir, but, its a slow, and timewaste solution...  :sad:

---

### Post by adamaster on 2005-01-06
Any other ideas?  :?:

---

### Post by notos on 2005-02-12
Actualy i found a form to do it :D

first open a console and type

sudo gedit /etc/mime.types

Search for "asf"

you'll find some thing like 

> 
application/vnd.ms-asf


only change for
> 
application/vnd.ms-asf				wmv


Save and you are done ;)

---

### Post by ups on 2005-02-12
It basically happens whenever Nautilus detects that the mime-type of the file doesn't correspond to the filename extension. You can also right click and then select the player I think.
The way mentioned above by notos should work for the wmv/asf issue

---

### Post by Ikari on 2005-12-21
I didn't manage to make notos' solution working, so I found another way to do this (see [Nautilus 2.6 and mime types](http://linux.seindal.dk/item8.html)). Hope that it will work.

```

cd /usr/share/mime/packages/
sudo cp -i freedesktop.org.xml freedesktop.org.xml.bak
sudo gedit freedesktop.org.xml

```

Search string "0x3026b275" in the file content and remove the following lines:

```

    <magic priority="50">
      <match value="0x3026b275" type="big32" offset="0"/>
    </magic>

```

What's important here is that Nautilus won't try again to guess whether a file is an ASF file according to its content. Only filenames (*.asf or *.asx) will be used for this.

Then save the file, and enter the following to update the MIME database and restart Nautilus:

```

sudo update-mime-database /usr/share/mime/
nautilus --quit

```

There's a similar process described in [HOWTO: View NFO files](http://ubuntuforums.org/showthread.php?t=83499).

---

