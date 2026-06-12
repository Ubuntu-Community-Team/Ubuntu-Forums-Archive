---
title: "setting fonts to have no antialiasing.. manually?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by lapsey on 2006-08-22
I'm using a lightweight IceWM install becasue of the limitations of my machine. I am convinced that antialiasing is slowing down X, and would like to be able to turn it off. I don't use XFCE or Gnome or anything else like that, so config files are my only tools to hand.

Apparently it is possible to turn antialising off selectively, such as only for small sized fonts - which would suit my situation perfectly.

(I would start to hack up config files until I got something that works but I figured its much quicker to see if anyone knows how to do this properly.)

---

### Post by lapsey on 2006-08-23
bump

---

### Post by lapsey on 2006-08-24
check this out

/etc/fonts/local.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/local.conf file to configure system font access -->

<fontconfig>

<!-- Enable sub-pixel rendering -->

<match target="font">
        <test qual="all" name="rgba"><const>unknown</const></test>
        <edit name="rgba" mode="assign"><const>rgb</const></edit>
</match>
 
<!-- Turn off the Autohinter -->

<match target="font">
       	<edit name="autohint" mode="assign"><bool>false</bool></edit>
</match>

<!-- less than 9px B V Sans made aliased -->

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans</string></test>
	<test compare="less" name="size" qual="any" ><double>9</double></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans</string></test>
	<test compare="less" name="pixelsize" qual="any" ><double>9</double></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans</string></test>
	<test compare="less" name="size" qual="any" ><double>9</double></test>
	<test compare="more" name="weight" ><int>100</int></test>
	<test compare="eq" target="pattern" name="slant" ><const>roman</const></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans</string></test>
	<test compare="less" name="pixelsize" qual="any" ><double>9</double></test>
	<test compare="more" name="weight" ><int>100</int></test>
	<test compare="eq" target="pattern" name="slant" ><const>roman</const></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans Mono</string></test>
	<test compare="less" name="size" qual="any" ><double>12</double></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans Mono</string></test>
	<test compare="less" name="size" qual="any" ><double>12</double></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans Mono</string></test>
	<test compare="less" name="size" qual="any" ><double>12</double></test>
	<test compare="more" name="weight" ><int>100</int></test>
	<test compare="eq" target="pattern" name="slant" ><const>roman</const></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

<match target="font" >
	<test name="family" ><string>Bitstream Vera Sans Mono</string></test>
	<test compare="less" name="size" qual="any" ><double>12</double></test>
	<test compare="more" name="weight" ><int>100</int></test>
	<test compare="eq" target="pattern" name="slant" ><const>roman</const></test>
	<edit mode="assign" name="antialias" ><bool>false</bool></edit>
	<edit mode="assign" name="autohint" ><bool>false</bool></edit>
</match>

</fontconfig>

```

fonts.conf must of course have an include for local.conf.

---

