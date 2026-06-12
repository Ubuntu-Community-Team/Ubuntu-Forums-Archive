---
title: "Windows-1252 file names within UTF-8 Ubuntu 5.10 Breezy with Gnome"
date: 2006-03-03
forum: Desktop Environments
---

### Post by adamkane on 2006-03-03
*****
Go here for new HOWTO: [http://www.ubuntuforums.org/showthread.php?t=144297]("http://www.ubuntuforums.org/showthread.php?t=144297")
*****

Like many first-time users, I installed **Breezy with UTF-8** file name encoding. I then added a second hard drive to store my media files and documents. I then formatted the second disc as ext3 and mounted it. And finally I transferred some files over my network from a Windows machine to the newly formatted hard disc. 

I have many files with **special characters** in the file name (ä,á,à,å,æ,ç,ñ,ß,&#8364;), and it wasn't until I was done moving the files, that I realized I had lost all my file name encodings. For example: 

björk.ogg -> bj?rk.ogg **(invalid encoding)**

I realized later that to avoid losing my encodings, **I should have used Windows to transfer files** over the network to the new ext3 disc or I should have mounted the share using the nls=utf8 flag.
[http://wiki.vidalinux.com/index.php/How_to_Mount_Windows_Partitions]("http://wiki.vidalinux.com/index.php/How_to_Mount_Windows_Partitions")

*** Or I could have browsed the Windows share * See thread 5 ***

I found some promising Ubuntu/Debian packages for **viewing non-UTF-8** encoded file names within a UTF-8 encoded file system. However these packages are bleeding edge and do not yet work within Breezy. 

*** Use ROX-Filer * See Thread 5 ***

**cxplorer**
[http://cxplorer.sourceforge.jp/]("http://cxplorer.sourceforge.jp/")

**pcmanfm**
[http://pcmanfm.sourceforge.net/]("http://pcmanfm.sourceforge.net/")

**KDE** users already have a solution:

**changeFilenameCode**
[http://kubuntu.free.fr/servicemenu/]("http://kubuntu.free.fr/servicemenu/")

**ToUTF-8**
[http://www.kde-apps.org/index.php?xcontentmode=287]("http://www.kde-apps.org/index.php?xcontentmode=287")

**Big list of KDE service menus**:
[http://www.kde-apps.org/index.php?xcontentmode=287]("http://www.kde-apps.org/index.php?xcontentmode=287")

Since these packages are not available to **Ubuntu Gnome users, use the convmv command** to convert the invalid encoded file names:

```

sudo apt-get install convmv
cd /<path to>
convmv -f windows-1252 -t utf-8 -r --notest *.*

``` 
*** Incorrect -f switch * See thread 4 ***

Switches:
-f windows-1252 *Initial encoding*
-t utf-8 *Final encoding*
-r *Convert subfolders*
--notest *Commit the conversion, this is not a test!*

Details:
[http://www.suse.de/~mfabian/suse-cjk/encodings-file-names.html/]("http://www.suse.de/%7Emfabian/suse-cjk/encodings-file-names.html")
[http://man-wiki.net/index.php/1:convmv/]("http://man-wiki.net/index.php/1:convmv")

I found the following **Nautilus script** in a Taiwan Debian forum. I modified the script slightly to handle Windows-1252 encoded files, and to handle multiple files. Edit the -f and -t switches to suit your particular encodings.
[http://moto.debian.org.tw/viewtopic.php?t=5367/]("http://moto.debian.org.tw/viewtopic.php?t=5367")

```

#!/bin/bash
#Convert Windows-1252 to UTF-8

if [ $# -gt 0 ];then[INDENT]convmv -f windows-1252 -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close[/INDENT]fi
exit 0

``` 
*** Incorrect -f switch * SEE THREAD 4 ***

To install the Nautilus script, **save the script as a text file** in[INDENT]/home/<username>/.gnome2/nautilus-scripts/[/INDENT]and **mark the file as executable.**

```

sudo chmod 700 /home/<username>/.gnome2/nautilus-scripts/*.*

``` 
Find more information about using Nautilus scripts here:
[http://g-scripts.sourceforge.net/faq.php]("http://g-scripts.sourceforge.net/faq.php")

Until **File Roller** (or some other archive manager) acquires support for alternate encodings, any **ISO-8859-1** or **Windows-1252 encoded files** will be extracted with their original encoding. **Execute the convmv command** or the Nautilus script on the extracted files to convert the file names to UTF-8.

Note:
Sometimes convmv will "convert" a file name that is already UTF-8. If this happens, then you can convert the file back by switching the -f and -t switches. 

Note:
UTF-8 is a UNICODE encoding. Windows-1252 and ISO8859-1 are Latin encodings.

---

### Post by akiro.yamamoto on 2006-03-03
Good ti, nice job ;)

---

### Post by adamkane on 2006-03-03
I investigated **cxplorer** a bit more and was able to install it on my system. It is a file manager to display **Japanese encoded files** in UTF-8. It uses **nkf**, a kanji code filter.
[http://www.die.net/doc/linux/man/man1/nkf.1.html](http://www.die.net/doc/linux/man/man1/nkf.1.html)  

I found some info about how to use filters in cxplorer, but it is in japanese. cxplorer ran slowly, so install only if you have need for the package.
[http://cxplorer.seesaa.net/article/7884118.html](http://cxplorer.seesaa.net/article/7884118.html)

> 
&#12288;&#20170;&#22238;&#12289;&#35373;&#23450;&#12480;&#12452;&#12450;&#12525;&#12464;&#12395;&#12302;&#12501;&#12449;&#12452;&#12523;&#21517;&#12398;&#34920;&#31034;&#12395;&#22806;&#37096;&#12501;&#12451;&#12523;&#12479;&#12434;&#21033;&#29992;&#12377;&#12427;&#12303;&#35373;&#23450;&#12364;&#12391;&#12365;
&#12427;&#12424;&#12358;&#12395;&#12452;&#12531;&#12479;&#12540;&#12501;&#12455;&#12540;&#12473;&#12434;&#36861;&#21152;&#12375;&#12414;&#12375;&#12383;&#12290;&#20197;&#21069;&#12363;&#12425;&#12289;&#12354;&#12387;&#12383;&#27231;&#33021;&#12391;&#12377;&#12364;&#35373;&#23450;&#12452;&#12531;&#12479;&#12540;
&#12501;&#12455;&#12540;&#12473;&#12434;&#29992;&#24847;&#12377;&#12427;&#12398;&#12434;&#24536;&#12428;&#12390;&#12356;&#12383;&#12398;&#12391;&#12290;

[&#20351;&#29992;&#20363;]
1 /path/filter.sh&#12434;&#28310;&#20633;

#!/bin/sh

echo "$1" | nkf --euc

2 cxplorer&#12391;[&#32232;&#38598;]-[&#35373;&#23450;]&#12434;&#38283;&#12365;[&#22806;&#37096;&#12501;&#12451;&#12523;&#12479;]&#12479;&#12502;&#12391;&#20197;&#19979;&#12398;&#12467;&#12510;&#12531;&#12489;&#12434;&#20837;&#21147;&#12375;&#12390;
[OK]

sh /path/filter.sh

# &#12509;&#12452;&#12531;&#12488;&#12399;&#12289;&#20986;&#21147;&#12434;locale&#12395;&#21512;&#12431;&#12379;&#12427;&#12371;&#12392;&#12391;&#12377;&#12290;

More info on cxplorer:
[http://cxplorer.seesaa.net/](http://cxplorer.seesaa.net/)

---

### Post by adamkane on 2006-03-05
After some investigation and trial and error, I understand now that there are two conversions necessary after transferring files from a Windows share to a UTF-8 encoded ext3 file system. You need to convert your file names from **CP850 to UTF-8**, and then convert any **archives of ISO-8859-1 encoded files** to convert to UTF-8 as required. **These are two different operations**.

I should also note that I misunderstood the difference between Windows-1252, CP1232, CP850, and ISO-8859-1. According to the documentation, the files on my Windows machines had Windows-1252 or CP1252 encoded file names, but they seemed to be CP850 encoded, which is an MSDOS encoding. Note that Windows-1252 (i.e. CP1252) is essentially the same as ISO-8859-1 for the purpose of converting file names, although they handle a few special characters differently.
[http://j3e.de/linux/convmv/man/]("http://j3e.de/linux/convmv/man/")
[http://ppewww.ph.gla.ac.uk/~flavell/iso8859/iso8859-pointers.html]("http://ppewww.ph.gla.ac.uk/%7Eflavell/iso8859/iso8859-pointers.html")
[http://en.wikipedia.org/wiki/Windows-1252]("http://en.wikipedia.org/wiki/Windows-1252")

Also there is a bug in perl, which affects **convmv 1.08**. The author of convmv says that you need to use the **--nosmart** switch to convert to UTF-8, or the conversion won't happen at all. If you use the --nosmart switch however, you risk re-converting filenames that are already UTF-8 encoded, and you will have to reverse the operation on the affected files. I was able to convert all my files without the --nosmart switch, but I had to undo the operation a few times, when I inadvertantly converted a directory of files with mixed encodings.

> 
ATTENTION: Perl 5.8.7 seems to have a broken decode_utf8() function so that convmv can not convert files to UTF-8 without using the --nosmart switch! convmv 1.09 works around this.
 
[http://j3e.de/linux/convmv/]("http://j3e.de/linux/convmv/")
[http://arainyday.se/notebook/convmv.php]("http://arainyday.se/notebook/convmv.php")

There are two scenarios to understand when transferring files from a Windows share to ext3. You may have files with special characters in the file name, or you may have an archive of files with special characters in the archived file names.

[SIZE=1]* There is a third case, where you have to convert the file name of an archive, and also convert the file names of the archived files.[/SIZE]

If you are converting files that have been transferred from a **Windows share to a UTF-8 ext3** file system, then

```

cd /<path to>
convmv -f **cp850** -t utf-8 -r --notest *.*

``` 
If you are converting files that have been **extracted from an archive**, then

```

cd /<path to>
convmv -f **iso-8859-1** -t utf-8 -r --notest *.*

``` 
Nautilus scripts:

```

#!/bin/bash
#Convert CP850 to UTF-8

if [ $# -gt 0 ];then

    convmv -f **cp850** -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi
exit 0

``` 
```

#!/bin/bash
#Convert ISO-8859-1 to UTF-8

if [ $# -gt 0 ];then

    convmv -f **iso-8859-1** -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi
exit 0

``` 
As I noted before, be prepared to undo some of your conversions, as you may accidentally "convert" some file names that did not need it. Also as I noted, file name conversion will be invisible, when File Roller and Nautilus acquire support for alternate encodings.

The KDE solutions, **changeFilenameCode and ToUTF-8**, only apply to ISO-8859-1 encoded files. If you have files that were transferred from a CP850 file system, create additional entries in the .desktop and .sh files for CP850 to UTF-8 conversion, or use convmv to convert your files.
[http://kubuntu.free.fr/servicemenu/]("http://kubuntu.free.fr/servicemenu/")
[http://www.kde-apps.org/index.php?xcontentmode=287]("http://www.kde-apps.org/index.php?xcontentmode=287")

See more about Unicode text conversion from the **command line**:
[http://www.linux.com/howtos/Unicode-HOWTO-3.shtml]("http://www.linux.com/howtos/Unicode-HOWTO-3.shtml")

or about text conversion with KDE service menus:
[http://www.kde-apps.org/index.php?xcontentmode=287]("http://www.kde-apps.org/index.php?xcontentmode=287")

(Useful information to create **new Nautilus scripts**.) ;)

If you are committed to maintaining your file system with ISO-8859-1 encoding, you still need to convert your file names from CP850 to ISO-8859-1, when transferring files from a Windows share to an ext3 file system.

*** Also use ROX-Filer to view your ISO-8859-1 files * See Thread 5 ***

---

### Post by adamkane on 2006-03-07
After more investigation, I learned that my encodings would have been saved, if I had browsed my Windows share, rather than mounted it. Network browsing preserves encodings, and no special configuration is required:

If you've managed to transfer all your files without losing your encodings, or if you've successfully converted all your files from CP850 to UTF-8, you will likely have some archives that contain ISO-8859-1 file names that need to be converted. There is a file manager, ROX-Filer, that will display file names with ISO-8859-1 encoding in red, and will allow you to rename these files with UTF-8 encoding. ROX-Filer misinterprets CP850 encoded file names however, so it won't be able to handle your initial conversion from Windows-1252 NTFS to UTF-8 ext3.  ROX-Filer is already the default file manager for XFCE users.

ROX-Filer
[http://rox.sourceforge.net]("http://rox.sourceforge.net/")

```

sudo apt-get install rox-filer

``` 
If you install ROX-Filer in Gnome, you may need to create a Panel launcher.

Panel -> Right click -> Add to Panel... -> Custom Application Launcher -> Add -> 

Name: ROX-Filer
Command: rox-filer
Icon: /usr/share/icons/hicolor/48x48/apps/file-manager.png

Here is information to make ROX-Filer the default file manager in Gnome:
[http://ubuntuforums.org/showthread.php?t=48169]("http://ubuntuforums.org/showthread.php?t=48169")

More info about ROX-Filer (and UTF-8 advocacy): 
_[http://rox.sourceforge.net/desktop/Internationalisation]("http://rox.sourceforge.net/desktop/Internationalisation")_

> 
Why does ROX-Filer complain that my filenames aren't UTF-8?

In the past, filenames have been stored using the local character set. This means that you can't send a file to someone in a different locale or have two files from different character sets on your system at once.

Therefore, there is a general move over to the UTF-8 encoding (which can represent all characters in a single encoding). Many applications (not just ROX ones) now assume that your filenames are UTF-8 and will complain if not. ROX-Filer displays names not in UTF-8 in red.

You can specify a fall-back encoding by setting the CHARSET environment variable. Use something like this to test it (-n forces a new copy of the filer to start):

CHARSET=iso-8859-2 rox -n

A better solution for the future is to convert your filenames to UTF-8 (use the filer's Rename box to convert individual files, or the iconv utility for mass conversion). You can use UTF-8 names from the shell by setting LANG, for example:

LANG=en_GB.UTF-8 xterm

For more information, see the httpUTF-8 and Unicode FAQ for Unix/Linux.
[http://www.cl.cam.ac.uk/~mgk25/unicode.html]("http://www.cl.cam.ac.uk/%7Emgk25/unicode.html")

Why doesn't ROX-Filer provide the option to use my local encoding?

ROX-Filer only supports non-UTF-8 encodings enough to let you rename your files to UTF-8. Although we often get requests to add more support, this is not a useful direction. There are a huge number of places where support must be added, and even if you got the whole filer converted, you'd need to convert all your other applications too.

And, at the end of all this work converting everything to support your legacy encoding, you're just back to the bad old pre-UTF-8 days, where you can't exchange files with users in a different locale, can't have files with different alphabets on the same system, and you have to keep track of the encodings whereever you go, or the names become unreadable. So, just convert to UTF-8. It's easier in the long run!
 

List of possible encodings to use with convmv:

> 
7bit-jis AdobeStandardEncoding AdobeSymbol AdobeZdingbat ascii ascii-ctrl big5-eten big5-hkscs cp1006 cp1026 cp1047 cp1250 cp1251 cp1252 cp1253 cp1254 cp1255 cp1256 cp1257 cp1258 cp37 cp424 cp437 cp500 cp737 cp775 cp850 cp852 cp855 cp856 cp857 cp860 cp861 cp862 cp863 cp864 cp865 cp866 cp869 cp874 cp875 cp932 cp936 cp949 cp950 dingbats euc-cn euc-jp euc-kr gb12345-raw gb2312-raw gsm0338 hp-roman8 hz iso-2022-jp iso-2022-jp-1 iso-2022-kr iso-8859-1 iso-8859-10 iso-8859-11 iso-8859-13 iso-8859-14 iso-8859-15 iso-8859-16 iso-8859-2 iso-8859-3 iso-8859-4 iso-8859-5 iso-8859-6 iso-8859-7 iso-8859-8 iso-8859-9 iso-ir-165 jis0201-raw jis0208-raw jis0212-raw johab koi8-f koi8-r koi8-u ksc5601-raw MacArabic MacCentralEurRoman MacChineseSimp MacChineseTrad MacCroatian MacCyrillic MacDingbats MacFarsi MacGreek MacHebrew MacIcelandic MacJapanese MacKorean MacRoman MacRomanian MacRumanian MacSami MacSymbol MacThai MacTurkish MacUkrainian MIME-B MIME-Header MIME-Q nextstep null posix-bc shiftjis symbol UCS-2BE UCS-2LE UTF-16 UTF-16BE UTF-16LE UTF-32 UTF-32BE UTF-32LE UTF-7 utf-8-strict utf8 viscii
 

Tip:
Gnome users can take advantage of the Big List of KDE service menus by using Konqueror. The KDE .desktop service menu files are invisible within Gnome, so you may have to log into KDE to install the service menus.

Save the .desktop files here for the current user:

~/.kde/share/apps/konqueror/servicemenus/ 
 
or save them here for all users:
 
/usr/share/apps/konqueror/servicemenus/ 

How to internationalize your desktop:
[http://www.gentoo.org/doc/en/utf-8.xml]("http://www.gentoo.org/doc/en/utf-8.xml")
[http://gentoo-wiki.com/Index:HOWTO]("http://gentoo-wiki.com/Talk:HOWTO_Make_your_system_use_unicode/utf-8")
[http://www.suse.de/~mfabian/suse-cjk/unicode-switch.html](http://www.suse.de/~mfabian/suse-cjk/unicode-switch.html)
[ ]("http://gentoo-wiki.com/Talk:HOWTO_Make_your_system_use_unicode/utf-8")

---

