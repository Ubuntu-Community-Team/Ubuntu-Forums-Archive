---
title: "how do open gnome applications from CLI"
date: 2013-02-17
forum: Desktop Environments
---

### Post by linuxnovice. on 2013-02-17
So I'm studying for my midterms, and I have a test where I will have to do everything from the CLI so I have been using nothing but the CLI mode (ctrl + alt + f12)

but I do need to use chrome and pdf viewer, how can I open them from the CLI?

---

### Post by Bashing-om on 2013-02-17
linuxnovice. Hi !

Type the name of the application you want to run in the cli;
a) The application must exist in the path environment, else the full path name must be employed.
b) If the application is a GUI application, then xserver must be running, else a text based alternative must be employed.
c) If it is desired for the terminal to remain resident, follow the application name with the ampersand "&".

I am sure there are other caveat's // but it is all in knowing how !
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)
in the search box enter the term "command line interface" -> much docs on this topic.

[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-02-17
```
google-chrome
evince
acroread
```

Most user programs are found in /usr/bin, so browse that directory for correct names.

Also use the search function:

```
apropos pdf
```

To find where a program is stored use the *which* command:

tgalati4@Mint14-Extensa ~/Desktop $ which evince
/usr/bin/evince
tgalati4@Mint14-Extensa ~/Desktop $ which firefox
/usr/bin/firefox

---

### Post by markbl on 2013-02-18
Just type "xdg-open <whatever>" to open the file or target in the preferred application for that target, i.e. "xdg-open file.pdf" will open the pdf file in your nominated pdf viewer, or "xdg-open ." will open nautilus for the current directory, etc.

I use xdg-open from the command line probably every day. Works in gnome, kde, etc.

---

