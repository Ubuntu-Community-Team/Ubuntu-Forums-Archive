---
title: "HOWTO: Make your fonts look as good as they do in Windows (version 2.0)"
date: 2008-12-09
forum: General Help
---

### Post by thegizmoguy on 2008-12-09
(I'm not sure if this is the "proper" way of doing it...it just works)  I'm on an LCD laptop @ 1280 x 800 and the default rendering was annoying the hell out of me.

1) In the terminal type:

```
sudo gedit .fonts.conf
```

2) Paste in the following:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
    <edit name="antialias" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

3) Click "Save" and close
===================================

Optional but I like it:

4) Go Add/Remove search "core fonts"

5) Install Microsoft Core Fonts

6) Download Segoe UI (Vista font) from [http://home.arcor.de/salnet/segoe_ui.zip](http://home.arcor.de/salnet/segoe_ui.zip)

7) Go Settings > Appearance > Fonts

Set App to Segoe UI 9
Set Docu to Segoe UI 10
Set Desk to Segoe UI 10
Set Window to Trebuchet MS Bold 10

8) In the Fonts tab still, enable sub-pixel smoothing

9) Set subpixel smoothing to "light" from details button

===========================================


HIT CTRL + BACKSPACE (IT WILL LOG YOU OUT) AND YOU GOOD TO GO!

---

### Post by socomoddjob on 2008-12-12
this worked out for me nicely, thanks.

---

