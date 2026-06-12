---
title: "Fonts not as good as Ubuntu, solution?"
date: 2009-09-04
forum: Desktop Environments
---

### Post by frankwakeman on 2009-09-04
With 9.04, the fonts clarity came on leaps and bounds, and became arguably better than Windows and Mac for one reason or another.  That applied to Ubuntu and Gnome, but I'm now trying out Kubuntu and there the fonts are still at the 8.10 stage.  Has anyone here sorted this out, or is there some .conf file to use, maybe amended from whatever was done in Ubuntu 9.04.

I'm referring specifically to the 'slight' anti-aliasing setting for LCD displays, as medium or full looks odd with fonts in Open Office especially.

Thanks in advance.

---

### Post by Zorael on 2009-09-04
I'm not sure I understand. Can't you set it to use slight hinting in system settings, too?

To cover other apps that don't listen to KDE's settings, you could create a ~/.fonts.conf file and specify slight hinting there.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>**hintslight**</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

You can also make system-wide changes by removing/adding symlinks from **/etc/fonts/conf.avail/** into **/etc/fonts/conf.d/**.

---

### Post by frankwakeman on 2009-09-04
Yes, I have 'slight' selected.  But it is not as clear using Kubuntu or Mint 7 KDE as with Gnome Ubuntu.  There are all those little colours in the fonts that with Gnome were a thing of the past after Ubuntu 8.10.

---

### Post by Zorael on 2009-09-04
Now do correct me if I'm wrong, but I believe the colors suggest you have the "wrong" kind of supixel rendering enabled, in terms of what order the colors that make up each pixel is in. Is it set to RGB in both environments?

Again, beyond the settings you can touch in systemsettings there are those in **/etc/fonts/conf.d/**, of which user-specific changes should be saved in **~/.fonts.conf**. Looking at the contents of a vanilla (Karmic) Kubuntu installation;
```
$ ls **/etc/fonts/conf.d/**
10-antialias.conf                 40-nonlatin.conf              65-nonlatin.conf
10-hinting.conf                   41-ttf-arphic-uming.conf      66-wqy-zenhei-sharp.conf
10-hinting-slight.conf            44-wqy-zenhei.conf            69-unifont.conf
11-lcd-filter-lcddefault.conf     45-latin.conf                 70-no-bitmaps.conf
20-fix-globaladvance.conf         49-sansserif.conf             80-delicious.conf
20-unhint-small-vera.conf         50-user.conf                  89-ttf-thai-tlwg-synthetic.conf
25-ttf-arphic-uming-render.conf   51-local.conf                 90-synthetic.conf
30-cjk-aliases.conf               53-monospace-lcd-filter.conf  90-ttf-arphic-uming-embolden.conf
30-defoma.conf                    60-latin.conf                 99pdftoopvp.conf
30-metric-aliases.conf            64-ttf-arphic-uming.conf      README
30-urw-aliases.conf               64-ttf-thai-tlwg.conf
35-ttf-arphic-uming-aliases.conf  65-fonts-persian.conf
```
All of those are my enabled settings. They're symlinks to available configuration files in **/etc/fonts/conf.avail/**;
```
$ ls **/etc/fonts/conf.avail/**
10-antialias.conf                   29-language-selector-ko-kr.conf   66-wqy-zenhei-sharp.conf
10-autohint.conf                    29-language-selector-zh.conf      66-wqy-zenhei-sharp-no13px.conf
10-hinting.conf                     30-cjk-aliases.conf               69-language-selector-ja-jp.conf
10-hinting-full.conf                30-metric-aliases.conf            69-language-selector-ka-ge.conf
10-hinting-medium.conf              30-urw-aliases.conf               69-language-selector-ko-kr.conf
10-hinting-slight.conf              35-ttf-arphic-uming-aliases.conf  69-language-selector-zh-cn.conf
10-no-sub-pixel.conf                40-nonlatin.conf                  69-language-selector-zh-hk.conf
10-sub-pixel-bgr.conf               41-ttf-arphic-uming.conf          69-language-selector-zh-mo.conf
10-sub-pixel-rgb.conf               44-wqy-zenhei.conf                69-language-selector-zh-sg.conf
10-sub-pixel-vbgr.conf              45-latin.conf                     69-language-selector-zh-tw.conf
10-sub-pixel-vrgb.conf              49-sansserif.conf                 69-unifont.conf
10-unhinted.conf                    50-user.conf                      70-no-bitmaps.conf
11-lcd-filter-lcddefault.conf       51-local.conf                     70-yes-bitmaps.conf
20-fix-globaladvance.conf           53-monospace-lcd-filter.conf      80-delicious.conf
20-unhint-small-vera.conf           60-latin.conf                     89-ttf-thai-tlwg-synthetic.conf
25-ttf-arphic-uming-bitmaps.conf    64-ttf-arphic-uming.conf          90-synthetic.conf
25-ttf-arphic-uming-nobitmaps.conf  64-ttf-thai-tlwg.conf             90-ttf-arphic-uming-embolden.conf
25-ttf-arphic-uming-render.conf     65-fonts-persian.conf             99-language-selector-zh.conf
25-unhint-nonlatin.conf             65-khmer.conf
29-language-selector-ja-jp.conf     65-nonlatin.conf
```
Now, looking at the contents of conf.d, admittedly on this Karmic machine, we see both **11-_lcd-filter_-lcddefault.conf** and **53-monospace-_lcd-filter_.conf** are enabled. Perhaps they could be the cause of what you're experiencing, and GNOME is simply bypassing them with its own settings, while KDE does not?

Since they're symlinks, you can freely delete the files in **/etc/fonts/conf.d/** to disable settings, and freely make new symlinks of the files in **conf.avail** into **conf.d**. Might want to record what the defaults were.

---

