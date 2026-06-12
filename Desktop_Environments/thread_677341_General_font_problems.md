---
title: "General font problems"
date: 2008-01-24
forum: Desktop Environments
---

### Post by Anvilfolk on 2008-01-24
Hi everyone,

I've been repeatedly reading through several threads and forums and everything I can find on the subject, but I haven't been able to come up with a solution yet. Since I'm a Computer Science student, and I NEED to code stuff, this is really, really affecting me.

Since I upgraded to Gutsy, fonts (generally speaking) look blurry. I've tried changing settings just about everywhere, hinting, subpixel smoothing, anti-aliasing... And it still looks the same way. I need to fix this ASAP, I'm getting headaches. I have not directly manipulated any configuration files.

General stuff I've noticed so far: in GNOME, System->Preferences->Appearance->Fonts doesn't seem to change the way fonts are displayed in certain apps, such as the three I've attached on a screenshot (Eclipse, Code::Blocks and Firefox). In any case, default system fonts aren't working well either. Normal system fonts don't blur, but the ones from those applications do.

The first thing that annoyed me, stupidly enough, was the shape of the "n" :P It's too thin, much like the u, or h. Check for those letters on the screenshots and you'll see. 

I've tried several DPI settings too, but like I said, I haven't actually found anything that fixed the fonts, either the regular system fonts or the ones in those 3 apps (which from what I've read use GTK?).

I used GNOME but am currently switching to XFCE. I run 1280x800@50 or 60hz. I'm on a laptop, with an nVidia Go 7300 with proprietary nVidia drivers working.

Please don't suggest a fresh install, there's way too much stuff I need to re-install, and I have download limits from my ISP.

Thank you very much for any help (I really do need it).

---

### Post by chewearn on 2008-01-25
You can set firefox fonts from within firefox preferences.  Same with gnome-terminal.

A bit more drastic is install ubuntu-restricted-extras; this will give you new TTF fonts, but will also give you many other things (which you might not want).

---

### Post by Anvilfolk on 2008-01-26
Hi, thank you.

The problem isn't exactly my picking the fonts or not. They displayed fine in Edgy. The problem is font preferences/configurations, the way they are rendered, things such as DPI, hinting, anti-aliasing and others.

I'm not going to try to find a new font that might work with these configurations for every single application I use. That's not much more than a work-around, and a time-consuming one. I want to find a way to get the fonts rendered decently.

Besides, changing the fonts won't make them any less blurry in the IDE's I use, which are the most critical ones.

Thank you again for the post, though. Any other ideas?

---

### Post by hugmenot on 2008-01-26
BTW, Eclipse is run through java, and it has it&#8217;s own renderer, which is completely independent from Gnome. You would have to check the Eclipse settings.
What font rendering do you want anyway? The monochrome super-hinted appearance? There are plenty of fontconfig examples for this on the forums (search term: "fonts like windows") .

---

### Post by Anvilfolk on 2008-01-26
I don't want those "single-pixel-width" rendering, if that's what you're asking. Looking at the screenshots, it doesn't really hit you that hard, but once you're trying to code, you notice how blurry things really are.

Like I said, I'm starting to get headaches. And I really can't have headaches when I'm coding, since that's what I do around 80% of my waking life while I have classes at uni.

I've found a font that looks semi-decent, but I don't expect to have to change every IDE and every text editor (yes, gedit has the same problem) I use to another default font. That's absurd.

I'm guessing these applications I've mentioned are all using the same renderer, because the  blurriness is similar in all of them. What I need is a way to configure that renderer, probably.

Do compare it to a screenshot of Ubuntu in Feisty, which I've attached. You'll probably see the difference.

I *really* need to get some decents fonts. If this doesn't work, I might try updating to Hardy, I'm not going to downgrade. If that doesn't work, well, we'll see. I'd really like to keep Ubuntu.

---

### Post by chewearn on 2008-01-26
Ok, I do a bit more digging; instead of installing ubuntu-restricted-extras, you can just install msttcorefonts, which will give you a couple of Microsoft truetype fonts.

Now, before you object again, I can tell you that these fonts at least do help to make websites look better.  As you may know, many websites are coded for IE, and usually specify MS fonts; Firefox in ubuntu by default don't have these fonts, except by installing msttcorefonts.

I'm not sure if it will help else where, e.g. for Java apps, but I also find that some Java applets running in Firefox looks better (or "more correct") with these fonts.

As for other apps in your system, I can only say this: you only need to configure the font once for each apps; if you have 10 apps that you need to fix, you do that 10 times.  If it takes a minute to fix one apps, that's only 10 minutes spent.  How bad could that be?  Surely it's better than getting a headache, or spend an hour reinstall hardy or feisty?

EDIT:
I should also mention that on all my computers, I haven't seen the problem you are facing; I have had gusty ubuntu and xubuntu installed on a couple of PCs (connected to a few LCD monitors and LCD TVs) and one notebook. So the problem could well be not because of font rendering, but rather graphic driver.  But that's just a guess.

---

### Post by Vesslan on 2008-01-26
hi, i had a similar thing with my fonts, not running ubuntu though, but still.
this page helped me a lot: [http://wiki.archlinux.org/index.php/Xorg_Font_Configuration#Goodies](http://wiki.archlinux.org/index.php/Xorg_Font_Configuration#Goodies)
ignore the pacman stuff, further down are ways to modify ~/.fonts.conf
maybe that might help you too.

ps. i wish ubuntu had a resource like the archwiki, imho it is close to perfect.

---

### Post by Anvilfolk on 2008-01-26
Hi, Vesslan, thanks for the link, it's a very nice one.

It seemed like it was going to do it, what with the reference to GTK and QT and all that. Unfortunately, none of what I did worked. I've been making full restarts to make sure everything gets applied too.

It's fixed some problems in Firefox, it seems, but not all. See the attachment. The upper text is taken from Code::Blocks (same effect as Eclipse), and the lower one from Firefox.

The lower-case letters aren't so bad now, but upper-case still blur like heck.

I'll leave you with a copy of some of my files:

/etc/fonts/fonts.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/fonts.conf file to configure system font access -->
<fontconfig>

<!--
	DO NOT EDIT THIS FILE.
	IT WILL BE REPLACED WHEN FONTCONFIG IS UPDATED.
	LOCAL CHANGES BELONG IN 'local.conf'.

	The intent of this standard configuration file is to be adequate for
	most environments.  If you have a reasonably normal environment and
	have found problems with this configuration, they are probably
	things that others will also want fixed.  Please submit any
	problems to the fontconfig bugzilla system located at fontconfig.org

	Note that the normal 'make install' procedure for fontconfig is to
	replace any existing fonts.conf file with the new version.  Place
	any local customizations in local.conf which this file references.

	Keith Packard
-->

<!-- Font directory list -->

	<dir>/usr/share/fonts</dir>
	<dir>/usr/share/X11/fonts</dir> <dir>/usr/local/share/fonts</dir>
	<dir>~/.fonts</dir>

<!-- Font cache directory list -->

	<cachedir>/var/cache/fontconfig</cachedir>
	<cachedir>~/.fontconfig</cachedir>

<!--
  Accept deprecated 'mono' alias, replacing it with 'monospace'
-->
	<match target="pattern">
		<test qual="any" name="family">
			<string>mono</string>
		</test>
		<edit name="family" mode="assign">
			<string>monospace</string>
		</edit>
	</match>

<!--
  Accept alternate 'sans serif' spelling, replacing it with 'sans-serif'
-->
	<match target="pattern">
		<test qual="any" name="family">
			<string>sans serif</string>
		</test>
		<edit name="family" mode="assign">
			<string>sans-serif</string>
		</edit>
	</match>

<!--
  Accept deprecated 'sans' alias, replacing it with 'sans-serif'
-->
	<match target="pattern">
		<test qual="any" name="family">
			<string>sans</string>
		</test>
		<edit name="family" mode="assign">
			<string>sans-serif</string>
		</edit>
	</match>

<!--
  Load local system customization file
-->
	<include ignore_missing="yes">conf.d</include>

	<config>
<!--
  These are the default Unicode chars that are expected to be blank
  in fonts.  All other blank chars are assumed to be broken and
  won't appear in the resulting charsets
 -->
		<blank>
			<int>0x0020</int>	<!-- SPACE -->
			<int>0x00A0</int>	<!-- NO-BREAK SPACE -->
			<int>0x00AD</int>	<!-- SOFT HYPHEN -->
			<int>0x034F</int>	<!-- COMBINING GRAPHEME JOINER -->
			<int>0x0600</int>	<!-- ARABIC NUMBER SIGN -->
			<int>0x0601</int>	<!-- ARABIC SIGN SANAH -->
			<int>0x0602</int>	<!-- ARABIC FOOTNOTE MARKER -->
			<int>0x0603</int>	<!-- ARABIC SIGN SAFHA -->
			<int>0x06DD</int>	<!-- ARABIC END OF AYAH -->
			<int>0x070F</int>	<!-- SYRIAC ABBREVIATION MARK -->
			<int>0x115F</int>	<!-- HANGUL CHOSEONG FILLER -->
			<int>0x1160</int>	<!-- HANGUL JUNGSEONG FILLER -->
			<int>0x1680</int>	<!-- OGHAM SPACE MARK -->
			<int>0x17B4</int>	<!-- KHMER VOWEL INHERENT AQ -->
			<int>0x17B5</int>	<!-- KHMER VOWEL INHERENT AA -->
			<int>0x180E</int>	<!-- MONGOLIAN VOWEL SEPARATOR -->
			<int>0x2000</int>	<!-- EN QUAD -->
			<int>0x2001</int>	<!-- EM QUAD -->
			<int>0x2002</int>	<!-- EN SPACE -->
			<int>0x2003</int>	<!-- EM SPACE -->
			<int>0x2004</int>	<!-- THREE-PER-EM SPACE -->
			<int>0x2005</int>	<!-- FOUR-PER-EM SPACE -->
			<int>0x2006</int>	<!-- SIX-PER-EM SPACE -->
			<int>0x2007</int>	<!-- FIGURE SPACE -->
			<int>0x2008</int>	<!-- PUNCTUATION SPACE -->
			<int>0x2009</int>	<!-- THIN SPACE -->
			<int>0x200A</int>	<!-- HAIR SPACE -->
			<int>0x200B</int>	<!-- ZERO WIDTH SPACE -->
			<int>0x200C</int>	<!-- ZERO WIDTH NON-JOINER -->
			<int>0x200D</int>	<!-- ZERO WIDTH JOINER -->
			<int>0x200E</int>	<!-- LEFT-TO-RIGHT MARK -->
			<int>0x200F</int>	<!-- RIGHT-TO-LEFT MARK -->
			<int>0x2028</int>	<!-- LINE SEPARATOR -->
			<int>0x2029</int>	<!-- PARAGRAPH SEPARATOR -->
			<int>0x202A</int>	<!-- LEFT-TO-RIGHT EMBEDDING -->
			<int>0x202B</int>	<!-- RIGHT-TO-LEFT EMBEDDING -->
			<int>0x202C</int>	<!-- POP DIRECTIONAL FORMATTING -->
			<int>0x202D</int>	<!-- LEFT-TO-RIGHT OVERRIDE -->
			<int>0x202E</int>	<!-- RIGHT-TO-LEFT OVERRIDE -->
			<int>0x202F</int>	<!-- NARROW NO-BREAK SPACE -->
			<int>0x205F</int>	<!-- MEDIUM MATHEMATICAL SPACE -->
			<int>0x2060</int>	<!-- WORD JOINER -->
			<int>0x2061</int>	<!-- FUNCTION APPLICATION -->
			<int>0x2062</int>	<!-- INVISIBLE TIMES -->
			<int>0x2063</int>	<!-- INVISIBLE SEPARATOR -->
			<int>0x206A</int>	<!-- INHIBIT SYMMETRIC SWAPPING -->
			<int>0x206B</int>	<!-- ACTIVATE SYMMETRIC SWAPPING -->
			<int>0x206C</int>	<!-- INHIBIT ARABIC FORM SHAPING -->
			<int>0x206D</int>	<!-- ACTIVATE ARABIC FORM SHAPING -->
			<int>0x206E</int>	<!-- NATIONAL DIGIT SHAPES -->
			<int>0x206F</int>	<!-- NOMINAL DIGIT SHAPES -->
			<int>0x3000</int>	<!-- IDEOGRAPHIC SPACE -->
			<int>0x3164</int>	<!-- HANGUL FILLER -->
			<int>0xFEFF</int>	<!-- ZERO WIDTH NO-BREAK SPACE -->
			<int>0xFFA0</int>	<!-- HALFWIDTH HANGUL FILLER -->
			<int>0xFFF9</int>	<!-- INTERLINEAR ANNOTATION ANCHOR -->
			<int>0xFFFA</int>	<!-- INTERLINEAR ANNOTATION SEPARATOR -->
			<int>0xFFFB</int>	<!-- INTERLINEAR ANNOTATION TERMINATOR -->
		</blank>
<!--
  Rescan configuration every 30 seconds when FcFontSetList is called
 -->
		<rescan>
			<int>30</int>
		</rescan>
	</config>

</fontconfig>
```

/etc/fonts/local.conf
```
<?xml version="1.0"?>

<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<fontconfig>

<!-- Enable sub-pixel rendering -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>rgb</const>
 </edit>
</match>

<!-- Turn on the autohinter -->
<match target="pattern">
	<edit name="autohint" mode="assign">
		<bool>true</bool>
	</edit>
</match>

<match target="pattern">
	<edit name="dpi" mode="assign"><double>100</double></edit>
</match>

  <!-- Turn on antialiasing -->
  <match target="font">
    <edit name="antialias" mode="assign"><bool>true</bool></edit>
  </match>

  <!-- Don't use bitmapped fonts -->
  <selectfont>
    <rejectfont>
      <pattern>
         <patelt name="scalable"><bool>false</bool></patelt>
      </pattern>
    </rejectfont>
  </selectfont>

  <!-- Disable hinting for bold fonts -->
  <match target="font">
      <test name="weight" compare="more"><const>medium</const></test>
      <edit name="autohint" mode="assign"><bool>false</bool></edit>
  </match>
</fontconfig>
```

/etc/profile
```
 ... stuff ...
export GDK_USE_XFT=1
export QT_XFT=true
```

```
$ xdpyinfo | grep resolution
  resolution:    100x100 dots per inch
$ xdpyinfo | grep dimension
  dimensions:    1280x800 pixels (325x203 millimeters)
```
That's about it. I've tried a few things, so maybe some of those files are conflicting or something along those lines. I've also noticed that there's a slight difference between logging in in GNOME and XFCE, but those are from the system font, which seems half-decent because it doesn't use a lot of upper-case :) Look at the upper-case letters in the 2nd attachment: they were scaled without any interpolation, and to 200%. One pixel = 4 pixels there. See all the darker shades, like shadows? I'm guessing that's what's causing me all this grief.

All I want is the sharp fonts that I had in Feisty :(

---

### Post by hugmenot on 2008-01-27
Okay, I'll tell you what you want. You want a strong hinting ("full") with some antialiasing, but not on the stems. You said you don't want single pixel wide characters, but in your feisty screenshot you have single pixel wide &#8220;sharp&#8221; stems. Depending on the font you probably also want to enable the &#8220;native&#8221; mode and disable the autohinter.
About subpixel rendering: You probably want it, but there's a catch. We have gotten a new LCD filtering algo in Gutsy, which many people rejected, because it was not entirely intra-pixel, like the old one, but it always &#8220;bleeds&#8221; into neighboring pixels. So a patch was made to fontconfig to support two LCD filters, &#8216;legacy&#8217; and &#8216;default&#8217;. Unfortunately the patch doesn't work. So setting lcdfilter = legacy does nothing. This is the point where actually upgrading to hardy might bring you feisty-style subpixel rendering back. With this you get 1px wide snapped stems, and subpixel smoothed, sharp curves.

[http://ubuntuforums.org/showthread.php?t=555964](http://ubuntuforums.org/showthread.php?t=555964)
[https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/159434](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/159434)

BTW, there's a huge group that welcomed and lauded the font appearance changes in Gutsy. That you currently cannot entirely replicate the feisty settings is just a bug. Myself, I use the new subpixel rendering and the authinter set to &#8220;slight&#8221;. And I code a lot, too.

---

### Post by hugmenot on 2008-01-27
Here's a comparison:
[http://spasche.net/files/lcdfiltering/](http://spasche.net/files/lcdfiltering/)

---

### Post by Anvilfolk on 2008-01-27
Hi, thanks a bunch! I think that those things cleared up my options a bit!

However, my problem remains. All the changes I make on those files do not seem to affect the way letters are rendered in Code::Blocks, Eclipse, the GNOME Terminal and gedit, to name a few.

What am I missing?

---

### Post by hugmenot on 2008-01-27
I guess you just messed up your config files. Try to revert all your changes, cleanly.

EDIT: And Eclipse is not affected at all by fontconfig options; it's Java.

---

### Post by Anvilfolk on 2008-01-27
Well, locals.conf didn't exist, and I don't have a ~/.fonts.conf because I want system-wide change.

Java must use some font rendering engine. I know Code::Blocks uses GTK, and I just checked and gedit does too. By the way the fonts look, I'm guessing that's what the JVM used to run Eclipse might be using too.

Like I said, the system font seems half-decent now. The settings I use for the system fonts do not, however, seem to have any effect on those applications, possibly the ones using GTK in general. So that's where I'm guessing I need to go.

---

### Post by hugmenot on 2008-01-28
So, your problem is restricted to the monospace font? There's some special casing in this file /etc/fonts/conf.avail/53-monospace-lcd-filter.conf	.

---

### Post by flargen on 2008-02-01
I think you can get nice smooth and sharp fonts by doing the following:

[LIST]
[*]Deleting /etc/fonts/local.conf
[*]Deleting ~/.fonts.conf
[*]Running ```
sudo dpkg-reconfigure fontconfig-config
``` and selecting Native, Automatic, then No
[*]Going to System->Preferences->Appearance->Fonts and choosing Subpixel rendering
[/LIST]

Obviously, make sure to back-up any files you are going to delete. I'm asking you to delete the above files because you mentioned earlier that the Fonts dialog was having no effect on the appearance. This is because the settings in the above files override Gnome's.

Also, I'm pretty sure that although Eclipse is written in Java, it actually renders its fonts (and widgets etc) using GTK on Linux (through the SWT library, which uses native widgets on each platform). So the settings should effect Eclipse in the same way they do any other GTK or Gnome application.

A screenshot of Eclipse is attached.

Oh, I just realised that you said you don't even have /etc/fonts/local.conf or ~/.fonts.conf. Err, try the last two steps above only then, I guess...

---

### Post by Anvilfolk on 2008-02-01
Hi, thanks!

I'll try that, but I'm pretty sure it's not going to have any effect. Like I said, I didn't have a ~/.fonts.conf or even /etc/fonts/locals.conf, and changing the settings directly in Gnome wasn't affecting applications rendered with GTK - which, as of now, is what I'm trying to solve. Vesslan's link looked like it'd do it, but it did not, unfortunatley.

In any case, I had already done what you've suggested, always with a full computer restart (even restarting only X, you never know).

I have also tried hugmenot's special case file, but while the problem is more apparent in Monospace (and its derivatives), it is by no means a problem singular to that font or font-family. There are fonts that are more propitious to this kind of things, while others are not - and the problem is present in most.

So, what the problem really is, is making GTK use the system options. Also, since I'm switching to XFCE (it's that little bit faster:)), what does the Gnome font settings / appearance menu interface to? Which files? Because I haven't found a similar application in XFCE, and I might as well get to know the files.

Thank you all again for your efforts! This way it definitely does not seem like a lost case :)

---

### Post by flargen on 2008-02-01
Ok, well, the last thing I can think of is to switch to a terminal and forcefully uninstall the fontconfig and fontconfig-config packages, manually delete the contents of /etc/fonts/ and then reinstall the two above packages from the repositories.

Definitely backup the entire /etc/fonts/ directory first.

This command should remove the packages (and their configuration files):
```
sudo dpkg --purge --force-depends fontconfig fontconfig-config
```
Then go (backup first!):
```
sudo rm -r /etc/fonts/
```
And finally:
```
sudo apt-get install -f
```
should automatically install the packages again.

Note - I have not actually tried this before, so don't blame me if it breaks your computer!

---

### Post by Roger Mudd on 2008-02-02
I and many others have also had issues with Gnome fonts. Most of the lucid complaints I've come across have focused on the nebulous "DPI" setting in the Gnome font settings manager.
One solution I found was to discover what DPI my Xserver was actually running at. You can do so by entering the following at the command line:

```
xdpyinfo | grep resolution
```

I think the default DPI is set to 96 DPI. Neither my workstation or my laptop display run at that resolution. Substituting the result from the command above seemed to improve things for me.

Hope this helps!

Sources: 

[Solving the Linux DPI Puzzle]("http://scanline.ca/dpi/")
[Font Sizes]("http://www.gnome.org/~federico/news-2007-01.html#font-sizes")

---

