---
title: "Better font appearance, hopefully ...."
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by timus on 2007-08-25
As it seems most of the sites use Arial font, which does not render very well in linux
here is a custom .fonts.conf for better appearance of text especially in firefox. What it actually does is sybstituting arial fonts with RedHat's Liberation font,

Any comments are welcome.

Save or append to .fonts.conf in your home directory the following:

[I]<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- If the font is bold, turn off autohinting -->
  <match target="font">
    <test name="weight" compare="more">
      <const>medium</const>
    </test>
    <edit mode="assign" name="autohint">
      <bool>false</bool>
    </edit>
    <edit mode='assign' name='hintstyle'>
      <const>hintfull</const>
    </edit>
  </match>

<match target="pattern">
            <test qual="any" name="family">
                    <string>Arial</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Liberation Sans</string>
            </edit>
</match>
</fontconfig>[/I]

---

### Post by bronze on 2007-08-25
I would love a screenshot before trying this. Do you mind?

---

### Post by mechanic on 2007-08-28
After some time spent fiddling with fonts on various sites, I came to the conclusion that Tahoma was the villain of the piece, especially on Ubuntuforum pages! The only easy way out was to delete the tahoma.ttf file, rebuild the cache ("fc-cache -f -v")and reset Opera prefs to suit. Mucho improvement!

m.

---

