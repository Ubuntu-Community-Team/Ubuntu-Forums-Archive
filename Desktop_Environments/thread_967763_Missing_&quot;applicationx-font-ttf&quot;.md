---
title: "Missing &quot;application/x-font-ttf&quot;"
date: 2008-11-02
forum: Desktop Environments
---

### Post by lsd on 2008-11-02
I've installed Intrepid Ibex and, oh surprise, there are no truetype thumbnails. I've googled it and found that a string "application/x-font-ttf" is missing in Gnome configuration. How can I enable this? What's the TTF thumbnailer in Nautilus?

---

### Post by Blackwolf_Oz on 2008-11-03
You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the “Universe” component of the repositories. This is done by default in Feisty. After you do that, use the following command from the command line:

$sudo apt-get install msttcorefonts

This will give you the core fonts, but if there are other TrueType fonts that you want installed, it is as easy as copying the font files to the ~/.fonts/ directory.

After installing new fonts, you will have to log out and log in again to be able to see and use the new fonts. If you want to avoid this, you can regenerate the fonts cache by issuing the following command:
$sudo fc-cache -fv

---

### Post by lsd on 2008-11-03
I meant: Nautilus can create thumbnails from  videos, images, douments, and even HTMLs. But how about fonts? In Hardy it was enabled but not in Intrepid. Why?

---

### Post by em4r1z on 2008-11-09
**gnome-font-viewer** and **gnome-thumbnail-font** were depreciated just before the release of Gnome 2.24. I recently needed to preview many fonts and I noticed this. I guess we'll need to manually install (or compile) them to have this feature back. It's annoying, really, for other applications I've checked can only preview installed fonts (why would I install a font without knowing how it looks?)

---

### Post by lsd on 2008-11-10
I don't know what's the reason why Gnome Dev group decided to DELETE features, unlike adding. Now we need any of unique Font Managers available for Linux, FontyPython or FontMatrix, both really horrible!

Could we compile only gnome-font-thumbnailer or we need to implement it within Gnome core libraries?

Sigh!

---

### Post by em4r1z on 2008-11-10
> **lsd said:**
> Could we compile only gnome-font-thumbnailer or we need to implement it within Gnome core libraries?Why it seems that the package that provided **gnome-font-viewer** and **gnome-thumbnail-font** is **gnome-control-centre** thus it might not be that easy to manually install them. I'm still searching for a possible workaround. Maybe other more experienced users will help us accomplish this.

It's annoying, really, I have a lot of fonts for different design projects and now I cannot preview them.

---

### Post by benerivo on 2008-11-10
I agree that the built in font preview is a big loss. Have you tried the gwaterfall package?

---

### Post by lsd on 2008-11-10
I understend you perfectly, I'm designer too. I use to work with Mac at job, but I don't really like it, Finder neither does thumbnails. Gnome (or Thunar/XFCE installing gnome-control-center) was perfect!

Please, is there any Ubuntu or Gnome developer reading this?!

---

### Post by edward_silicon on 2008-11-17
I'm not a graphic designer by trade but I thought this feature was very useful.  It was especially helpful when sifting through hundreds of font files looking for a particular style of lettering.  Rather than having to open each font to inspect it, I could just glance at the thumbnails and quickly choose the font I needed.

Please consider adding this feature back into Gnome!

---

### Post by glotz on 2008-11-18
Have you guys tried the **gnome-specimen** package?

---

### Post by brainkilla on 2008-11-18
> **lsd said:**
> I understend you perfectly, I'm designer too. I use to work with Mac at job, but I don't really like it, Finder neither does thumbnails. Gnome (or Thunar/XFCE installing gnome-control-center) was perfect!

Please, is there any Ubuntu or Gnome developer reading this?!

You should know that Gnome people are known for this kind of *blunders* - removing useful features, marking them obsolete or 'deprecated', making stupid, yet stubborn and spiteful design decisions etc. This is one of them, an historically stupid decision to remove something actually useful. And I don't care about some underlying technical reasons in the vein of bad code, or lack of HIG compliance, or we'll-have-something-much-better-in-three-releases-time explanations...

---

### Post by helmuthdu on 2008-11-22
I found one solution!
Install fontypython, AMAZING PROGRAM!

---

### Post by DrussRob on 2008-12-29
I installed the gnome-specimen package, however nothing happened. This feature was one of the main deciding factors in my switch to and usage of Ubuntu/Gnome and I, being a commercial graphic designer, would lose alot of functional usage if it were not re-implemented.

---

### Post by Stargazer989 on 2009-01-10
i have over 300 font files... some i install and some i don't... depends on what programs i have... still. i would like to not install them just to see them, i have to turn on my desktop just to preview them... it's a serious bother to do this, specially when i have to take them with me and use them in some graphics(like some logos or something). BRING gnome-font-viewer/other BACK, PLEASE!!

---

### Post by lsd on 2009-01-11
Fully agree, Stargazer989. I have a compiled CD with more than 4000 fonts, some of them are japanese ones (impossible to preview with Specimen, FontyPython or anything else).

Everybody's asking for that, misters. You should reconsider recompiling those lines of code to avoid Gnome/XFCE lovers using KDE. I've tested the new **KDE 4.2** desktop on Ubuntu and has this feature, but you need to install EVERYTHING (the core of KDE) to enable it in **Dolphin** file manager. It's about 240 mb installation.

I'm thinking that some coders don't listen what people really needs, like this font preview feature, the global menu on desktop, etc. Wasn't Linux a collaborative and free software where everybody can submit his own oppinion and it should be considered? Or not?

---

### Post by evaklo on 2009-02-10
> **lsd said:**
> .....

I'm thinking that some coders don't listen what people really needs, like this font preview feature, the global menu on desktop, etc. Wasn't Linux a collaborative and free software where everybody can submit his own oppinion and it should be considered? Or not?

I think you are been a bit harsh with the core programmers of Gnome. If you think this (or any) of the improvements should be there, you could send an email to the gnome list programmers, or even you could post it as a bug/enhance in the gnome issue tracker.

Don't get me wrong, I agree with you, but there sure are more important things than a font previewer.

Bye :KS

---

### Post by lsd on 2009-02-10
I'm so sorry if I was too hard. I know that coders do their best, and sometimes they can't go ahead with their projects for any reason (long time ago I used to code in the DOS years) so, don't missunderstand my words, I'm not angry with the Gnome Project or any other. I only wanted to say that in Intrepid was lost an important feature, but now I know it's back (more or less) in Jaunty (alpha 3 tested), so everything's allright (I hope, because alpha 3 doesn't thumbnail well yet).

To all coders and people around Ubuntu, my message is: GO AHEAD!

---

### Post by practic on 2009-02-18
I was missing the font thumbnail previews also.

I tried FontMatrix, FontyPython, Specimen, and Waterfall, but none of them seemed to be able to launch a simple preview window when double-clicking the font file within Nautilus.

But today I discovered that Gwenview (KDE4 version) is able to give a preview from double-click!  For newbies like me, here are the steps:

1. Open terminal, and type: sudo apt-get install gwenview

2. Open a font folder, right-click the Font file and choose Properties.

3. Choose "Open With" tab, and select Gwenview.  If it is not showing in the list, click "Add" and choose it from the list of applications.  If it is not there, click the "Use custom command" text and type gwenview into the command field.  Then click "Add".

So that's at least a work-around until the thumbnail preview gets put back into Gnome.

---

### Post by lsd on 2009-02-18
Nautilus still buggy in Ubuntu Alpha 4. But he tries! :p (need killing task "gnome-font-thumbnailer" due to CPU level overload).

The solution is Jaunty Jackalope!

---

### Post by Saisombun on 2009-02-23
Hi!

I encountered with the same problem and found a solution. It's originally in Russian, so here is a translation. :)

1. Go to [http://packages.ubuntu.com/hardy/gnome-control-center](http://packages.ubuntu.com/hardy/gnome-control-center) and download GNOME Control Center 2.22 for Hardy.

2. Open downloaded DEB file just as a simple archive in File Roller, go to data.tar.gz./usr/bin and extract two binaries:
'gnome-font-viewer' (for viewing a font by a double click)
'gnome-thumbnail-font' (for generating thumbnails in Nautilus)

3. Copy the files to a proper place:
cd /a_place_where_you_extracted_the_files
sudo cp ./gnome-font-viewer ./gnome-thumbnail-font /usr/bin

4. Nautilus > right-click on a font file > Open with > Add > gnome-font-viewer > OK

:)

See also about this bug in Launchpad: [https://bugs.launchpad.net/gnome-control-center/+bug/269920](https://bugs.launchpad.net/gnome-control-center/+bug/269920)

---

### Post by blendenzo on 2009-02-23
I was able to get font thumbnails working by using Saisombun's instructions, then adding the appropriate gconf entries to enable the thumbnailer.  The gconf instructions are here:
[http://library.gnome.org/devel/integration-guide/stable/thumbnailer.html.en](http://library.gnome.org/devel/integration-guide/stable/thumbnailer.html.en)
but they don't explain how to add new entries, something which I have never done before.  After a good deal of searching around, I was able to figure out how to use gconftool-2 to add the necessary entries.

Here are the complete instructions to enable font previews in nautilus:

1. If you have not followed Saisombun's instructions to install the gnome-thumbnail-font binary, do that first.  They are in the post directly previous to this.

2. Open a terminal window as the user you want to enable font thumbnails for (you will need to enable thumbnails for each user individually).

3. Type the following to add an entry for "application/x-font-ttf" to gconf:```
gconftool-2 -t bool -s /desktop/gnome/thumbnailers/application@x-font-ttf/enable true
```
4. Now add the actual command.```
gconftool-2 -t string -s /desktop/gnome/thumbnailers/application@x-font-ttf/command 'gnome-thumbnail-font --size %s %i %o'
```You can specify your own custom preview text by adding the --text *custom* tag to the gnome-thumbnail-font command (put it before the %i).  Here is an example that shows a preview of AaZz instead of just Aa:```
gconftool-2 -t string -s /desktop/gnome/thumbnailers/application@x-font-ttf/command 'gnome-thumbnail-font --size %s --text AaZz %i %o'
```

---

### Post by Saisombun on 2009-02-23
Yessss! It works!! :)

Thank you, **blendenzo**! That's what I missed and finally thought that the problem was somewhere in 2.24 gnome-vfs... It's great to know, that everything is much simpler. A very useful information. Respect! :)

---

### Post by Saisombun on 2009-03-07
One small addition. If you want to see thumbnails not only for TTF fonts, but, for example, for Open Type Fonts as well, add the same keys as Blendenzo explained, but change MIME-type from x-font-ttf to x-font-otf, i.e.:

```
gconftool-2 -t bool -s /desktop/gnome/thumbnailers/application@x-font-otf/enable true

gconftool-2 -t string -s /desktop/gnome/thumbnailers/application@x-font-otf/command 'gnome-thumbnail-font --size %s %i %o'
```

:popcorn:

---

### Post by rafaellaguna on 2009-03-13
Due to a recent update (both XFCE and Gnome installed) I was susprised. I haven't done the trick of GConf, just installed Gnome a week ago, and now thumbnails are back (look screenshot)!

---

