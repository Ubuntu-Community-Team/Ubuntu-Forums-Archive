---
title: "Font aa style is missing today after normal update."
date: 2005-03-20
forum: Desktop Environments
---

### Post by hantsy on 2005-03-20
When I updated my ubuntu today,the font "AA"(Anti Alias) style is missing.
The following is my local.conf file fragment.
It works well before.
I  always enabled  AA for Bitstreams font , and disabled for other my favorite fonts  if its size is between 8 and 14 px, because it seems more beautiful. But the style is missing.
[PHP]
<match target="font">
        <test name="family">
		<!--             
	   	<string>Bitstream Vera Sans</string>
               	<string>Bitstream Vera Serif</string>
               	<string>Bitstream Vera Sans Mono</string>
		-->
		<string>Tahoma</string>
		<string>Times New Roman</string>
		<string>simsun</string>
        </test>

	<test name="pixelsize" compare="less_eq">
		<double>14</double>
	</test>
	<test name="pixelsize" compare="more_eq">
		<double>8</double>
	</test>
	<edit name="antialias" mode="assign">
		<bool>f</bool>
	</edit>
</match>
<match target="font">
        <test name="family">
		<!--           	
		<string>Bitstream Vera Sans</string>
               	<string>Bitstream Vera Serif</string>
               	<string>Bitstream Vera Sans Mono</string>
		-->
		<string>Tahoma</string>
		<string>Times New Roman</string>
		<string>simsun</string>
        </test>
	<test name="size" compare="less_eq">
		<double>14</double>
	</test>
	<test name="size" compare="more_eq">
		<double>8</double>
	</test>
	
	<edit name="antialias" mode="assign">
		<bool>f</bool>
	</edit>
</match>
[/PHP]

---

### Post by hantsy on 2005-03-20
Oh,sorry!
This is a problem about Hoary.Please move to 5.04 discussion area for me ,Thanks .

---

