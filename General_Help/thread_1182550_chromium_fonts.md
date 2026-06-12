---
title: "chromium fonts"
date: 2009-06-09
forum: General Help
---

### Post by olaf-g on 2009-06-09
I didn't like the standard fonts chromium uses for rendering. After some experimenting I found a solution. You have to create a file .fonts.conf in your home dir. Be aware that this font config applies to other programs, too (eg. firefox) I love the android fonts, so my .fonts.conf looks like this:

```

  <?xml version="1.0"?>  <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
  <!-- ~/.fonts.conf for per-user font configuration -->
  <fontconfig>
    <alias>
      <family>serif</family>
      <prefer>
        <family>Droid Serif</family>
      </prefer>
    </alias>
    <alias>
      <family>sans-serif</family>
        <prefer>
          <family>Droid Sans</family>
        </prefer>
    </alias>
    <alias>
      <family>monospace</family>
      <prefer>
        <family>Droid Sans Mono</family>
       </prefer>
    </alias>
  </fontconfig>

```

---

### Post by abhiroopb on 2009-11-09
Thanks it looks great now, but, I'm having a problem with this.

I have done exactly as you suggested. But, I am getting the following error whenever I type in certain command into a terminal (haven't figured out which ones it shows up with and which ones it doesn't):

```

$ sudo gedit test
Fontconfig error: "~/.fonts.conf", line 1: XML or text declaration not at start of entity

```

Any suggestions?

---

### Post by Softwayer on 2011-01-04
Make sure you don't have any spaces before *<?xml version="1.0"?>*

---

