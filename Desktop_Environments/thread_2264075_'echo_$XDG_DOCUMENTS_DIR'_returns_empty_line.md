---
title: "'echo $XDG_DOCUMENTS_DIR' returns empty line"
date: 2015-02-05
forum: Desktop Environments
---

### Post by kebabbaro on 2015-02-05
Hello,
though in ~/.local/user-dirs.dirs there is the line:
```
XDG_DOCUMENTS_DIR="/media/dati/Documenti"
```

when I open a terminal and enter 
```
echo $XDG_DOCUMENTS_DIR
```
the command returns an empty line

why is that? why does the terminal not return the value "/media/dati/Documenti"? 
does that imply that every other program sees an empty line too when given the $XDG_DOCUMENTS_DIR parameter?


by the way if I enter
```
echo $XDG_DOCUMENTS_DIR/games
```
the command returns only
```
/games
```
with no leading spaces before it

---

### Post by CantankRus on 2015-02-05
What makes you think the entries in user-dirs.dirs will show as variables in the terminal?
```
echo $XDG_DOCUMENTS_DIR
```
returns an empty line because  $XDG_DOCUMENTS_DIR returns nothing but echo still outputs the trailing newline.
Get the same result if you just run "echo" by itself.

From man echo...
> Echo the STRING(s) to standard output.

**-n**
do not output the trailing newline

enter "echo $XDG" in terminal and press tab a few times to show available auto-completion...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **echo $XDG_**
$XDG_CONFIG_DIRS       $XDG_GREETER_DATA_DIR  $XDG_SEAT              $XDG_SESSION_PATH
$XDG_CURRENT_DESKTOP   $XDG_MENU_PREFIX       $XDG_SEAT_PATH         $XDG_VTNR
$XDG_DATA_DIRS         $XDG_RUNTIME_DIR       $XDG_SESSION_ID
```

---

