---
title: "GNOME Files Compress Formats - Any way to add tar.gz"
date: 2020-10-07
forum: Desktop Environments
---

### Post by rmemm on 2020-10-07
In 18.04, GNOME Files (aka Nautilus) no longer opens File Roller for compression.  Instead I get a dialog with tar.xz, zip. and 7z archive formats.  Is there a way to change some install or configuration options to add tar.gz file format?  Or for that matter tar.bz2 format and other formats?  Or to reconfigure it to go back to using File Roller like it did previously?

I realize I can open File Roller manually still, or open the command line to archive in other formats like tar.gz or tar.bz2.  I just like the convenience of the context menu click that has been that for a long time.  

Thanks,
rmemm

---

### Post by ajgreeny on 2020-10-07
Are you saying that double clicking on an archive file, eg .zip, tar.gz, etc does not open it in file-roller or any other archive manager, or right clicking on any file or folder and choosing "Create archive" does not open file-roller?

On Xubuntu, which I use, the former action opens engrampa, another archive manager, but if I right click to create an archive all I see is a dialogue with similar options to those you mention, and that has always been the way Xubuntu does it so far as I can remember, so is exactly what I want and expect to see.

I have hardly ever used Gnome in 18.04 or the newer GUI version in 20.04, in fact not since gnome 2, so I do not know how Gnome now normally does this.

---

### Post by rmemm on 2020-10-07
I'm saying the 2nd... by that I mean... context (right) mouse click on item brings up a menu, and you select compress...  That brings up a dialog with 3 options.  I read somewhere that there was a change at some point and now this is integrated into Gnome Files, but beyond that I don't know.  On Ubuntu 16.04 under Unity, if you did the same thing you'd get a different dialog box with a popup menu where you could select the file format you wanted and I image this was basically from file roller or intended to mimic it.  I liked the 16.04 dialog a lot better because it defaulted to tar.gz, and had a ton of other options including 7z with encryption capability which I also used sometimes.  The new dialog lacks that too.  Seems like a big step back.

As far as double clicking on a tar.gz archive, that is fine it opens something that looks a lot like file roller.  Same for context (right click) then select Extract Here... the tar.gz will extact as expected.  So it's only on the compress... side of things.  Terribly limited dialog... only 3 formats, no advanced options like encryption.  Just not great.

I suppose some of this is due to some people fixated on moving to tar.xz formats... but I'm not one of them. Also, there seems to be the tendency to dumb things down to the point they are unusable.  Ironically of the past 15 years or so I've found myself using the command line more and  more as GUI interfaces have been removed for things that actually matter.

---

### Post by ajgreeny on 2020-10-08
OK.  Thanks for the clarification.  I don't think I've ever seen or needed a full GUI for application creation of a new archive, though to add files to an existing archive I would always open whatever the default archive-manager is, eg file-roller, or in my case engrampa.

However, I suspect you are missing a package needed to encode some types of archive, hence the missing options in your dialogue; the one I think you may be missing is p7zip-full and one or other of the gzip or bzip packages, but it's difficult to know with any certainty as we don't know what you already have installed.

I use p7zip-full for a simple encryption of files that I don't want family members to read by adding a password requirement to read them.  It's not high encryption but enough for simple control in the family.

---

### Post by rmemm on 2020-10-08
Thanks.

Yes... I have p7zip and p7zip-full installed.  I also have gzip installed.  File Roller has the formats and options and encrypts fine.  

I think it's just a new "feature"...

---

### Post by SeijiSensei on 2020-10-08
Kubuntu 20.04 still offers .tar.gz if you right-click an object in the file manager Dolphin and pick Compress.  You can also choose from a complete list of compression formats like tar.xz.

---

### Post by ajgreeny on 2020-10-08
Here's a screenshot of all the archive options I see when creating an archive from files in my Xubuntu 20.04; it seems to include the ones you're missing, so I still suspect you are missing a package used for archive encoding or creation, so maybe we just need to figure out what that is.

---

### Post by norobro on 2020-10-08
Here's a link to the dev's justification for the change: [https://razvanchitu.wordpress.com/2016/08/09/internal-compression/](https://razvanchitu.wordpress.com/2016/08/09/internal-compression/)

I use "pcmanfm" in 20.04 and it offers a plethora of format options. It uses "Engrampa". [https://launchpad.net/ubuntu/bionic/+package/pcmanfm](https://launchpad.net/ubuntu/bionic/+package/pcmanfm)

---

### Post by Frogs Hair on 2020-10-08
I too have a wide range of options with Nemo.

---

### Post by rmemm on 2020-10-08
Thanks... that must be it.

---

### Post by ajgreeny on 2020-10-09
> **rmemm said:**
> Thanks... that must be it.
I have to admit that one reason I do not like gnome is the constant removal of options and the ability to configure things as I would like them; looks like you've come across another of those things I dislike.

---

