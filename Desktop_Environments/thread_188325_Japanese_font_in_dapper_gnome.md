---
title: "Japanese font in dapper gnome"
date: 2006-06-03
forum: Desktop Environments
---

### Post by matthis on 2006-06-03
Hello,

I have a problem with japanese fonts not rendering very nicely since I upgraded to dapper. Maybe this is because I upgraded a bit before june, before the official release, with a dist-upgrade. In any case, hiragana render nicely but kanji look bad.
Screenshot:
[http://badaboum.bidibom.free.fr/font-screenshot.png](http://badaboum.bidibom.free.fr/font-screenshot.png)

I have tried changing the font hinting and rendering in the gnome font preferences, but to no avail.
Thank you for any help.

---

### Post by JoWilly on 2006-06-03
[QUOTE=matthis]Hello,

I have a problem with japanese fonts not rendering very nicely since I upgraded to dapper. Maybe this is because I upgraded a bit before june, before the official release, with a dist-upgrade. In any case, hiragana render nicely but kanji look bad.
Screenshot:
[http://badaboum.bidibom.free.fr/font-screenshot.png](http://badaboum.bidibom.free.fr/font-screenshot.png)

I have tried changing the font hinting and rendering in the gnome font preferences, but to no avail.
Thank you for any help.[/QUOTE]


hmm.... this japanese writing looks so nice :)

Sorry I can't help you. Have you tried to report a bug on lauchpad to inform the developers of the problem with this font ?

---

### Post by Rondonjin on 2006-06-03
[QUOTE=matthis]Hello,

I have a problem with japanese fonts not rendering very nicely since I upgraded to dapper. Maybe this is because I upgraded a bit before june, before the official release, with a dist-upgrade. In any case, hiragana render nicely but kanji look bad.
Screenshot:
[http://badaboum.bidibom.free.fr/font-screenshot.png](http://badaboum.bidibom.free.fr/font-screenshot.png)

I have tried changing the font hinting and rendering in the gnome font preferences, but to no avail.
Thank you for any help.[/QUOTE]

Have you looked in other threads regarding improving fonts?

[http://www.ubuntuforums.org/showthread.php?t=4456&highlight=howto+font](http://www.ubuntuforums.org/showthread.php?t=4456&highlight=howto+font)

[http://www.ubuntuforums.org/showthread.php?t=180647&highlight=font](http://www.ubuntuforums.org/showthread.php?t=180647&highlight=font)

I'd also suggest installing the MS Mincho and MS Gothic TT fonts. I got them here:

[http://www.themeworld.com/](http://www.themeworld.com/)

I just dropped them in the msttcorefonts directory and they were picked up.

Wayne

---

### Post by matthis on 2006-06-04
Thanks for pointing at these threads.
Unfortunately they did not solve my problem....

---

### Post by Rondonjin on 2006-06-04
[QUOTE=matthis]Thanks for pointing at these threads.
Unfortunately they did not solve my problem....[/QUOTE]

The quality of the DBCS rendering in Ubuntu is definitely not the same as it was when I was using FC5 but overall I prefer Ubuntu to FC. With the MS fonts I mentioned this is the best rendering I get in Firefox (pages are allowed to use their own fonts) Regualr fonts are OK but bold are not.

Wayne

---

### Post by matthis on 2006-06-04
I installed the MS Mincho font to give it a try, but the problem remains the same.
It is very "dry", not anti-aliased. I had no problem in Breezy, even with the normal Kochi Mincho font.
I have just realised that the problem is not present in japanese pages rendered by firefox. The problem appears in nautilus menus/paths, evolution-mail, openoffice...

---

### Post by Rondonjin on 2006-06-04
[QUOTE=matthis]I installed the MS Mincho font to give it a try, but the problem remains the same.
It is very "dry", not anti-aliased. I had no problem in Breezy, even with the normal Kochi Mincho font.[/QUOTE]

There are also the Sazanami Mincho and Gothic TT fonts in the repos. Have you tried them?

Wayne

---

### Post by matthis on 2006-06-04
Yes I have tried them all, they are all "dry", (in the apps mentionned above), while they used to be nice and "shady". Wonder what I broke ;)

---

### Post by seshomaru samma on 2006-06-04
i fresh installed dapper and japanese looks much nicer than in breezy (+ SCIManthy is a much better input system than whatever they used for SCIM in breezy)
this includes open office and the menus
i followed[ this]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")
maybe that might help...

---

### Post by Rondonjin on 2006-06-04
[QUOTE=seshomaru samma]i fresh installed dapper and japanese looks much nicer than in breezy (+ SCIManthy is a much better input system than whatever they used for SCIM in breezy)
this includes open office and the menus
i followed[ this]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")
maybe that might help...[/QUOTE]

Inputting is no problem but I've seen better DBCS font rendering in Mandrivel and FC5.

BTW. I love the blue in the theme you're using. Is it obtainable anywhere?

Also, you should take out one of the M's in your nick, samma is a fish :-)

Wayne

---

### Post by seshomaru samma on 2006-06-04
[QUOTE=Rondonjin]Inputting is no problem but I've seen better DBCS font rendering in Mandrivel and FC5.

BTW. I love the blue in the theme you're using. Is it obtainable anywhere?

[/QUOTE]

I think it's the 'High Contrast Large Print Invert' theme where the controls are 'blue heart' , window border is 'glider' and icons are 'GNOME' but not so sure ...

> Also, you should take out one of the M's in your nick, samma is a fish

my japanese is pathetic , it's mostly guesswork based on the what the Kanji means in Chinese and what Katakana words mean in English...

thanks for the tip , it might be too late now though...
\

---

### Post by Rondonjin on 2006-06-04
[QUOTE=seshomaru samma]I think it's the 'High Contrast Large Print Invert' theme where the controls are 'blue heart' , window border is 'glider' and icons are 'GNOME' but not so sure ...



my japanese is pathetic , it's mostly guesswork based on the what the Kanji means in Chinese and what Katakana words mean in English...

thanks for the tip , it might be too late now though...
\[/QUOTE]

Have you installed Gjiten (Japanese-English dictionary) I find it very useful. It's in the repos. Also go to the Gjiten homepage and download the perl script to install loads of extra dictionaries.

Wayne

---

### Post by Rondonjin on 2006-06-05
[QUOTE=matthis]Yes I have tried them all, they are all "dry", (in the apps mentionned above), while they used to be nice and "shady". Wonder what I broke ;)[/QUOTE]

Although I prefer to have an English system I've come across a Japanese version of Dapper and I'm going to install it on my old test machine to see if it looks better. After I go out tomorrow and buy a pack of CDs, that is :eek: 

[http://www.ubuntulinux.jp/](http://www.ubuntulinux.jp/)

Wayne

---

### Post by Rondonjin on 2006-06-06
[QUOTE=Rondonjin]The quality of the DBCS rendering in Ubuntu is definitely not the same as it was when I was using FC5 but overall I prefer Ubuntu to FC. With the MS fonts I mentioned this is the best rendering I get in Firefox (pages are allowed to use their own fonts) Regualr fonts are OK but bold are not.

Wayne[/QUOTE]

I just downloaded, burnt to Cd and booted the Dapper version from the Japanese team and what a difference! The desktop fonts are clear and the same height between kana and kanji and rendering on web pages is much better than on an Engrish system! Copmare my previous screenshot of Dapper in Japanese and this one!

[http://www.ubuntuforums.org/attachment.php?attachmentid=10541&d=1149403372](http://www.ubuntuforums.org/attachment.php?attachmentid=10541&d=1149403372)

Wayne

---

### Post by kairu0 on 2006-06-07
Following post #1 of this thread made Japanese fonts better here.

[http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647)

---

### Post by matthis on 2006-06-12
Yes! This solved my problem Kairu0! Thank you everyone for you help!!

---

### Post by ~Mi on 2006-06-23
[QUOTE=Rondonjin]I just downloaded, burnt to Cd and booted the Dapper version from the Japanese team and what a difference! The desktop fonts are clear and the same height between kana and kanji and rendering on web pages is much better than on an Engrish system! Copmare my previous screenshot of Dapper in Japanese and this one!

[http://www.ubuntuforums.org/attachment.php?attachmentid=10541&d=1149403372](http://www.ubuntuforums.org/attachment.php?attachmentid=10541&d=1149403372)

Wayne[/QUOTE]

You don't actually have to download the Japanese Team Dapper CD to get those fonts... just add their repos to you sources.list

> deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper/
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper-ja/

then sudo apt-get update && sudo apt-get install ubuntu-ja-keyring  ubuntu-desktop-ja

then just reboot and enjoy ^^

---

### Post by kairu0 on 2006-06-25
My Japanese fonts are the best that they've ever been in Ubuntu now thanks to installing mgothic.ttc, mincho.ttc (from Windows partition), and then copying the following code to /etc/fonts/local.conf:

```
<fontconfig>
	<match target="font">
		<edit name="embeddedbitmap" mode="assign">
			<bool>false</bool>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintnone</const>
		</edit>
	</match>

	<match target="font">
		<test name="lang" compare="contains">
			<string>ja</string>
		</test>
		<test name="spacing" compare="eq">
			<const>dual</const>
		</test>
		<edit name="spacing">
			<const>proportional</const>
		</edit>
		<edit name="globaladvance" binding="strong">
			<bool>false</bool>
		</edit>
	</match>

	<match target="font">
		<test name="lang" compare="contains">
			<string>ja</string>
		</test>
		<test name="outline" compare="eq">
			<bool>false</bool>
		</test>
		<test name="spacing" compare="eq">
			<const>mono</const>
			<const>charcell</const>
		</test>
		<edit name="spacing">
			<const>proportional</const>
		</edit>
		<edit name="globaladvance" binding="strong">
			<bool>false</bool>
		</edit>
	</match>

	<match target="pattern">
		<test qual="any" name="family">
			<string>sans-serif</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaPGothic</string>
			<string>IPAPGothic</string>
			<string>Sazanami Gothic</string>
			<string>Kochi Gothic</string>
		</edit>
	</match> 
	<match target="pattern">
		<test qual="any" name="family">
			<string>serif</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaPMincho</string>
			<string>IPAPMincho</string>
			<string>Sazanami Mincho</string>
			<string>Kochi Mincho</string>
		</edit>
	</match> 
	<match target="pattern">
		<test qual="any" name="family">
			<string>monospace</string>
		</test>
		<edit name="family" mode="prepend" binding="strong">
			<string>IPAMonaGothic</string>
			<string>IPAGothic</string>
			<string>Sazanami Gothic</string>
			<string>Kochi Gothic</string>
		</edit>
	</match> 
</fontconfig>

```

source: [http://people.ubuntu.com/~mvo/bzr/language-selector/language-selector--mvo/fontconfig/ja_JP](http://people.ubuntu.com/~mvo/bzr/language-selector/language-selector--mvo/fontconfig/ja_JP)

---

### Post by Endukugga on 2006-07-02
Hi, I wrote another HOWTO for a better Japanese fonts display in Ubuntu 6.06. You can have a look [here]("http://ubuntuforums.org/showthread.php?t=206280").

I hope you find it useful. Feedback is welcome!

---

