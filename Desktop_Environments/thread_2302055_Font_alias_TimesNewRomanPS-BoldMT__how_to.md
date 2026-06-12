---
title: "Font alias TimesNewRomanPS-BoldMT : how to ?"
date: 2015-11-07
forum: Desktop Environments
---

### Post by cheribibi on 2015-11-07
Hi there,

I'm receiving pdf files with some non embedded MS fonts I don't get on my Ubuntu 14.04 workstation... So they're badly displayed on my computer.

While I've been able to alias some of these MS fonts in ~/.config/font-manager/local.conf I'm getting stuck with "TimesNewRomanPS-BoldMT".

Here's what my local.conf looks like right now : 
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

  <match> 
    <test name="family"><string>TimesNewRomanPSMT</string></test>
    <edit name="family" mode="assign" binding="same">
      <string>Times New Roman</string>
    </edit>
  </match>

  <match>
    <test name="family"><string>TimesNewRomanPS-BoldMT</string></test>
    <edit name="family" mode="assign" binding="same">
      <string>Times New Roman</string>
    </edit>
  </match>

  <match>
    <test name="family"> <string>ArialMT</string> </test>
    <edit name="family" mode="assign" binding="same">
      <string>Arial</string>
    </edit>
  </match>

</fontconfig>
```

Hopefully, I'd like TimesNewRomanPS-BoldMT to look like Bold "Times New Roman", although I'd be ok with non-bold "Times New Roman"...:roll:

And here's what fc-match is telling me about these MS fonts alias :
```

$ fc-match ArialMT
arial.ttf: "Arial" "Normal"

$ fc-match TimesNewRomanPSMT
Times_New_Roman.ttf: "Times New Roman" "Normal"

$ fc-match TimesNewRomanPS-BoldMT
DejaVuSans.ttf: "DejaVu Sans" "Book"

```

Any suggestion ?

---

### Post by oldos2er on 2015-11-07
Have you installed the package ttf-mscorefonts-installer?

---

### Post by cheribibi on 2015-11-07
Thanks oldos2er for such a quick reply.

Yes, ttf-mscorefonts-installer is here and, to make sure, I've already been reinstalling it :

$ dpkg -l ttf-mscorefonts-installer
[...]
+++-===========================-==================-==================-===========================================================
ii  ttf-mscorefonts-installer   3.4+nmu1ubuntu1    all                Installer for Microsoft TrueType core fonts

---

### Post by oldos2er on 2015-11-07
I just noticed the "PS" appended to your font name; I don't know if the mscorefonts package installs postscript fonts, though I don't think it does. Have you tried searching for package keywords "postscript times new roman"?

---

### Post by cheribibi on 2015-11-07
I'm not trying to install any new font, but just aliasing un-embedded MS fonts from these PDF I receive, in order to be able to read them ('cause now it's almost unreadable here and there, with Ä and so on...)

As you can see, I've been able to alias 2 of them : ArialMT aliases to Arial and TimesNewRomanPSMT aliases to Times New Roman. 

Right, now why can't I alias TimesNewRomanPS-BoldMT to Times New Roman ?

---

### Post by oldos2er on 2015-11-07
I don't know, hopefully someone who does will happen along soon.

---

