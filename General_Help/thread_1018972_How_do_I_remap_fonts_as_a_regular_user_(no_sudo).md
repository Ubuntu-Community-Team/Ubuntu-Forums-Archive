---
title: "How do I remap fonts as a regular user? (no sudo)"
date: 2008-12-22
forum: General Help
---

### Post by 2cute4u on 2008-12-22
On a system where I'm a regular user (i.e. I don't have sudo preveleges"), I'm trying to remap:** Serif** to **Nimbus Roman No9 L**,** Sans** to **Nimbus Sans L**,and** Arial** to **Nimbus Sans L**

I tried editing my ~/.font.conf file to as foolows:```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="pattern">
    <test qual="any" name="family" qual="any">
    <string>Sans-serif</string>
    </test>
    <edit name="family" mode="assign">
    <string>Nimbus Sans L</string>
    </edit>
</match>
<match target="pattern">
    <test qual="any" name="family" qual="any">
    <string>Serif</string>
    </test>
    <edit name="family" mode="assign">
    <string>Nimbus Roman No9 L</string>
    </edit>
</match>
<match target="pattern">
    <test qual="any" name="family" qual="any">
    <string>Arial</string>
    </test>
    <edit name="family" mode="assign">
    <string>Nimbus Sans L</string>
    </edit>
</match>
</fontconfig>
```When I did that, I got the following errors:```
 
$ fc-match Sans-serif
Fontconfig error: "~/.fonts.conf", line 5: duplicate attribute
DejaVuSans.ttf: "DejaVu Sans" "Book"

$ fc-match Serif
Fontconfig error: "~/.fonts.conf", line 5: duplicate attribute
DejaVuSans.ttf: "DejaVu Serif" "Book"

$ fc-match Arial
Fontconfig error: "~/.fonts.conf", line 5: duplicate attribute
Arial.ttf: "Arial" "Normal"

```What am I doing wrong and how do I get it to work?

---

