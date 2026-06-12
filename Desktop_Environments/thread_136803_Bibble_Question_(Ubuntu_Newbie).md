---
title: "Bibble Question (Ubuntu Newbie)"
date: 2006-02-26
forum: Desktop Environments
---

### Post by fuxxtor on 2006-02-26
I'm a professional photographer attempting to get away from Windows entirely.  I've got a powerbook (running OSX) that I can use until Linux fully supports my editing needs (Gimp is pretty good, but lacks EXIF and IPTC functionality, not to mention RAW support that I need).

Until Gimp catches up, I'm investigating Bibble Pro as my photo editing solution.  It's not open source, nor is it free, but it looks like it will do what I need it to.  Besides, I have no problem paying for good software.

I've tried to download the installer but it's either a .deb or .rpm file, and I'm not sure if I can install either. 

Any help?

Thanks!

Oh yeah.  Ubuntu 5.10 Breezy.  Gnome WM.

---

### Post by BeatBoxRocker on 2006-02-26
The packages for your system have the extension .deb (debian) because this distribution is based on Debian. 

To install a debian package open console and type: sudo dpkg -i packagename.deb

Try first to find program packages for Ubuntu but if they dont exist just try normal .deb.

Saludos!

---

### Post by pestilence on 2006-02-26
There is also the solution of Crossoffice which allows you to run photoshop on Linux.

---

### Post by pestilence4hr on 2006-02-26
I was wondering what exactly you can't do in linux?  For example, you can read EXIF info with free tools.  Not sure what the other tasks are.

edit: aacck another pestilence!

---

### Post by fuxxtor on 2006-02-26
Thanks all for your help.

For anyone searching this forum, xlibs is the only dependency called by Bibble 4.5 in Ubuntu 5.10.

just sudo apt-get install xlibs

and you're good.

Now if only I could figure out how to launch the darn thing!

Cheers,

---

### Post by fuxxtor on 2006-02-26
Hi pesilence4r,

Since you asked, strict IPTC adherence (even though there is no standard beyond XMP's suggestions) is demanded by my editors.  It's not so much being able to view them on my end as it is preserve EXIF data throughout the editing process as well as modify and preserve IPTC fields for captioning, copyright, special instructions, etc.

Additionally, although I laud Gimp for supporting the D2X RAW files at all, Bibble does it significantly better.  I can't criticize Gimp, as it's freeware.

Thanks!

---

### Post by PsychoTrauma on 2006-02-26
Try pushing alt-f2 and typing bibble in the window that opens.

You can add a menu entry if that works by using the same command. Just use the menu editor that comes with breezy.

---

### Post by xmastree on 2006-02-26
[QUOTE=fuxxtor]not to mention RAW support that I need[/QUOTE]
Look at [**dcraw**](http://www.cybercom.net/~dcoffin/dcraw/) for raw support.

You'll find it in synaptic.

There's also a Gimp plug in for it, so you can import RAW directly into Gimp.

There's also **ufraw** but I haven't tried that. (I haven't tried the gimp plugin for dcraw either)

---

### Post by pestilence4hr on 2006-02-26
Ah, ok.  Just wondering :)

To find out how to launch it, you could do "dpkg -L <packagename>"  where <packagename> is probably "bibble".  This will show you what files were installed by that package.  The executables are probably in /usr/bin

---

### Post by htoerrin on 2006-02-27
Bibble installs the executable under /usr/bin, and the rest of the files under /usr/lib/bibblelabs. The Light version is called bibblelite, so the Pro version might be called bibblepro. Try typing bibblepro from a terminal window.

And for the open source alternatives: I have tried all mentioned, but unfortunately none of them are usable for serious work.

---

### Post by borderline on 2006-03-22
I'm using [exiftool]("http://www.sno.phy.queensu.ca/~phil/exiftool/"), from package libimage-exiftool-perl (it's in dapper, I used source packages to install it in breezy)  to write IPTC-tags to images. It supports wide range of different metadataformats and wide range of different picture formats. Bad news is, it's commandline application. Besides it I use ufraw-plugin for gimp ( [http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/) ), gimp, gthumb and gtkam. I would welcome better integration for these programs for better workflow and usability. Now things kind of suck :)

---

