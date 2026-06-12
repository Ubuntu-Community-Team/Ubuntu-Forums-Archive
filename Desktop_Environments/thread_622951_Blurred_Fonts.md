---
title: "Blurred Fonts"
date: 2007-11-25
forum: Desktop Environments
---

### Post by andreabenaglia on 2007-11-25
Hi All! I'm new to this forum, and I start posting with a font problem. After upgrading Feisty to Gutsy, I found out that fonts in some application look blurred. Since I don't know how to exactly explain the problem, i posted here a screenshot


Fonts in xterm and the text in emacs look fine, wherease the "menu" font (both in emacs and in the other application) don't...

Thanks to all who can help me solve this problem, it's really driving me crazy!

(I tried all the "simple" solutions, like system->look->font etc etc)

---

### Post by ajgreeny on 2007-11-25
Try going to System->Preferences->Appearance and on the fonts tab set the rendering to Subpixel smoothing if you have an LCD monitor.  This may help things considerably.  If not, try all the other options until you get the best available for your system.

---

### Post by andreabenaglia on 2007-11-25
I already tried all possible combinations under system->preferences->appearance with no luck.I'm afraid it is some default font that is automatically chosen for some applications, but I don't know how to change it...

The point is that other fonts look really great...

---

### Post by ajgreeny on 2007-11-25
On the same tab you can change the fonts used in the various situations.  Try out others and there must be something that pleases you.

---

### Post by andreabenaglia on 2007-11-25
Yes, I already tried all those combinations... The problem is that, for example, emacs menu font is not affected by changing fonts through that tab...

I also tried to change the gtk-1.2 default font, and this really improved the problem for some applications, but i still get the same ugly fonts in emacs...

Any help will be much appreciated!!!!!!!

---

### Post by hugmenot on 2007-11-26
If you insist on monochrome fonts, then maybe changing the display dpi in the .Xresources file will help. It looks like the dpi is slightly wrong.

If you might befriend your eyes with antialised and subpixel fonts for Emacs too then I recommend emacs-snapshot. Packages are available for this:

[http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/](http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/)

---

### Post by gungazoo on 2007-11-26
I've had font issues upgrading from Feisty to Gusty as well; most notably in Firefox.  I found the fonts in FF to be so bad I'm back on Feisty right now.  I still have my Gusty install and can get to its filesystem and also boot into it.  I would really like to solve that font issue so that I can use Gusty.  

I keep getting suggestions to do Edit->Preferences->blah and while I appreciate all suggestions it seems to me that since everything on a *NIX system is a file the best way to solve the problem would be something along the lines of:  diff /file.old /file.new -- I just don't know what files to do that to.  Looking at it in the GUI they look the same (Feisty and Gusty).

Here are some screenshots:

[http://pjanderson.googlepages.com/feisty-gusty](http://pjanderson.googlepages.com/feisty-gusty)

(be sure to click on the image to enlarge it)

Peter

---

### Post by qqzhenyi on 2007-11-26
Can you post the content of your /etc/fonts/local.conf file?
my local.conf file looks like this:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/fonts.conf file to configure system font access -->
<fontconfig>
	<match target="font" >
		<edit mode="assign" name="antialias" >
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="rgba" >
			<const>rgb</const>
		</edit>
		<edit mode="assign" name="autohint" >
			<bool>false</bool>
		</edit>
		<edit mode="assign" name="hinting" >
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="hintstyle" >
			<const>hintnone</const>
		</edit>
	</match>
</fontconfig>

```

Screenshot:
[http://i186.photobucket.com/albums/x228/amgong/notubuntu.png](http://i186.photobucket.com/albums/x228/amgong/notubuntu.png)

---

### Post by gungazoo on 2007-11-26
Interesting...On the Gusty install (whose fonts I don't like) there is this in local.conf:

[INDENT] cat /old-data/etc/fonts/local.conf
 <?xml version="1.0"?>
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
 <fontconfig>

 <!-- Font directory list -->

 <dir>/usr/X11R6/lib/X11/fonts/misc</dir>

 </fontconfig>[/INDENT]


and on the Feisty there isn't a local.conf at all.  The /etc/fonts/fonts.conf file is identical on both.

---

### Post by qqzhenyi on 2007-11-26
don't edit the font.conf file because it will be replaced when fontconfig is updated.

try change your local.conf to this, and restart X?
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/fonts.conf file to configure system font access -->
<fontconfig>
	<dir>/usr/X11R6/lib/X11/fonts/misc</dir>
	<match target="font" >
		<edit mode="assign" name="antialias" >
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="rgba" >
			<const>rgb</const>
		</edit>
		<edit mode="assign" name="autohint" >
			<bool>false</bool>
		</edit>
		<edit mode="assign" name="hinting" >
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="hintstyle" >
			<const>hintnone</const>
		</edit>
	</match>
</fontconfig>
```

show you the screenshot *after* i renamed my local.conf file... does it looks like yours?
[http://i186.photobucket.com/albums/x228/amgong/notubuntu2.png](http://i186.photobucket.com/albums/x228/amgong/notubuntu2.png)

---

### Post by gungazoo on 2007-11-26
That is so much better!  Thanks.

It looks like everything is a little bit fuzzy now but the fonts are so much better.  It may be that I've been looking at it too long and the fuzzyness is my eyes not the machine.  I'll look at it again in the morning and play around w/ it.

Thanks again.

---

### Post by qqzhenyi on 2007-11-26
You're welcome :)

---

