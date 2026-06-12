---
title: "MP4 to AMV Converter"
date: 2006-07-28
forum: Desktop Environments
---

### Post by mosestruong on 2006-07-28
Just wondering if there is a tool that will convert MP4 to AMV format?

---

### Post by cosine7 on 2006-08-02
> **mosestruong said:**
> Just wondering if there is a tool that will convert MP4 to AMV format?

*Bump*
I'll second that.....

---

### Post by Fra_221187 on 2006-08-08
someone had founded a avi or mpeg to amv converter?




(excuse me for my english, i'm italian an this is my first post in this forum :D)

---

### Post by Fra_221187 on 2006-08-10
up :(

---

### Post by cosine7 on 2006-08-11
Sorry Fra, i have had no luck, i found a w32 one but it will not work under WINE....

so *BUMP*

---

### Post by Fra_221187 on 2006-08-12
So i can't use my mp4 player without windows??? :S

---

### Post by cosine7 on 2006-08-12
There doesn't seem to be much out there at all, even for windows. It took me ages just to get a w32 program(don't even know if it works, don't have win), any this [http://forum.doom9.org/showthread.php?t=112738](http://forum.doom9.org/showthread.php?t=112738) might clear some things up.

---

### Post by cosine7 on 2006-08-12
[http://www.mympxplayer.com](http://www.mympxplayer.com) apprently has a player, not sure if it will work under WINE, but the site is done, but heaps of links to it...

---

### Post by marcelomanzo on 2006-11-20
How to encode on Unix or Linux

This has been tested in Wine (0.9.7 and later), but you need to install Windows Media Player 9 (not 10) first.

Follow these steps:

    * You will first need msxml.dll, quartz.dll and qedit.dll (google for the files and copy to ~/.wine/drive_c/windows/system32) and run regsvr32 msxml.dll && regsvr32 qedit.dll. If msxml.dll fails to register, you need a different version (the one that depends on msxmlr.dll can't be used).
    * Run winecfg and add a native DLL override for qedit.
    * (Probably not necessary for Wine 0.9.7 and later) Run winecfg and add native DLL overrides for msiexec.exe and msi (exactly as spelled).
    * (Probably not necessary for Wine 0.9.7 and later) Install Windows Installer by running the InstMsiA.exe that comes with the MP3 Player Utilities, after setting Windows version in winecfg to Win98.
    * Download and install WMP 9 (MPSetup.exe). Don't worry if it doesn't start.
    * Install the MP3 Player Utilities by running the setup.exe or similar installer.
    * Install other codecs for XviD/DivX etc (e.g. ffdshow) so you can convert AVI files. 

Things to note about using AMV tools:

    * The Settings window (to change encoding settings) doesn't display unless you press the Alt key (or possibly Alt-Tab) TWICE. Very weird.
    * The AMV convert tool uses CPU time when displaying progress so minimise the window when converting so it doesn't get slowed down.
    * You might not be able to change the output folder. The default is "C:\" (i.e., ~/.wine/drive_c). 

(original on the forums by trisk) 

I'Ve Got from: [http://wiki.s1mp3.org//index.php/Video_encoding](http://wiki.s1mp3.org//index.php/Video_encoding)

---

### Post by pahbloo.marks on 2007-10-06
The site [www.media-convert.com](www.media-convert.com) promises on-line converting from/to a lot of formats of video, audio, presentation, document, spreadsheet, etc. One of options is to convert a video file to .amv format.

I had no luck in my tests, but you can try...

Good luck!

(Excuse my English. I'm Brazilian and I'm learning English by myself. Plese, correct any grammar mistake.)

---

### Post by patslap on 2007-12-27
for files over 150mb in size try [http://www.bytessence.com/bamvc.html](http://www.bytessence.com/bamvc.html)

---

### Post by d1prince1 on 2008-01-12
Has anyone tried this yet?

---

### Post by topgun on 2008-01-13
Hello everyone :)
So on ubuntu-in the solution has been found, It is necessary to use ffmpeg, recovering sources SVN :
svn checkout [http://amv-codec-tools.googlecode.com/svn/trunk/](http://amv-codec-tools.googlecode.com/svn/trunk/) amv-codec-tools
cd amv-codec-tools/AMVmuxer
make build
./ffmpeg/ffmpeg -i monfichier.avi -f amv -r 16 -s 160x120 -ac 1 -ar 22050 -y monfichier.amv
This is a file. avi in this example, but if the conversion mp4> amv does not work directly, it is sufficient to convert the first mp4 in avi then in amv
I applied and I must say that I am pleased with the outcome :)
The move if a moderator could move in Multimedia & Video it would be more appropriate ;)

---

### Post by sulfo on 2008-06-13
hey guys!
got something:
[http://code.google.com/p/amv-codec-tools/wiki/HowToConvertToAMV](http://code.google.com/p/amv-codec-tools/wiki/HowToConvertToAMV)

works fine ;)

---

