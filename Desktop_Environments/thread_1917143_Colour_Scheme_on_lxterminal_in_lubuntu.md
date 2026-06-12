---
title: "Colour Scheme on lxterminal in lubuntu"
date: 2012-01-29
forum: Desktop Environments
---

### Post by charnley on 2012-01-29
Hi Guys.

Just installed lubuntu, but after working a few hours with
the lxterminal, i find the syntax highlight colours are really 
annoying. I cannot find the anyway too change the colours 
except the 'background / foreground' colours, which doesnt 
change the very dark blue for comments. 

How do I make the colours more readable?

best regards
Jim

---

### Post by Rodney9 on 2012-01-29
Go to 'Edit' 'Preferences' in KXTerminal and you can change colours, fonts etc. See screenshot below.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by charnley on 2012-01-29
Thanks for the prompt reply.

These settings, however, does not change the colour of the
syntaxhighlight

fx:

ls -> folders are very dark

vim code.src -> comment syntax highlight are very hard to read
with such a dark colour.

These were the colours I wanted to change.

---

### Post by Rodney9 on 2012-01-29
Marty Jack from LXDE Org [http://forum.lxde.org/viewtopic.php?t=1478&f=26](http://forum.lxde.org/viewtopic.php?t=1478&f=26) wrote:
> At this time we do not offer any more customization than foreground/background. You are encouraged to run any terminal emulator that meets your needs. 

These pages has tips on Vim Syntax Colours - 

[http://unix.stackexchange.com/questions/13258/dark-blue-color-in-vim-or-ls-output-in-linux](http://unix.stackexchange.com/questions/13258/dark-blue-color-in-vim-or-ls-output-in-linux)

[http://vim.wikia.com/wiki/256_colors_in_vim](http://vim.wikia.com/wiki/256_colors_in_vim)

I think you may want to try another terminal, Aterm is very lightweight - [http://linuxreviews.org/software/x11-terms/aterm/](http://linuxreviews.org/software/x11-terms/aterm/)

Some prefer Eterm - [http://www.eterm.org/docs/view.php?doc=man](http://www.eterm.org/docs/view.php?doc=man)

and of course there is Xterm - [http://mkaz.com/solog/system/xterm-colors.html](http://mkaz.com/solog/system/xterm-colors.html)

Rodney

---

### Post by charnley on 2012-01-29
Thanks for the answer. 

Ended up installing gnome-terminal, so i could change the colour theme.

Too bad the colours is unreadable in lxterminal. I normally do not use a lot of time on choosing a colour : )

---

### Post by itcotbtoemik on 2012-01-29
> **Rodney9 said:**
> Marty Jack from LXDE Org [http://forum.lxde.org]("http://forum.lxde.org/viewtopic.php?t=1478&f=26")

and of course there is Xterm - [http://mkaz.com/solog/system/xterm-colors.html](http://mkaz.com/solog/system/xterm-colors.html)

Rodney

The "xterm-colors" page seems to imply that colors have to be names from rgb.txt
That is not correct, since colors can be specified as hexadecimal triples (as in
the app-defaults file for xterm).  Some applications may require names.

---

