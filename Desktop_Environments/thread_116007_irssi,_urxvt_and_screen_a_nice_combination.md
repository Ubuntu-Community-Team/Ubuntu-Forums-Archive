---
title: "irssi, urxvt and screen: a nice combination"
date: 2006-01-11
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-11
For those of you who like using irssi for IRC in a screen session, I am posting my experiences with the urxvt-unicode app.

From the urxvt man page:

"rxvt-unicode, version 5.6, is a colour vt102 terminal emulator intended as an xterm(1) replacement for users who do not require features such as Tektronix 4014 emulation and toolkit-style configurability. As a result, rxvt-unicode uses much less swap space -- a significant advantage on a machine serving many X sessions."

I have been spoiled by gnome-terminal, and its display of anti-aliased fonts, and I have found that urxvt displays them equal to or better than gnome-terminal.

urxvt is available in the universe repo as rxvt-unicode.
```

sudo apt-get rxvt-unicode

```

I have found urxvt to be quite nice looking with the following added to ~/.Xdefaults

```

urxvt.background:black
urxvt.foreground:grey
urxvt.cursorBlink:true
urxvt.scrollBar:false
urxvt.scrollBar_right:false
urxvt.saveLines:32767
urxvt.font: xft:Courier 10 Pitch-12
urxvt.boldFont: xft:Courier 10 Pitch-12:bold
urxvt.geometry:110x30

```

See the below screenshot for a preview.

---

