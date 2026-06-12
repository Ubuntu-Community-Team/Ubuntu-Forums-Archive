---
title: "Text editor for xubuntu?"
date: 2007-02-23
forum: Desktop Environments
---

### Post by graabein on 2007-02-23
Hi does anyone know of a lightweight GUI text editor for Xfce/Xubuntu that is better than mousepad? I want syntax highlighting (for XML at least) and I don't want to install hundreds of megs of GNOME libraries. 

I looked at Bluefish and Scribes but both depend on GNOME. Nano is CLI and I didn't get syntax highlighting for XML even though I tried with the disable/enable highlight function.

---

### Post by picpak on 2007-02-23
For nano, this is my .nanorc:

```

# Display cursor position
set const

# Disable word wrap
set nowrap

# Use smooth scrolling
set smooth

# Allow suspend
set suspend

# HTML syntax highlighting
##########################
syntax "HTML" "\.html$"
color blue start="<" end=">"
color red "&[^; 	]*;"


# Generic conf/rc/sh file syntax highlighting
#############################################
syntax "conf/rc/sh" "conf$|rc$|sh$"
color white ".+"
color green "^#.*"


# .nanorc syntax highlighting
#############################
syntax "nanorc" "[\.]*nanorc$"
color white "^ *(set|unset).*$"
color cyan "^ *(set|unset) (autoindent|backup|const|cut|fill|keypad|multibuffer|noconvert|nofollow|nohelp|nowrap|operatingdir|preserve|quotestr|regexp|smooth|speller|suspend|tabsize|tempfile|historylog|view)"
color brightwhite "^ *syntax [^ ]*"
color brightblue "^ *set\>" "^ *unset\>" "^ *syntax\>"
color white "^ *color\>.*"
color yellow "^ *color (bright)?(black|blue|cyan|green|magenta|red|white|yellow)\>"
color magenta "^ *color\>"
color green "^#.*$"


# sources.list syntax highlighting
##################################
syntax "sources.list" "\.list$"
color brightred "^deb"
color brightblue "http.+"
color brightmagenta "(edgy.+)"
color brightwhite "(main|restricted|universe|multiverse|free|non-free|xfce-4-4-0|3v1n0)"
color brightgreen "^#.*"


# menu.lst syntax highlighting
###############################
syntax "menu.lst" "menu\.lst"
color cyan "(^default.+|^timeout.+)"
color red "^title.+"
color yellow "(initrd.+|kernel.+|root.+)"
color green "^#.*"
```

It does syntax highlighting for me.

---

### Post by kerry_s on 2007-02-23
I hear nedit is good. You can also just add nano to your right click custom actions in thunar, that way you can select it just when you need it, with picpak's .nanorc you don't even have to install anything. :)

---

### Post by graabein on 2007-02-24
Thanks for your replies. **nedit** crashed on me after install. Don't know how to debug this...

```
$ sudo apt-get install nedit
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lesstif2
Suggested packages:
  csh
The following NEW packages will be installed:
  lesstif2 nedit
0 upgraded, 2 newly installed, 0 to remove and 70 not upgraded.
Need to get 1321kB of archives.
After unpacking 3125kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://no.archive.ubuntu.com edgy/universe lesstif2 1:0.94.4-2 [584kB]
Get:2 http://no.archive.ubuntu.com edgy/universe nedit 1:5.5-1ubuntu1 [737kB]
Fetched 1321kB in 7s (185kB/s)                                                                                              
Selecting previously deselected package lesstif2.
(Reading database ... 87919 files and directories currently installed.)
Unpacking lesstif2 (from .../lesstif2_1%3a0.94.4-2_i386.deb) ...
Selecting previously deselected package nedit.
Unpacking nedit (from .../nedit_1%3a5.5-1ubuntu1_i386.deb) ...
Setting up lesstif2 (0.94.4-2) ...

Setting up nedit (5.5-1ubuntu1) ...

$ nedit
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  372
  Current serial number in output stream:  382
```

I'll see if I can edit *.nanorc* to include highlighting for XML.

---

### Post by picpak on 2007-02-24
It's been done:

[http://gentoo-wiki.com/TIP_Nano_Context_Highlighting#xml](http://gentoo-wiki.com/TIP_Nano_Context_Highlighting#xml)

---

### Post by antenna on 2007-02-24
Medit, Scite, Geany, in order of complexity.

---

### Post by sgraham on 2007-02-24
Scite should work fine with XFCE.  I think it is a fine editor, a real workhorse and you can tweak it to your hearts desire.

---

### Post by graabein on 2007-02-25
Off topic: antenna that's a great album by Godspeed You Black Emperor! Just listened to it on a plane ride last week. Been too long.

And I'll give **scite** a chance.

---

### Post by afx on 2007-02-25
Hi everyone!
I also wanted a simple text editor w/ color syntaxing.
I installed nedit but got the same error like graabein.

I decided to go with nano... Except, there is a problem:
there is no .nanorc in my home dir.
I created one and added the syntaxing for c but it seems
that it does nothing... I need highlighting!!! Help!

---

### Post by kerry_s on 2007-02-25
The best way to use nano, is to go into /etc/nanorc and set that up to your needs or copy that to your home, you'll find that it has all the settings, there just commented out, you just need to uncomment them. I also added some i found to /usr/share/nano/* . Attached is my nanorc and the extra *.nanorc setups->

---

### Post by ebullient on 2007-11-13
> **afx said:**
> Hi everyone!
I also wanted a simple text editor w/ color syntaxing.
I installed nedit but got the same error like graabein.

I decided to go with nano... Except, there is a problem:
there is no .nanorc in my home dir.
I created one and added the syntaxing for c but it seems
that it does nothing... I need highlighting!!! Help!

and also for the OP


Why not use vim?

```
sudo apt-get install vim
vimtutor
```

When you're reasonably comfy with it edit your .vimrc:
```
vim .vimrc
```
in your home directory and add the line:
```
syntax on
```
and you're done.  Other options that are useful for .vimrc:
```
set bs=2
set ts=4
set nocompatible
```
Set bs=2 causes the backspace to behave in a way that may be more intuitive.  Set ts=4 sets your tab stop to 4, that's what I use but you may have a different preference.  Set nocompatible enables a mode where files aren't saved in a version compatible with much older versions of vi/vim, you really shouldn't need this.

Anyway, I get syntax highlighting even in the most obscure config files.  Good stuff.

---

### Post by RedSquirrel on 2007-11-13
There is also GVIM (package: vim-gtk), which is vim with a graphical interface (GTK 2).

---

### Post by moon2js on 2008-02-21
@ebullient: Thanks! That's exactly what I was looking for. Now I can ssh in with putty from a silly windows computer and finally get some coding done without getting a headache. I've been looking for reason to brush up on and get good with vi, and this may be it.

---

