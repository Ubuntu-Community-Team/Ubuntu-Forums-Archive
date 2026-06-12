---
title: "GUI front end for 7-zip resurrected"
date: 2016-05-20
forum: Desktop Environments
---

### Post by Antony_F_Heaton on 2016-05-20
I found [this closed thread]("http://ubuntuforums.org/showthread.php?t=782897") from 2008: it had no answer, despite the desirability of a 7-Zip GUI. After trying various approaches, I found that the Windows version works well under Wine. In addition to providing a GUI version, it also handles file types that the Ubuntu command-line version does not recognise, such as virtual discs (***.vmdk**).

I used the [Portable Apps]("http://portableapps.com/") version (many of the Portable Apps run under Wine, including the GUI). The only draw-back is that files need to be opened in the Wine environment, but I made this more or less transparent by creating a short-cut **~/.local/share/applications/7-Zip.desktop** using the Command line **Exec=wine c:\\\\PA\\\\PortableApps\\\\7-ZipPortable\\\\7-ZipPortable.exe Z:%f** (assuming that **Z:** addresses the root file system in Wine). This allowed me to add the 7-Zip GUI to the **Open With** list for the files I want it to open.

As the final icing on the cake, I used Portable IcoFX (also under Wine) to extract an icon from the Windows executable to use in the launcher.

I am running Wine 1.6.2 under Ubuntu 15.04.

---

### Post by QDR06VV9 on 2016-05-20
If you are really using Ubuntu 15.04 I would urge to upgrade to a supported release as 15.04 has ended support February 4, 2016
See this [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ajgreeny on 2016-05-20
Do we really need a separate GUI just for 7-zip?

All of the various compression types seem to be supported by file-roller, the default archive-manager in Ubuntu (and some of the other *ubuntu family OSs), or by the right click in file-managers.

---

### Post by Frogs Hair on 2016-05-20
The 7-zip file manager GUI is only included in the Windows version AFIK. I use it to handle RAR archives.

---

### Post by Antony_F_Heaton on 2016-06-10
I shall move to 16.04 when it's stable. Initial reviews indicate that it's not there yet. Meanwhile, I am still getting regular security updates.

None of the standard Ubuntu compression utilities (whether GUI or command-line) support some of the file types that the Windows 7-Zip handles, and that includes the command-line version of 7-Zip itself. If there is another general archiver which handles (for example) ***.vmdk** files, I would be pleased to hear about it.

---

### Post by X-RED_Tech on 2016-06-10
7-Zip isn't installed by default but once installed it handles all the file types 7-Zip for Windows and "integrates" with the same file-roller GUI evrything else uses, as commented before.

---

### Post by Antony_F_Heaton on 2016-06-20
> **X-RED_Tech said:**
> 7-Zip isn't installed by default but once installed it handles all the file types 7-Zip for Windows and "integrates" with the same file-roller GUI everything else uses, as commented before.

Not true: there are several file types supported by 7-Zip for Windows which are not recognised as an archive in Linux, which is why I contributed this thread. I have already cited VM discs (***.vmdk**): they do not appear in archive manager as a supported archive type and will not open if you select it using all files in the open dialogue; nor do they open open with **7z l** on the command line, but are handled fine with **wine 7-Zip.exe**. I can't off-hand remember the other file types - they may have been Windows-specific archives, but I'll post examples when I next encounter them.

---

### Post by yoshii on 2016-06-21
Yeah, I think another format is the MacOS .dmg (disk data image), which 7-zip Windows can open.  
There is a nice Linux portable version of PeaZip though.  And it has some 7-zip support also.  
And Windows freeware BandiZip also works well in Wine.  

Personally, I like using the Linux file-roller or whatever it's called in XFCE integrated with the p7zip synaptic packages.  But I do miss the configuration options in the Windows version.  But since Windows tends to not be as case-sensitive as Linux, I don't normally use Windows programs for archive management.  BandiZip has some nicer UTF-8 support for Linux data, but I hardly ever use it.

---

### Post by altosch on 2016-07-03
p7zip GUI for Linux: [https://www.ruinelli.ch/p7zip-gui-for-linux](https://www.ruinelli.ch/p7zip-gui-for-linux)

---

### Post by Antony_F_Heaton on 2016-08-09
> **altosch said:**
> p7zip GUI for Linux: [https://www.ruinelli.ch/p7zip-gui-for-linux](https://www.ruinelli.ch/p7zip-gui-for-linux)

Thanks for the link. I have now upgraded to 16.04 Mate and the GUI works well (apart from the lack of a context menu for the archive files). Since the upgrade I now find that **7z**  opens virtual discs, as does the GUI of course, so we now have a native  solution. Since I don't use Dolphin much, I don't get the file manager  integration, but adding the GUI to the **Open with** list is fine for my purposes. The default archive manager (**Engrampa** in Mate) will not open the archive, nor will it open RAR archives. The **7-Zip** GUI handles both, despite the fact that the standard **p7zip-rar** can't be installed because of incompatible libraries, and [your link]("https://www.ruinelli.ch/p7zip-gui-for-linux") does not have a compatible update for it. One of life's little mysteries...

Thanks again.

---

