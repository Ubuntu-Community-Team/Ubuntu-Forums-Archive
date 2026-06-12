---
title: "Font problem in ubuntu hardy [ligature problem]"
date: 2008-05-13
forum: Desktop Environments
---

### Post by windtracekimo on 2008-05-13
Hi dear all:
I just upgraded to ubuntu 8.04LTS from 7.10.
Every package is updated to the latest.
When I look at the webpage in firefox 2.0.0.14. with something like this page [http://www.gnome.org/~jamesh/firefox-ligature.html](http://www.gnome.org/~jamesh/firefox-ligature.html)
I saw some words are mixed together(such as ff, fi, as the attached picture shows)
Has anyone got this problem?

ps: I use the following fonts.conf in my home directory to make the font more smooth
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

Appreciate any help
Thanks

---

