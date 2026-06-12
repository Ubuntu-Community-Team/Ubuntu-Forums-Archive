---
title: "Mapping fonts"
date: 2009-03-17
forum: Desktop Environments
---

### Post by schickb on 2009-03-17
Using fc-match I've found that "Helvetica" and "Times" are mapped to old 75dpi fonts by default in Ubuntu.

>fc-match "Helvetica"
helvR12.pcf.gz: "Helvetica" "Regular"

>fc-match "Times"
timR12.pcf.gz: "Times" "Regular"

I'd like to force these to more modern fonts for all users on my system. I've tried adding the following to **/etc/fonts/local.conf** and then restarting X, but it has no effect. Any ideas what I'm doing wrong?

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<alias>
        <family>Times</family>
        <prefer><family>Times New Roman</family></prefer>
        <default><family>serif</family></default>
</alias>
<alias>
        <family>Helvetica</family>
        <prefer><family>Arial</family></prefer>
        <default><family>sans</family></default>
</alias>
<alias>
        <family>Courier</family>
        <prefer><family>Courier New</family></prefer>
        <default><family>monospace</family></default>
</alias>
</fontconfig>
```

---

### Post by Zorael on 2009-03-17
Yeah, Helvetica looks awful. That would explain why, too.

I think you want it to look like this. (Excerpt copy/pasted from my user-specific **~/.fonts.conf**)
```
 <!-- Font Replacement -->
 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Verdana**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**DejaVu Sans**</string>
  </edit>
 </match>

 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Helvetica**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**Arial**</string>
  </edit>
 </match>

 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Lucida**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**Arial**</string>
  </edit>
 </match>

 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Lucida Grande**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**Arial**</string>
  </edit>
 </match>

 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Tahoma**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**DejaVu Sans**</string>
  </edit>
 </match>

 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>**Geneva**</string>
  </test>
  <edit mode="assign" name="family" >
   <string>**Arial**</string>
  </edit>
 </match>
```

---

### Post by schickb on 2009-03-17
> **Zorael said:**
> Yeah, Helvetica looks awful. That would explain why, too.

I think you want it to look like this. (Excerpt copy/pasted from my user-specific **~/.fonts.conf**)

Its not really clear to me when to use <match> and when to use <alias>. I did some more digging and I think my solution didn't work because it needed to be <alias binding="same"> instead of just <alias>. I also decided to assign more specific family names. The following now works as expected:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
   <alias binding="same">
      <family>Helvetica</family>
      <prefer>
      <family>DejaVu Sans</family>
      </prefer>
   </alias>
   <alias binding="same">
      <family>Times</family>
      <prefer>
      <family>DejaVu Serif</family>
      </prefer>
   </alias>
   <alias binding="same">
      <family>Courier</family>
      <prefer>
      <family>DejaVu Sans Mono</family>
      </prefer>
   </alias>
</fontconfig>
```

Sure seems like something similar to this should be the default for Ubuntu. /etc/fonts/conf.d/30-metric-aliases.conf has something similar, but it uses <accept> rather than <prefer> which seems to let the old 75dpi fonts win.

---

