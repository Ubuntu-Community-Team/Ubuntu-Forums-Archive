---
title: "How to compile Dungeon Crawl Stone Soup v0.4.3 on Ubuntu"
date: 2008-11-27
forum: Gaming &amp; Leisure
---

### Post by Inquisitorthemad on 2008-11-27
I tried to compile my favourite roguelike, it didn't work. Sorted through the first few obvious problems - didn't solve the problem. Currently I get the following errors when making the attempt:

```
g++  -Iutil -I. -Iutil/lua/src -Iutil/sqlite -I/usr/include/ncurses -Wall -Wwrite-strings -Wshadow -pedantic -Wuninitialized -fsigned-char -DUNIX  -DCLUA_BINDINGS -O2  -c libunix.cc
libunix.cc:74:24: error: curses.h: No such file or directory
libunix.cc:82: error: ‘COLOR_PAIR’ was not declared in this scope
libunix.cc:86: error: ‘WINDOW’ was not declared in this scope
libunix.cc:86: error: ‘w’ was not declared in this scope
libunix.cc:86: error: expected primary-expression before ‘const’
libunix.cc:86: error: initializer expression list treated as compound expression
libunix.cc: In function ‘unsigned int convert_to_curses_attr(int)’:
libunix.cc:94: error: ‘A_STANDOUT’ was not declared in this scope
libunix.cc:95: error: ‘A_BOLD’ was not declared in this scope
libunix.cc:96: error: ‘A_BLINK’ was not declared in this scope
libunix.cc:97: error: ‘A_UNDERLINE’ was not declared in this scope
libunix.cc:98: error: ‘A_REVERSE’ was not declared in this scope
libunix.cc:99: error: ‘A_DIM’ was not declared in this scope
libunix.cc:100: error: ‘A_NORMAL’ was not declared in this scope
libunix.cc: In function ‘short int translate_colour(short int)’:
libunix.cc:115: error: ‘COLOR_BLACK’ was not declared in this scope
libunix.cc:117: error: ‘COLOR_BLUE’ was not declared in this scope
libunix.cc:119: error: ‘COLOR_GREEN’ was not declared in this scope
libunix.cc:121: error: ‘COLOR_CYAN’ was not declared in this scope
libunix.cc:123: error: ‘COLOR_RED’ was not declared in this scope
libunix.cc:125: error: ‘COLOR_MAGENTA’ was not declared in this scope
libunix.cc:127: error: ‘COLOR_YELLOW’ was not declared in this scope
libunix.cc:129: error: ‘COLOR_WHITE’ was not declared in this scope
libunix.cc: In function ‘void setup_colour_pairs()’:
libunix.cc:160: error: ‘init_pair’ was not declared in this scope
libunix.cc:164: error: ‘COLOR_BLACK’ was not declared in this scope
libunix.cc:164: error: ‘init_pair’ was not declared in this scope
libunix.cc: In function ‘int getch_ck()’:
libunix.cc:307: error: ‘KEY_BACKSPACE’ was not declared in this scope
libunix.cc:308: error: ‘KEY_DC’ was not declared in this scope
libunix.cc:309: error: ‘KEY_HOME’ was not declared in this scope
libunix.cc:310: error: ‘KEY_PPAGE’ was not declared in this scope
libunix.cc:311: error: ‘KEY_END’ was not declared in this scope
libunix.cc:312: error: ‘KEY_NPAGE’ was not declared in this scope
libunix.cc:313: error: ‘KEY_UP’ was not declared in this scope
libunix.cc:314: error: ‘KEY_DOWN’ was not declared in this scope
libunix.cc:315: error: ‘KEY_LEFT’ was not declared in this scope
libunix.cc:316: error: ‘KEY_RIGHT’ was not declared in this scope
libunix.cc: At global scope:
libunix.cc:358: error: expected initializer before ‘*’ token
libunix.cc: In function ‘void setup_message_window()’:
libunix.cc:361: error: ‘Message_Window’ was not declared in this scope
libunix.cc:362: error: ‘newwin’ was not declared in this scope
libunix.cc:372: error: ‘scrollok’ was not declared in this scope
libunix.cc:373: error: ‘idlok’ was not declared in this scope
libunix.cc: In function ‘void clear_message_window()’:
libunix.cc:384: error: ‘Message_Window’ was not declared in this scope
libunix.cc:384: error: ‘wattrset’ was not declared in this scope
libunix.cc:385: error: ‘werase’ was not declared in this scope
libunix.cc:386: error: ‘wrefresh’ was not declared in this scope
libunix.cc: In function ‘void message_out(int, int, const char*, int, bool)’:
libunix.cc:392: error: ‘Message_Window’ was not declared in this scope
libunix.cc:392: error: ‘wattrset’ was not declared in this scope
libunix.cc:399: error: ‘wmove’ was not declared in this scope
libunix.cc:400: error: ‘waddstr_with_altcharset’ cannot be used as a function
libunix.cc:405: error: ‘getyx’ was not declared in this scope
libunix.cc:406: error: ‘scroll’ was not declared in this scope
libunix.cc:414: error: ‘getyx’ was not declared in this scope
libunix.cc:415: error: ‘move’ was not declared in this scope
libunix.cc:418: error: ‘wrefresh’ was not declared in this scope
libunix.cc: In function ‘void unixcurses_startup()’:
libunix.cc:442: error: ‘initscr’ was not declared in this scope
libunix.cc:443: error: ‘raw’ was not declared in this scope
libunix.cc:446: error: ‘nonl’ was not declared in this scope
libunix.cc:447: error: ‘stdscr’ was not declared in this scope
libunix.cc:447: error: ‘FALSE’ was not declared in this scope
libunix.cc:447: error: ‘intrflush’ was not declared in this scope
libunix.cc:449: error: ‘TRUE’ was not declared in this scope
libunix.cc:449: error: ‘keypad’ was not declared in this scope
libunix.cc:452: error: ‘ESCDELAY’ was not declared in this scope
libunix.cc:456: error: ‘meta’ was not declared in this scope
libunix.cc:457: error: ‘start_color’ was not declared in this scope
libunix.cc:460: error: ‘scrollok’ was not declared in this scope
libunix.cc: In function ‘void unixcurses_shutdown()’:
libunix.cc:470: error: ‘Message_Window’ was not declared in this scope
libunix.cc:472: error: ‘delwin’ was not declared in this scope
libunix.cc:477: error: ‘endwin’ was not declared in this scope
libunix.cc: In function ‘int itoa(int, char*, int)’:
libunix.cc:535: error: ‘OK’ was not declared in this scope
libunix.cc: In function ‘int cprintf(const char*, ...)’:
libunix.cc:548: error: ‘stdscr’ was not declared in this scope
libunix.cc:548: error: ‘waddstr_with_altcharset’ cannot be used as a function
libunix.cc:549: error: ‘refresh’ was not declared in this scope
libunix.cc: At global scope:
libunix.cc:556: error: redefinition of ‘int waddstr_with_altcharset’
libunix.cc:86: error: ‘int waddstr_with_altcharset’ previously defined here
libunix.cc:556: error: ‘WINDOW’ was not declared in this scope
libunix.cc:556: error: ‘w’ was not declared in this scope
libunix.cc:556: error: expected primary-expression before ‘const’
libunix.cc:82: warning: ‘Current_Colour’ defined but not used
libunix.cc:84: warning: ‘int curs_fg_attr(int)’ declared ‘static’ but never defined
libunix.cc:85: warning: ‘int curs_bg_attr(int)’ declared ‘static’ but never defined
libunix.cc:88: warning: ‘cursor_is_enabled’ defined but not used
libunix.cc:90: warning: ‘unsigned int convert_to_curses_attr(int)’ defined but not used
libunix.cc:110: warning: ‘short int translate_colour(short int)’ defined but not used
make[1]: *** [libunix.o] Error 1
make[1]: Leaving directory `/home/user/Desktop/stone_soup-0.4.3-src/source'
make: *** [all] Error 2

```

I'm aware that this might be an issue with Crawl Stone Soup itself, but given my inexperience with compiling source I'm not about to jump to that conclusion.

---

### Post by binbash on 2008-11-27
libunix.cc:74:24: error: curses.h: No such file or directory

It is something about ncurses,can you provide me the download link of the code or website of the game.

---

### Post by Inquisitorthemad on 2008-11-27
The homepage is here: [http://crawl-ref.sourceforge.net/]("http://crawl-ref.sourceforge.net/")

---

### Post by binbash on 2008-11-27
install deps then make clean and try to give the make command again.From readme : 

'GNU gcc and g++, GNU make, libncurses or libcurses. You need the
development headers for ncurses - they may not be installed by default
on some Unixes.                                                       

flex and bison are optional but highly recommended. Recent versions of
byacc are also fine (edit your makefile appropriately).  '

Those are dps.Dont forget development headers for ncurses.I guess that was your problem

---

### Post by Perfect Storm on 2008-11-27
Guide; [http://gaming.gwos.org/doku.php/guides:64bit:dungeon_crawl_stone_soup](http://gaming.gwos.org/doku.php/guides:64bit:dungeon_crawl_stone_soup)

---

### Post by Inquisitorthemad on 2008-11-28
I followed the guide, installed things as needed, compiled the source, moved it to appropriate directory etc. but the launcher does nothing when triggered. Absolutely nothing.

Thanks for the link to it though.

---

### Post by Perfect Storm on 2008-11-28
I'll take a look at its launcher guide when I get home from work.

---

### Post by Inquisitorthemad on 2009-06-13
Bumping this because I'm trying to install Crawl 0.5, and despite apparently having all the prerequisites for it, the following happens and stops the installation...

```
make[1]: *** No rule to make target `/usr/include/SDL/SDL_main.h', needed by `acr.o'. Stop.
make[1]: Leaving directory `/home/matthew/Desktop/stone_soup-0.5-src/source'
make: *** [install] Error 2
```

This message is, sadly, about as helpful as the Blue Screen of Death (at least to me).

For reference, I am running Ubuntu 8.10 still.

---

### Post by n0_mad on 2009-06-16
If you did not know it runs perfectly under wine=)

---

### Post by pendletone on 2009-09-21
@Inquisitorthemad:
Had the exact error messages you had on your first post. Most likely you haven't installed the development headers for libncurses.

```
sudo apt-get install libncurses5-dev
```

---

### Post by Allwynd on 2010-03-10
i have the dumbest question.. i have the game via PlayDeb, seems interesting, but how do i make it windowed or at least quit the game without restarting the whole machine?

---

