---
title: "Font rendering XP vs X11/Dapper"
date: 2006-07-27
forum: Desktop Environments
---

### Post by neo_reloaded on 2006-07-27
Hi
I have dapper on my laptop. Fonts look really great after performing this - [http://ubuntuforums.org/showpost.php?p=1041769&postcount=1](http://ubuntuforums.org/showpost.php?p=1041769&postcount=1) quick trick.

But in general, I still find certain TTF fonts look far better on Windows XP or OS X. I do not have XP on my laptop, but I got a comparison screenshot of How XP displays Monaco 9pt on a desktop vs how X11/Gnome/Dapper displays Monaco 9pt on my laptop(res 1600 X 1200 - 96 X 96 dpi)
(Please see the attached comparison image)
Is there a way to improve the look?
Thanks!!!

---

### Post by neo_reloaded on 2006-08-03
btw, I got this fixed by adding a nice .fonts.config file on my home folder.
Here is how it looks like:
<?xml version="2.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<!-- Info at [http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts) -->

	<!-- Replace Courier with a better-looking font -->
	<match target="pattern" name="family">
		<test name="family" qual="any">
			<string>Courier</string>
		</test>
		<edit name="family" mode="assign">
			<!-- Other choices - Courier New, Luxi Mono -->
			<string>Bitstream Vera Sans Mono</string>
		</edit>
	</match>

	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hinting" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintmedium</const>
		</edit>
	</match>

	<!-- Disable autohint for bold fonts, otherwise they look *too* bold -->
	<match target="font">
   		<test name="weight" compare="more">
			<const>medium</const>
		</test>
   		<edit name="autohint" mode="assign">
			<bool>false</bool>
		</edit>
	</match>

	<!-- Reject bitmap fonts in favour of Truetype, Postscript, etc. -->
	<selectfont>
		<rejectfont>
			<pattern>
				<patelt name="scalable">
					<bool>false</bool>
				</patelt>
			</pattern>
		</rejectfont>
	</selectfont>

</fontconfig>

---

