---
title: "Font Rendering xubuntu 14.10 &gt;"
date: 2015-04-04
forum: Desktop Environments
---

### Post by beancounter3 on 2015-04-04
Under settings/appearance/fonts i setup
	font: Sans 10
	anti-aliasing
	hinting: medium
	
But firefox and qt-applications prefer the relaxed
ignorance of these settings.
They use the correct font and ignore the hinting-style.




Here is a solution to fix this:




Under $HOME create a file named .fonts.conf
with following content:




<?xml version='1.0'?> <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'> <fontconfig>
<match target="font">
    <edit mode="assign" name="autohint">
        <bool>false</bool>
    </edit>
</match>
<match target="font">
    <edit mode="assign" name="rgba">
        <const>rgb</const>
    </edit>
</match>
<match target="font">
    <edit mode="assign" name="hinting">
        <bool>true</bool>
    </edit>
</match>
<match target="font">
    <edit mode="assign" name="hintstyle">
        <const>hintmedium</const>
    </edit>
</match>
<match target="font">
    <edit mode="assign" name="antialias">
        <bool>true</bool>
    </edit>
</match> </fontconfig>








no reboot necesseary.
restart firefox or qt-application sufficient.


Best Regards

---

