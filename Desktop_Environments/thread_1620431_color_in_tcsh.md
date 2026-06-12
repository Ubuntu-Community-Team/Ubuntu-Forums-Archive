---
title: "color in tcsh"
date: 2010-11-13
forum: Desktop Environments
---

### Post by rre12 on 2010-11-13
I am wondering how do I use the same color settings as the one in bash for tcsh? Currently everything is all white in tcsh when I typed in the command 'ls'. Also I used the chsh command to change my default shell, but when I typed in echo $SHELL, I still get /bin/bash, is this supposed to be normal?

---

### Post by x1a4 on 2010-11-16
Add the following to your ~/.tcshrc file
```
setenv LS_COLORS  'pi=40;33:bd=40;33;01:cd=40;33;01:or=01;05;37;41:mi=01;05;37;41:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.xbm=01;35:*.xpm=01;35:*.png=01;35:*.mng=01;35:*.tif=01;35:*.tiff=01;35:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.rar=01;31:*.bz2=01;31:*.bz=01;31:*.tz=01;31:*.rpm=01;31:*.deb=01;31:*.cpio=01;31:*.7z=01;31:*.svg=01;35:*.xcf=01;35'
```

Modify the colours and add/remove file types to your liking.  

Colour codes are: 
```

First number:
0 - normal
1 - bold
2 - normal again
3 - background color
4 - underline the text
5 - blinking

Foreground colours (3rd number):
30 - black
31 - brick red
32 - green
33 - yellow ochre
34 - dark blue
35 - magenta
36 - cyan
37 - white/gray

```

The background colour code is the same as the foreground but with 10 added to it. Ex.: Background of red can be achieved with code 41.

Once done, run: 
```
source ~/.tcshrc
```

If you want $SHELL to change, you have to run tcsh as a login shell.  Add the **-l** switch when changing shells.  It has to be the _only_ option present.

Have a look in the tcsh manual for more info: 
```
man tcsh
```

There's also a project called [The tcshrc project]("http://tcshrc.sourceforge.net/") with great tcsh configuration you can use as a base for your own tweaks.

---

### Post by iamanidiot123 on 2011-12-22
Add this to your .tcshrc file:
```
alias ls 'ls --color=auto'
alias grep 'grep --color=auto'
alias fgrep 'fgrep --color=auto'
alias egrep 'egrep --color=auto'
```
I just figured out how to do that after looking at the .bashrc file. :)
It colors grep, fgrep, egrep, and ls.

---

