---
title: "fonts.conf + Sans issue"
date: 2006-02-07
forum: Desktop Environments
---

### Post by zeeone on 2006-02-07
I use fonts.conf to make Breezy look better. I can alter all fonts except "Sans" and "FreeSans". Can anyone help? I want to make these fonts show as Verdana. Here is my fonts.conf file:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="font" >
  <test compare="less" name="pixelsize" qual="any">
  <double>13</double>
  </test>
  <edit mode="assign" name="antialias" >
    <bool>false</bool>
  </edit>
</match>


<match target="font">
	<test compare="eq" name="weight" qual="any">
	<int>200</int>
	</test>
	<edit mode="assign" name="antialias">
	<bool>true</bool>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Sans</string>
	</test>
	<edit name="family" mode="assign">
	<string>Verdana</string>
	</edit>
</match>


<match target="pattern">
	<test compare="eq" name="family" qual="any">
	<string>Courier New</string>
	</test>
	<edit mode="assign" name="antialias">
	<bool>false</bool>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Bitstream Vera Sans</string>
	</test>
	<edit name="family" mode="assign">
	<string>Verdana</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Bitstream Vera Sans Mono</string>
	</test>
	<edit name="family" mode="assign">
	<string>Verdana</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family">
	<string>Bitstream Vera Seriff</string>
	</test>
	<edit name="family" mode="assign">
	<string>Times New Roman</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Cursor</string>
	</test>
	<edit name="family" mode="assign">
	<string>Verdana</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>FreeSans</string>
	</test>
	<edit name="family" mode="assign">
	<string>Verdana</string>
	</edit>
</match>



<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Serif</string>
	</test>
	<edit name="family" mode="assign">
	<string>Times New Roman</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Helvetica</string>
	</test>
	<edit name="family" mode="assign">
	<string>Arial</string>
	</edit>
</match>

<match target="pattern">
	<test qual="any" name="family" qual="any">
	<string>Palatino</string>
	</test>
	<edit name="family" mode="assign">
	<string>Georgia</string>
	</edit>
</match>
</fontconfig>


```

Thanks in advance!

---

