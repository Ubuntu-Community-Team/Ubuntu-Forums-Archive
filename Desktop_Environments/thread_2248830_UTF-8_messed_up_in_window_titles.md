---
title: "UTF-8 messed up in window titles"
date: 2014-10-17
forum: Desktop Environments
---

### Post by Lars Noodén on 2014-10-17
I've noticed that Firefox is messing up special characters in the window title.  See attached image for an example.  This is in Ubuntu 14.04.1 LTS  What do I need to adjust to get these back to normal?

---

### Post by The Cog on 2014-10-17
That's odd. The heading looks OK on my firefox (v33.0). Could it be down to the font you use for window headings? Mine is "Sans Bold".

---

### Post by Lars Noodén on 2014-10-17
This is a plain vanilla, fresh re-installation of 14.04 updated to 14.04.1  I haven't changed the fonts or anything.

---

### Post by vasa1 on 2014-10-17
In Lubuntu, the font in the window title is set in ~/.config/openbox/lubuntu-rc.xml in the section between <theme> and </theme>:```
  <theme><name>AAA111</name><titleLayout>L</titleLayout>
<!--
      available characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
-->
  <keepBorder>no</keepBorder>
    <animateIconify>no</animateIconify>
    <font place="ActiveWindow"><name>Ubuntu Medium</name><size>11</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="InactiveWindow"><name>Ubuntu Medium</name><size>11</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="MenuHeader"><name>Ubuntu</name><size>11</size><!-- font size in points --><weight>normal</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="MenuItem"><name>Ubuntu</name><size>11</size><!-- font size in points --><weight>normal</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="ActiveOnScreenDisplay"><name>Ubuntu Medium</name><size>11</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="InactiveOnScreenDisplay"><name>Ubuntu Medium</name><size>11</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
  </theme>

```And I think that the font chosen there is what we see in the window titles of most if not all programs. So I don't understand why the issue is limited to Firefox.

I forgot to mention that the "smart quotes" in the title of the Launchpad page appear okay for me in Firefox 33 on Lubuntu 14.04 (fully updated).

---

### Post by Lars Noodén on 2014-10-18
It's not limited to Firefox.  That's where I noticed it first.  I should mention that it is also present in LibreOffice, Thunderbird, etc.  The body of said documents uses UTF-8 just fine, though.  I notice that in the terminal there is a problem with filenames and directory names in UTF-8.

---

