---
title: "How can I change the terminal used in Nautilus &gt; Open in Terminal?"
date: 2024-02-24
forum: Desktop Environments
---

### Post by Paddy Landau on 2024-02-24
I have installed the newly-available [Warp terminal]("https://www.warp.dev/") for Linux, and I'm most impressed by it.

I am shocked, though, at how hard it is to change the default terminal in Ubuntu! It's ridiculous.

I managed to change the default terminal used with Ctrl+T as follows:
```
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/warp-terminal 50
sudo update-alternatives --config x-terminal-emulator
```
But, I cannot figure out how to change the terminal used in Nautilus (right-click > Open in Terminal)! Everything that I've tried has failed. Most instructions on the internet appear to be badly out of date, or want me to uninstall gnome-terminal (which I don't want to do).

I'm trying to install [nautilus-open-any-terminal]("https://github.com/Stunkymonkey/nautilus-open-any-terminal"), but the "make" command fails:
```
make[1]: msgfmt: No such file or directory
```
What can you advise, please?

---

### Post by &amp;KyT$0P# on 2024-02-24
> **Paddy Landau said:**
> I'm trying to install [nautilus-open-any-terminal]("https://github.com/Stunkymonkey/nautilus-open-any-terminal"), but the "make" command fails:
```
make[1]: msgfmt: No such file or directory
```
What can you advise, please?

For errors like this you can [search Ubuntu packages for the filename]("https://packages.ubuntu.com/#search_contents"), which [in this case suggests]("https://packages.ubuntu.com/search?searchon=contents&keywords=msgfmt&mode=exactfilename&suite=jammy&arch=any") you maybe able to resolve that error by installing [FONT=Courier New]gettext[/FONT] ?

---

### Post by Paddy Landau on 2024-02-24
> **halogen2 said:**
> For errors like this you can [search Ubuntu packages for the filename]("https://packages.ubuntu.com/#search_contents"), which [in this case suggests]("https://packages.ubuntu.com/search?searchon=contents&keywords=msgfmt&mode=exactfilename&suite=jammy&arch=any") you maybe able to resolve that error by installing [FONT=Courier New]gettext[/FONT] ?
That's a great resource, thank you! I installed [FONT=courier new]gettext[/FONT], and the [FONT=courier new]make[/FONT] command worked.

Unfortunately, the next required command failed:
```
**$ make install schema**
install -Dm644 nautilus_open_any_terminal/nautilus_open_any_terminal.py -t /home/paddy/.local/share/nautilus-python/extensions
make -C nautilus_open_any_terminal/locale install
make[1]: Entering directory '/home/paddy/NoBackup/nautilus-open-any-terminal/nautilus_open_any_terminal/locale'
install -Dm644 de.mo /home/paddy/.local/share/locale/de/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 es.mo /home/paddy/.local/share/locale/es/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 fr.mo /home/paddy/.local/share/locale/fr/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 pl.mo /home/paddy/.local/share/locale/pl/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 pt_BR.mo /home/paddy/.local/share/locale/pt_BR/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 ru.mo /home/paddy/.local/share/locale/ru/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 sw.mo /home/paddy/.local/share/locale/sw/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 tr.mo /home/paddy/.local/share/locale/tr/LC_MESSAGES/nautilus-open-any-terminal.mo; install -Dm644 zh_CN.mo /home/paddy/.local/share/locale/zh_CN/LC_MESSAGES/nautilus-open-any-terminal.mo;
install: cannot stat 'de.mo': No such file or directory
install: cannot stat 'es.mo': No such file or directory
install: cannot stat 'fr.mo': No such file or directory
install: cannot stat 'pl.mo': No such file or directory
install: cannot stat 'pt_BR.mo': No such file or directory
install: cannot stat 'ru.mo': No such file or directory
install: cannot stat 'sw.mo': No such file or directory
install: cannot stat 'tr.mo': No such file or directory
install: cannot stat 'zh_CN.mo': No such file or directory
make[1]: *** [Makefile:14: install] Error 1
make[1]: Leaving directory '/home/paddy/NoBackup/nautilus-open-any-terminal/nautilus_open_any_terminal/locale'
make: *** [Makefile:23: install] Error 2
```
I only ever compile from source when following instructions, so unfortunately I have no clue how to proceed with this. It's obvious that I'm missing a set of ".mo" files, but where would they come from?

This is so frustrating!

---

### Post by Holger_Gehrke on 2024-02-24
*.mo is gettext's binary format for message catalogs. They are created from *.po files (human readable text files with a specific structure) using 'msgfmt' which should be part of the gettext package. If I look on github in [https://github.com/Stunkymonkey/nautilus-open-any-terminal/tree/master/nautilus_open_any_terminal/locale/](https://github.com/Stunkymonkey/nautilus-open-any-terminal/tree/master/nautilus_open_any_terminal/locale/) I see {de,es,fr,pl,pt_BR,ru,sw,tr,zh_CN}.po, so if you 'git clone'd the project you should have the *.mo files if msgfmt was executed by make. You could try changing to the 'locale' directory and running 'make clean; make all', that should remove any debris and recompile the message catalogs.

Holger

---

### Post by Paddy Landau on 2024-02-25
> **Holger_Gehrke said:**
> You could try … running 'make clean; make all'
I figured that perhaps it would be better to just start again, and curiously enough, this time it worked perfectly!

So, thank you!

Curiously, after completing the instructions for nautilus-open-any-terminal, Nautilus now has three terminal entries in its right-click menu:

[LIST=1]
[*]*Open in Terminal*. This opens in gnome-terminal.
[*]*Open warp Here*. This opens in Warp terminal.
[*]Duplicate of 2.
[/LIST]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293428&stc=1[/IMG]
As you can see, Warp is duplicated. Both of those entries work. I'll live with it.

---

