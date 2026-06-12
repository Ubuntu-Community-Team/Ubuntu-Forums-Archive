---
title: "FoxitReader"
date: 2009-06-02
forum: General Help
---

### Post by Chazzan on 2009-06-02
There is now a "Desktop Linux" version of Foxit Reader, which I would love to add, but as a total noob, I'm at sea as to how to go about it.  Step by step instruction, would be most welcome!
thanks!
Chazzan

---

### Post by juancarlospaco on 2009-06-02
Ubuntu comes with a lightweight PDF Reader already installed.
:)

---

### Post by aysiu on 2009-06-02
Does the new version work?

The old one didn't. More details here:
[https://help.ubuntu.com/community/Foxit](https://help.ubuntu.com/community/Foxit)

---

### Post by albinootje on 2009-06-02
> **Chazzan said:**
> Step by step instruction, would be most welcome!


1) Download the .tar.bz file.
2) Make a new directory in your home directory, and move the .tar.bz file there.
3) Open it with the Archive Manager, see screenshot nr.1
4) Choose extract.
5) Close the Archive Manager, and open the file manager (Nautilus) in that directory with the extracted files.
6) Make a link for the executable. See screenshot nr.2
7) Move the link to your desktop.
8) Double-click on that new link.

Just tested it, and it works fine so far.

---

### Post by rcayea on 2009-06-02
> **Chazzan said:**
> There is now a "Desktop Linux" version of Foxit Reader, which I would love to add, but as a total noob, I'm at sea as to how to go about it.  Step by step instruction, would be most welcome!
thanks!
Chazzan

To answer your question. Click the link I provided and look at the screen shot I made. Instead of clicking on download, click on "More download" which I circled with my paint brush program in the screen shot. Then select the .deb file and you should be able to go from there. 

[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)

---

### Post by aysiu on 2009-06-02
Wow! There's a .deb for it? Who knew?

Yeah, just download this file:
[http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb)

And double-click it.

---

### Post by Chazzan on 2009-06-02
Thanks!!  Too easy.  The reason for wanting to go with foxit over the installed .pdf reader is the ease of saving interactive forms.

---

### Post by Wiebelhaus on 2009-06-02
> **aysiu said:**
> Wow! There's a .deb for it? Who knew?

Yeah, just download this file:
[http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb)

And double-click it.

Nice find , thanks.

---

### Post by UbuntuNerd on 2009-06-02
> **aysiu said:**
> Wow! There's a .deb for it? Who knew?

Yeah, just download this file:
[http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb)

And double-click it.

thanks for the link, it seems to work good :)

---

### Post by jenkinbr on 2009-06-03
Bingo!

Works beautifully.  Loads faster then the Ubuntu Default!

---

### Post by Jimmynemo2 on 2009-06-03
Glad to know about the .deb. Thats great.

---

### Post by Chazzan on 2009-06-03
> **Chazzan said:**
> Thanks!!  Too easy.  The reason for wanting to go with foxit over the installed .pdf reader is the ease of saving interactive forms.
...which the Linux version doesn't do yet, though they promise to add features soon.  Oh, well.

---

### Post by kaibob on 2009-08-10
I just downloaded and installed Foxit Reader for Linux. I thought I would add a few comments to this thread. 

* The deb file installed without issue.

* The Reader does not remember whether the navigation panel is enabled or not. I have no use for the panel, and it gets in the way, so I have to remove it every time I load the software. Fortunately, there is a toolbar button for this.

* The Reader does not always remember whether it was maximized when last used and opens very small. So, most of the time when loading the software I have to click on the maximize button.

* The Reader's menu's are often scrunched up with options overlaying other options. I'm sure this is my fault, as I use a large font, but this doesn't happen with other apps.

* I get the impression that version 1.1 will be released soon. 

* The Reader is fast and does a good job overall. With just a fixes, I would make it my default PDF reader.

---

### Post by kaibob on 2009-08-13
Foxit Reader 1.1 has been released. I installed the deb file, but the reader won't run. Instead, it issues the error message "Could not launch 'FoxitReader' Failed to execute child process "FoxitReader" (No such file or directory)." A lot of nice new features though. :P

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by lorenz_b on 2009-08-13
The update didn`t work for me. I have ubuntu 9.04 x64 installed and had the older foxitreader (i think it was 1.0.1). I I wanted to update via the .deb packet but now foxitreader doesn`t open.

cheers,
Lorenz

---

### Post by michy99 on 2009-08-13
> **kaibob said:**
> Foxit Reader 1.1 has been released. I installed the deb file, but the reader won't run. Instead, it issues the error message "Could not launch 'FoxitReader' Failed to execute child process "FoxitReader" (No such file or directory)." A lot of nice new features though. :P

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

I couldn't find a .deb for 1.1 so I got the tarball. It loads, but when I try to open a document, it crashes.```
(H&#65533;8
tReader:8896): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/gdkpixbuf-drawable.c:1247: Source drawable has no colormap; either pass in a colormap, or set the colormap on the drawable with gdk_drawable_set_colormap()

(H&#65533;8
tReader:8896): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(H&#65533;8
tReader:8896): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 16
The program 'H&#65533;8
tReader' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 5479 error_code 8 request_code 70 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by kaibob on 2009-08-13
I extracted the FoxitReader executable from the deb and copied it to the /usr/bin directory. FoxitReader works fine now. Unfortunately, the reader still does not remember that it was maximized and that the navigation panel is off.

---

### Post by evencoil on 2009-09-19
> **kaibob said:**
> I extracted the FoxitReader executable from the deb and copied it to the /usr/bin directory. FoxitReader works fine now. Unfortunately, the reader still does not remember that it was maximized and that the navigation panel is off.

Same exact experience, 64 bit Ubuntu 9.04.

---

### Post by bubblehead74 on 2009-09-29
I have an older notebook, which slows down to a crawl when I open the Adobe Reader malware. I need to open PDFs directly in Firefox. Can Foxit Reader do it? I know it can on Windows, but does it work on Ubuntu?

---

### Post by atentik on 2009-11-02
> **kaibob said:**
> Foxit Reader 1.1 has been released. I installed the deb file, but the reader won't run. Instead, it issues the error message "Could not launch 'FoxitReader' Failed to execute child process "FoxitReader" (No such file or directory)." A lot of nice new features though. :P

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

This error is true for me also. Anybody figured out how to go about it?

---

### Post by gedinfo on 2010-02-02
For the error on start up after upgrade, I had the same issue. 
1.0  was installed, I performed what I thought was an upgrade of 1.1, and got that message.  I resolved it by starting the update manager and removing foxit, then reinstalling 1.1.

I really like this application; use it as my default pdf reader on all of my Windows based PCs.

One issue that I have though, is how do I make Foxit my default instead of Evince?

---

### Post by kaibob on 2010-02-04
> **gedinfo said:**
> For the error on start up after upgrade, I had the same issue. 
1.0  was installed, I performed what I thought was an upgrade of 1.1, and got that message.  I resolved it by starting the update manager and removing foxit, then reinstalling 1.1.

I really like this application; use it as my default pdf reader on all of my Windows based PCs.

One issue that I have though, is how do I make Foxit my default instead of Evince?

To make Foxit the default for PDF files do the following: load Nautilus file manager; right-click on a PDF file; select properties and then the open-with tab. If Foxit is shown, select it as the default. If not, click on the add button and add Foxit.

---

### Post by msaraiva on 2010-04-06
> **michy99 said:**
> I couldn't find a .deb for 1.1 so I got the tarball. It loads, but when I try to open a document, it crashes.```
(H&#65533;8
tReader:8896): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/gdkpixbuf-drawable.c:1247: Source drawable has no colormap; either pass in a colormap, or set the colormap on the drawable with gdk_drawable_set_colormap()

(H&#65533;8
tReader:8896): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(H&#65533;8
tReader:8896): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 16
The program 'H&#65533;8
tReader' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 5479 error_code 8 request_code 70 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Change the X Server color depth to 24bit, and it should work without crashing.

---

### Post by catzlai on 2010-05-05
I am using Lucid and I downloaded the .deb v1.1 file from Foxit but it failed to install:

```
sudo dpkg -i FoxitReader_1.1.0_i386.deb
(Reading database ... 222417 files and directories currently installed.)
Preparing to replace foxitreader 1.1-0 (using FoxitReader_1.1.0_i386.deb) ...
Unpacking replacement foxitreader ...
Error in file "/usr/share/applications/kde4/kfontview.desktop": "fonts/package" is an invalid MIME type ("fonts" is an unregistered media type)
Error in file "/usr/share/applications/clamtk.desktop": "vms/exe" is an invalid MIME type ("vms" is an unregistered media type)
Error in file "/usr/share/applications/gnumeric.desktop": "zz-application/zz-winassoc-xls" is an invalid MIME type ("zz-application" is an unregistered media type)
Setting up foxitreader (1.1-0) ...

Error in file "/usr/share/applications/kde4/kfontview.desktop": "fonts/package" is an invalid MIME type ("fonts" is an unregistered media type)
Error in file "/usr/share/applications/clamtk.desktop": "vms/exe" is an invalid MIME type ("vms" is an unregistered media type)
Error in file "/usr/share/applications/gnumeric.desktop": "zz-application/zz-winassoc-xls" is an invalid MIME type ("zz-application" is an unregistered media type)
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
```

Any idea?

---

### Post by catzlai on 2010-05-20
Although the .deb package doesn't work, I just untar the tar.bz2 file on the foxit reader website and it works fine now.

---

### Post by colin.p on 2010-05-20
Interesting, I also use lucid (clean install) and the deb installed fine. I again have foxitreader as my default pdf reader.

Colin

btw, I really like lucid, absolutely no issues (as of yet) on my ancient XP 1800+, GF 6200, 786MB "turtle".

Colin

---

