---
title: "fontconfig - No more bytecode interpreter?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by bmgz on 2006-02-23
I recently tried Dapper flight 4, and then went back to Breezy...
I did a clean install/update and noticed when I did:
 $ sudo dpkg-reconfigure fontconfig

The curses menu only displays Native/Autohinter/None, Their used to be An option to enable Bytecode Interpreter. :confused: 

My fonts are either Too sharp or blurry. I have a crt monitor and this subpixel rendering is too sharp, it leaves a lasting impression on my eyes :???: 

Is their some other way to enable bytecode interpretor? perhaps roll back to an old fontconfig version?

---

### Post by Xian on 2006-02-23
[QUOTE=bmgz]Is their some other way to enable bytecode interpretor? perhaps roll back to an old fontconfig version?[/QUOTE]

Try it. Download the 5.10 package and install. You might also try using a decent /etc/fonts/local.conf file and installing the msttcorefonts package. Restart X.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/local.conf file to configure system font access -->

<fontconfig>

<!-- Enable sub-pixel rendering -->

<!--
        <match target="font">
                <test qual="all" name="rgba">
                        <const>unknown</const>
                </test>
                <edit name="rgba" mode="assign"><const>rgb</const></edit>
        </match>
-->


<!-- Use the Autohinter -->

<match target="font">
       <edit name="autohint" mode="assign"><bool>true</bool></edit>
       </match>

       <!-- Disable Autohinting for bold fonts -->

<match target="font">
   <test name="weight" compare="more">
<const>medium</const>
</test>
   <edit name="autohint" mode="assign"><bool>false</bool></edit>
</match>

<!-- Exclude/Include a range of fonts for Anti Aliasing -->

<!--

<match target="font">
<test qual="any" name="size" compare="more">
                <double>9</double>
        </test>
        <test qual="any" name="size" compare="less">
                <double>14</double>
        </test>
        <edit name="antialias" mode="assign">
        <bool>true</bool>
        </edit>
</match>

-->


<!-- And/Or disable Anti Aliasing for a range on pixel-based size. -->

<!--

<match target="font">
        <test compare="less" name="pixelsize" qual="any">
                <double>20</double>
        </test>
        <edit mode="assign" name="antialias">
                <bool>false</bool>
        </edit>
</match>

-->

<dir>~/.fonts</dir>
<dir>/usr/share/fonts</dir>
<dir>/usr/share/X11/fonts/Type1</dir>
<dir>/usr/share/X11/fonts/misc</dir>
<dir>/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType</dir>

</fontconfig>

```

---

