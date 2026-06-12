---
title: "The problem with conky-colors"
date: 2011-03-21
forum: Desktop Environments
---

### Post by yeketaz on 2011-03-21
When I type the "make" command,I see this output:
```
cc -Wall -std=c99    src/conky-colors.c src/conkycover.c src/conkyforecast.c src/conkyplayer.c src/conkyrc_cairo.c src/conkyrc_ring.c src/conkyrc_board.c src/conkyrc_default.c src/coverposition.c src/finddir.c src/help.c src/options.c src/photoposition.c src/themes.c src/translations.c src/variables.c src/confinstall.c src/utils.c src/initialize.c   -o conky-colors
src/options.c: In function ‘options’:
src/options.c:239: warning: format not a string literal and no format arguments
src/options.c:239: warning: format not a string literal and no format arguments
src/themes.c: In function ‘themes’:
src/themes.c:185: warning: format not a string literal and no format arguments
src/themes.c:185: warning: format not a string literal and no format arguments
```

---

### Post by nkrypt on 2012-02-25
I get the exact same message when I type make :(

---

