---
title: "Japanese font trouble"
date: 2010-10-05
forum: Desktop Environments
---

### Post by akai_kenshi on 2010-10-05
I posted this to [Launchpad]("https://answers.launchpad.net/ubuntu/+source/language-support-ja/+question/126691"), but have yet to get a reply so I thought I'd try here:

By default, Ubuntu uses the Takao series of fonts to display Japanese, which I am satisfied with. However, installing any additional Japanese fonts, either through Ubuntu Software Center, Synaptic, or manually with Font Viewer will change the display of Japanese text system-wide to the newly-installed font. It changes in webpages, titlebars, menus, everything.

What is causing this behavior, and how can I control it?

---

### Post by mips on 2010-10-05
Sorry I can't help but have you tried contacting the Nippon team?
[http://www.ubuntulinux.jp/community](http://www.ubuntulinux.jp/community)

They might have encountered the same problem as well as a possible solution.

---

### Post by akai_kenshi on 2010-10-05
That's probably the best idea, it just requires me to try to use Japanese in a technical context. :frown:

10.10 is just around the corner, so I might wait to see if it's addressed there. I think it has to do with how the system selects fonts in place of 'sans.'

---

### Post by akai_kenshi on 2010-10-08
Okay, so after some help from the the Ubuntu Japan forum and pulling and editing a font config file from an Ubuntu Japanese Remix live disk, here's the solution I came up with for anyone who might be having the same problem:

1) Open a terminal.

2) Type:

```
sudo gedit /etc/fonts/conf.d/69-language-selector-ja-jp.conf
```

3) Copy and paste this code into the opened file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <!-- Japanese (ja) -->
    <match target="pattern">
        <test qual="any" name="family">
            <string>serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>DejaVu Serif</string>
            <string>Takao P&#26126;&#26397;</string>
            <string>IPA P&#26126;&#26397;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#26126;&#26397;</string>
            <string>&#26757;P&#26126;&#26397;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#26126;&#26397;</string>
            <string>&#26481;&#39080;&#26126;&#26397;</string>
        </edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family">
            <string>sans-serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>DejaVu Sans</string>
            <string>Takao P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#12468;&#12471;&#12483;&#12463;</string>
            <string>UmePlus P Gothic</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;</string>
            <string>VL P&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26481;&#39080;&#12468;&#12471;&#12483;&#12463;</string>
        </edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family">
            <string>monospace</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>DejaVu Sans Mono</string>
            <string>Takao&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; &#12468;&#12471;&#12483;&#12463;</string>
            <string>UmePlus Gothic</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;</string>
            <string>VL &#12468;&#12471;&#12483;&#12463;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26481;&#39080;&#12468;&#12471;&#12483;&#12463;</string>
        </edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family">
            <string>Ryumin</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>Takao P&#26126;&#26397;</string>
            <string>IPA P&#26126;&#26397;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#26126;&#26397;</string>
            <string>&#26757;P&#26126;&#26397;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#26126;&#26397;</string>
            <string>&#26481;&#39080;&#26126;&#26397;</string>
        </edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family">
            <string>GothicBBB</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>Takao P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#12468;&#12471;&#12483;&#12463;</string>
            <string>UmePlus P Gothic</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;</string>
            <string>VL P&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#12373;&#12374;&#12394;&#12415; &#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26481;&#39080;&#12468;&#12471;&#12483;&#12463;</string>
        </edit>
    </match>

    <match target="font">
        <test name="family" compare="contains">
            <string>Takao&#12468;&#12471;&#12483;&#12463;</string>
            <string>Takao P&#12468;&#12471;&#12483;&#12463;</string>
            <string>TakaoEx&#12468;&#12471;&#12483;&#12463;</string>
            <string>Takao&#26126;&#26397;</string>
            <string>Takao P&#26126;&#26397;</string>
            <string>TakaoEx&#26126;&#26397;</string>
            <string>IPA&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPAex&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA&#26126;&#26397;</string>
            <string>IPA P&#26126;&#26397;</string>
            <string>IPAex&#26126;&#26397;</string>
            <string>IPA &#12514;&#12490;&#12540; &#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; UI&#12468;&#12471;&#12483;&#12463;</string>
            <string>IPA &#12514;&#12490;&#12540; &#26126;&#26397;</string>
            <string>IPA &#12514;&#12490;&#12540; P&#26126;&#26397;</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;C4</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;C5</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;O5</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;S4</string>
            <string>&#26757;&#12468;&#12471;&#12483;&#12463;S5</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;C4</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;C5</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;O5</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;S4</string>
            <string>&#26757;P&#12468;&#12471;&#12483;&#12463;S5</string>
            <string>&#26757;&#26126;&#26397;</string>
            <string>&#26757;&#26126;&#26397;S3</string>
            <string>&#26757;P&#26126;&#26397;</string>
            <string>&#26757;P&#26126;&#26397;S3</string>
            <string>&#26757;UI&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26757;UI&#12468;&#12471;&#12483;&#12463;O5</string>
            <string>UmePlus Gothic</string>
            <string>UmePlus P Gothic</string>
            <string>VL &#12468;&#12471;&#12483;&#12463;</string>
            <string>VL P&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#12373;&#12374;&#12394;&#12415;&#26126;&#26397;</string>
            <string>&#26481;&#39080;&#12468;&#12471;&#12483;&#12463;</string>
            <string>&#26481;&#39080;&#26126;&#26397;</string>
            <string>TakaoGothic</string>
            <string>TakaoPGothic</string>
            <string>TakaoExGothic</string>
            <string>TakaoMincho</string>
            <string>TakaoPMincho</string>
            <string>TakaoExMincho</string>
            <string>IPAGothic</string>
            <string>IPAPGothic</string>
            <string>IPAexGothic</string>
            <string>IPAMincho</string>
            <string>IPAPMincho</string>
            <string>IPAexMincho</string>
            <string>IPAMonaGothic</string>
            <string>IPAMonaPGothic</string>
            <string>IPAMonaUIGothic</string>
            <string>IPAMonaMincho</string>
            <string>IPAMonaPMincho</string>
            <string>Ume Gothic</string>
            <string>Ume Gothic C4</string>
            <string>Ume Gothic C5</string>
            <string>Ume Gothic O5</string>
            <string>Ume Gothic S4</string>
            <string>Ume Gothic S5</string>
            <string>Ume P Gothic</string>
            <string>Ume P Gothic C4</string>
            <string>Ume P Gothic C5</string>
            <string>Ume P Gothic O5</string>
            <string>Ume P Gothic S4</string>
            <string>Ume P Gothic S5</string>
            <string>Ume Mincho</string>
            <string>Ume Mincho S3</string>
            <string>Ume P Mincho</string>
            <string>Ume P Mincho S3</string>
            <string>Ume UI Gothic</string>
            <string>Ume UI Gothic O5</string>
            <string>Ume Gothic</string>
            <string>Ume P Gothic</string>
            <string>VL Gothic</string>
            <string>VL PGothic</string>
            <string>Sazanami Gothic</string>
            <string>Sazanami Mincho</string>
            <string>Kochi Gothic</string>
            <string>Kochi Mincho</string>
        </test>
        <test name="pixelsize" compare="less_eq">
            <double>18</double>
        </test>
        <edit name="hintstyle" mode="assign">
            <const>hintnone</const>
        </edit>
        <edit name="embeddedbitmap">
             <bool>false</bool>
        </edit>
    </match>
    <!-- Japanese (ja) ends -->
</fontconfig>
```

4) Save the file, close it, and restart your computer.

You should now have a desktop with a nice looking English and Japanese font display, and you can install as many Japanese fonts as you like without altering it.

:guitar:

---

### Post by mips on 2010-10-11
Good to know you came right.

---

### Post by stevepoppers on 2011-04-27
I know this is old, but it just helped me after trying KDE reamed my system fonts. Just wanted to point that out to anyone else who happens to wander here. I actually didn't try it for a while because there was no follow and I didn't have any idea what it would do. So, anyone else with this problem, **this worked for me too.**

Thanksk.

---

### Post by daithib8 on 2011-07-19
There is already a preset in the /etc/fonts/conf.avail directory. To activate it create a symlink to it in /etc/fonts/conf.d. ```
 cd /etc/fonts/conf.d 
sudo ln -s  /etc/fonts/conf.avail/69-language-selector-ja-jp.conf 
 
```

---

