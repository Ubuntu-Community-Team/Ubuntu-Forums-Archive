---
title: "Antialiasing truetype fonts"
date: 2007-12-06
forum: Desktop Environments
---

### Post by cisk4me on 2007-12-06
I have spent hours fixing a problem with my truetype fonts not being antialiased (ee, ff and gg). The problem was a file called local.conf in /etc/fonts which included further files alias.conf, misc.conf and msfonts-rules.conf. File msfonts-rules.conf had rules to stop the antialiasing of the M$ fonts.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!--  PC-BSD - Fonts configurations v.12012006-->

	<!-- Common rules for the MS fonts -->

<match target="font">
	<test name="family">
		<string>Andale Mono</string>
		<string>Arial</string>
		<string>Arial Black</string>
		<string>Comic Sans MS</string>
		<string>Georgia</string>
		<string>Impact</string>
		<string>Trebuchet MS</string>
		<string>Verdana</string>
		<string>Courier New</string>
		<string>Times New Roman</string>
		<string>Tahoma</string>
		<string>Webdings</string>
	</test>
	<edit mode="assign" name="hinting" >
		<bool>true</bool>
	</edit>
	<edit name="autohint">
		<bool>false</bool>
	</edit>
</match>
	<!-- Arial not bold less than 17px made aliased -->

<match target="font" >
	<test name="family" >
		<string>Arial</string>
	</test>
	<test compare="less" name="size" qual="any" >
		<double>17</double>
	</test>
	<test compare="less_eq" name="weight" >
		<int>100</int>
	</test>
	<edit mode="assign" name="antialias" >
		<bool>false</bool>
	</edit>
</match>

```
I renamed local.conf to local.conf_orig, rebooted and now my truetype fonts are antialiased:)
The permissions on these four files are all 755 instead of 644 and the owner is avg:avg instead of root:root. I have avg from grisoft installed, although at a later date than the conf files. But it's possible that there was an earlier avg installation.

The permissions look like the files come from a FAT partition and the owner like they were installed by avg. Can anyone explain how and why these conf files were installed?

---

