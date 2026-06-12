---
title: "Comic Book Viewer"
date: 2010-05-30
forum: Gaming &amp; Leisure
---

### Post by Oolongtea on 2010-05-30
[SIZE=2]There are several comic book viewers on Linux for cbr, cbz, RAR, and ZIP files. The most popular of these would be Comix. This is the one I tend to use. There are others that you may find better to your liking. I've compiled a list of digital comic book viewers below. 

Here is a list of comic book viewers on Linux:[/SIZE]
[SIZE=3][SIZE=2][Comix]("http://comix.sourceforge.net/")
[Comical]("http://comical.sourceforge.net/")
[RadicalCodex]("http://www.radicalbreeze.com/radicalcodex.shtml")
[QComicBook]("http://qcomicbook.linux-projects.net/")
[CbrPager]("http://www.jcoppens.com/soft/cbrpager/index.en.php")
[SIZE=2]
(This is all I could find. If you know of any others please tell me so I may add them to the list. Thanks)


[/SIZE]
[/SIZE][/SIZE]

---

### Post by Ranko Kohime on 2010-05-30
Do any of the programs you've listed download and archive Webcomics, the ones that are completely published online, or do these just get the online versions of ones that are in print, or do they just handle the archive which still has to be built manually?

---

### Post by Oolongtea on 2010-05-31
I believe the latest Comix can create cbr and cbz files. You can easily create you own by renaming a Zip file cbz and a RAR cbr. It is really simple.  You will have to manually download the comics. These programs usually only allow you to view the file. Sometimes they have more add ons.

---

### Post by del_diablo on 2010-05-31
Well, Comix works for me... for reading my mothly dose of good manga scanlations.

---

### Post by disturbedite on 2010-05-31
i can't beleive no one mentioned QComicBook. one of the main reasons i use it because it is the only viewer i can find that supports 7z, which i have converted my collections over to.

EDIT:
i see cbrpager supports 7z but i use KDE so QComicBook is preferable any way.

---

### Post by Oolongtea on 2010-05-31
I had qcomicbook up but the link was broken so I removed it. I'll see if I can add it :)

---

### Post by Oolongtea on 2010-05-31
There all done. QComicBook was added :)

---

### Post by disturbedite on 2010-06-01
> **Oolongtea said:**
> There all done. QComicBook was added :)

i think you might want to link to actual home page:
[http://qcomicbook.linux-projects.net/](http://qcomicbook.linux-projects.net/)

---

### Post by Oolongtea on 2010-06-01
Fixed.

---

### Post by ProlixTST on 2010-07-05
[I]I'm extremely new to Ubuntu specifically and Linux in general so I've no clue on how to properly install the "tarball" after downloading. 

I went to the "comical" homepage and downloaded the "source" for it but what do I do next?

I know it has something to do with using the terminal and typing in an install command but I don't know what to type.  

Thanks in advanced.
[/I]

---

### Post by AleksKeaton on 2010-07-05
What about PDF? Even Kindle can read PDF, if I'm not mistaken.

---

### Post by Oolongtea on 2010-07-06
Well kindle is an [SIZE="5"]**_EBOOK_**[/SIZE] reader. These programs deal with reading cbz, cbr, RAR, and Zip files on your [SIZE="5"]**_COMPUTER_**[/SIZE].

---

### Post by ProlixTST on 2010-07-09
How do I install the comic book reader? I tried to google instructions but everything I found just beats around the bush and doesn't come out and say what it is.

Step by step with commands if possible. 

Thanks in advance.

---

### Post by KIAaze on 2010-07-09
The following may also be of interest to those reading long webcomics:
[https://launchpad.net/comicget](https://launchpad.net/comicget)
[http://wnd.katei.fi/comic-get/](http://wnd.katei.fi/comic-get/)


> **ProlixTST said:**
> How do I install the comic book reader? I tried to google instructions but everything I found just beats around the bush and doesn't come out and say what it is.

Step by step with commands if possible. 

Thanks in advance.

For comix:
```
sudo apt-get install comix
```
To run it:
```
comix
```
(or look for the new shortcut somewhere in the applications menu)

For the others, I don't know, but it's possible they are in the repositories too. Otherwise find their official site and look for info there.

What it is:
A "comic book reader" is similar to an image viewer (the app that opens when you double-click on an image), except that it's specialized for reading comics/mangas (BD, graphic novel, webcomics, books...), i.e. folders or archives full of images corresponding to the pages/volumes of a comic/manga.
i.e. it has functions like bookmarks, reading images from archives (.rar,.zip,.cbr,.tgz,etc), zoom in/out, two pages per view (with left-to-right or right-to-left reading), library, easy image navigation, etc

P.S.: If you still have problems installing:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by ProlixTST on 2010-07-09
> **KIAaze said:**
> The following may also be of interest to those reading long webcomics:
[https://launchpad.net/comicget](https://launchpad.net/comicget)
[http://wnd.katei.fi/comic-get/](http://wnd.katei.fi/comic-get/)




For comix:
```
sudo apt-get install comix
```To run it:
```
comix
```(or look for the new shortcut somewhere in the applications menu)

For the others, I don't know, but it's possible they are in the repositories too. Otherwise find their official site and look for info there.

What it is:
A "comic book reader" is similar to an image viewer (the app that opens when you double-click on an image), except that it's specialized for reading comics/mangas (BD, graphic novel, webcomics, books...), i.e. folders or archives full of images corresponding to the pages/volumes of a comic/manga.
i.e. it has functions like bookmarks, reading images from archives (.rar,.zip,.cbr,.tgz,etc), zoom in/out, two pages per view (with left-to-right or right-to-left reading), library, easy image navigation, etc

P.S.: If you still have problems installing:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)


Thanks a lot for that. A million times more simple than I had anticipated.  

But I've run into another snag, when I try to open a .cbr file in 'comix' it says:  

COULD NOT FIND THE .RAR FILE EXTRACTOR

The cold part about this is that it isn't zipped.  I put the exact same files on my flash drive and opened them on a windows system using a different comic viewer and it didn't unzip anything. It just went right to the comic.  Can someone point me in the right direction? 

Thanks in advance.

---

### Post by KIAaze on 2010-07-09
This should fix it:
```
sudo apt-get install unrar
```

_Technical info for your information:_
This is not a problem of the package management system. It seems to have been a choice made by the packagers.

"comix" has not been made dependent on "unrar". "unrar" is just a suggested package as you can see here:
[http://packages.ubuntu.com/lucid/comix](http://packages.ubuntu.com/lucid/comix)

This was most likely done because unrar is non-free ([non-libre]("http://en.wikipedia.org/wiki/Gratis_versus_Libre")), thus allowing comix into 100% libre distributions like [Gnewsense]("http://www.gnewsense.org/").

---

### Post by ProlixTST on 2010-07-09
> **KIAaze said:**
> This should fix it:
```
sudo apt-get install unrar
```_Technical info for your information:_
This is not a problem of the package management system. It seems to have been a choice made by the packagers.

"comix" has not been made dependent on "unrar". "unrar" is just a suggested package as you can see here:
[http://packages.ubuntu.com/lucid/comix](http://packages.ubuntu.com/lucid/comix)

This was most likely done because unrar is non-free ([non-libre]("http://en.wikipedia.org/wiki/Gratis_versus_Libre")), thus allowing comix into 100% libre distributions like [Gnewsense]("http://www.gnewsense.org/").


Thank you sir.  You've single-handedly made life easier than it would be.

---

### Post by mekon on 2011-02-16
> **ProlixTST said:**
> Thank you sir.  You've single-handedly made life easier than it would be.

Yes. Comix working fine for me using the 2 commands. Thanks

---

### Post by pierrem-m on 2011-02-16
Hi Folks,

Comix etc have one defect from my point of view in that they don't seem to have the ability to print comics and from time to time I like to do that. (Also I like to combine multipart comic into a single file and that's quite easy with pdf's)

Given that pdf printing is dead easy I tried to find a way to easily convert cbr (and cbz) files to pdf and I rapidly found that in the Linux that is not easy to accomplish so I set about finding a way.

As I want Linux in general and Ubuntu in particular to eventually knock Windoze off it's perch I wanted this to be a GUI method for a very simple reason. If we Linux people say to a Windoze person interested in our much superior operating system that they have to learn arcane CLI commands they'll simply tell us to shove it! 

(Also, I work with Cisco equip and, whilst I have to use CLI there I really don't see why I should have to when I don't need to because the human brain is genetically adapted to pictures NOT letters/numbers!)

After a bit of searching and experimenting here's my method -

Firstly make sure that you have "Archive Manager", "GNOME Photo Printer" and a pdf printer installed (All are in Synaptic Package Manger and also in Ubuntu Software Centre) and then follow the these steps -

(N.B. Steps 2-4  are to keep your original comic file intact and to make it easier to work on one file at a time if you have a lot of comic files in your original folder and also my mouse is set up for single click to open files/folders etc.)

1. Open up the folder that you have the comic in
2. Create a new folder (I call mine "renamed") and open it in a new tab
3. Highlight your comic, right click and select "copy"
4. Click on the "renamed" tab, right click in there and select "paste"
5. Highlight the pasted copy of your comic and select "rename"
6. Highlight the "cbr" at the end of the file name and type "rar" (If it's a "cbz" change that to "zip")
7. Click on any part of the blank area away from the file
8. Right click on your new ".rar" file and select "Open with Archive Manager"
9. Extract the file to your "renamed" folder
10. Click on new folder "Archive Manager has created and there you will find all the individual pages of your comic as .jpg files
11. Fire up GNOME Photo Printer
12. Highlight all the jpg's in 10. above and the drag them over into GNOME Photo Printer
13. You will then need to change the default settings for GNOME Photo Printer (and you'll have to do this each time btw) (I use 18xmx28xm with the margins set to .5cm all round and print as pdf but you can also print directly to paper at this point if you want but you lose the advantages od printing froma pdf)
14. Select your output folder and output file name (I use the "renamed" folder and the comic file name)
15. Click on "Print and very shortly thereafter you'll have a pdf of your comic which you can than print combine etc.

The whole process would be a lot easier though if "Comix" etc had a print function!

Regards

Peter

---

### Post by disturbedite on 2011-02-17
there IS a super easy way to "convert" a PDF file to a combic book archive on linux (with kde): [http://kde-look.org/content/show.php/servicemenu-pdf+for+KDE4?content=37321](http://kde-look.org/content/show.php/servicemenu-pdf+for+KDE4?content=37321)
right-click -> extract images
right-click -> compress images to archive (or use your fav archiver, i use Q7Z).
done.

---

### Post by pierrem-m on 2011-02-20
Hi Folks,

I appreciate disturbedite's interest in this subject but I need to point that my post immediately above disturbedite's is about converting comics (cbr or cbz) **to pdf's** and **not** the other way around.

This is with the aim of printing comics to hardcopy as none of the comic readers seem to have a print function.

Regards to all

Peter

---

### Post by KIAaze on 2011-02-21
You should submit it as a feature request here:
[http://comix.sourceforge.net/contact.html](http://comix.sourceforge.net/contact.html)

It's unlikely that comix developers are reading this thread.

---

### Post by Gwrtheyrn on 2011-12-18
Just for the record, Calibre is able to convert cbr files to .pdf, .mobi and others.

---

### Post by Varad Vyapari on 2012-05-19
thanks

---

