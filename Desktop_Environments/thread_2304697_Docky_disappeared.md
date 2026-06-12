---
title: "Docky disappeared"
date: 2015-11-29
forum: Desktop Environments
---

### Post by Przemysaw_Skiba on 2015-11-29
Hello,

When I try to launch Docky in terminal I get the message:/usr/bin/docky: 14: exec: mono: not found. How can I fix it? Thanks and regards.

---

### Post by ajgreeny on 2015-11-29
Docky depends on several libmono packages that appear to be missing on your system.

Try re-installing docky which should then add back in any packages that are missing.

---

### Post by Przemysaw_Skiba on 2015-11-29
I have already reinstalled Docky but it didn't help.

---

### Post by buzzingrobot on 2015-11-29
How are you installing Docky? It is in the repos, as are the Mono dependencies.

> When I try to launch Docky in terminal I get the message:/usr/bin/docky: 14: exec: mono: not found...

Does Docky behave normally otherwise, when you *don't* try to launch it in a terminal? Or, is it not launching and you are troubleshoooting?

---

### Post by Przemysaw_Skiba on 2015-11-29
From Ubuntu Software Center. Docky isn't launching at all (nothing happens).

---

### Post by buzzingrobot on 2015-11-29
Open a terminal and try:

> sudo apt-get install --reinstall docky

If that fails, post the output, between quote tags.

---

### Post by Przemysaw_Skiba on 2015-11-30
It didn't help.

> Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
0 aktualizowanych, 0 nowo instalowanych, 1 ponownie instalowanych, 0 usuwanych i 0 nieaktualizowanych.
Konieczne pobranie 0 B/606 kB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 0 B miejsca na dysku.
(Odczytywanie bazy danych ... 368817 plików i katalogów obecnie zainstalowanych.)
Preparing to unpack .../archives/docky_2.2.0-2_all.deb ...
Unpacking docky (2.2.0-2) over (2.2.0-2) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Konfigurowanie pakietu docky (2.2.0-2) ...


---

### Post by Przemysaw_Skiba on 2015-11-30
Huh, I've found something like this in the Terminal history:

> sudo rm -rf /usr/bin/mono /etc/mono /usr/lib/mono /usr/bin/X11/mono /usr/share/mono /usr/share/man/man1/mono.1.gz

I must have accidentally deleted mono.

---

### Post by ajgreeny on 2015-11-30
> **Przemysaw_Skiba said:**
> Huh, I've found something like this in the Terminal history:

> sudo rm -rf /usr/bin/mono /etc/mono /usr/lib/mono /usr/bin/X11/mono /usr/share/mono /usr/share/man/man1/mono.1.gz 

I must have accidentally deleted mono.
Wow!  How on earth did you manage to do that?  Presumably you were trying to do something related to mono at the time, but using rm -rf is a dangerous command when you are not too sure of what you're doing.

I presume you have now reinstalled all those mono packages that you will still have had installed, even though the executables and libraries had been removed.  If you have not done so already, do it now and see if docky works again.

---

### Post by Przemysaw_Skiba on 2015-12-01
How can I reinstall all mono packages? I have reinstalled mono-complete and received a message that it's already installed. I don't know if it's enough.

---

### Post by ajgreeny on 2015-12-01
I tend to use synaptic package manager as it is very flexible and would allow you to search for all the mono packages that are installed by simply searching (Name) for "mono" then reinstalling all of those you appear to have, but which you may have now broken with that **rm -rf** command.

You will have to install synaptic first as it is not a part of the default installation of most of the *ubuntu family any more, though I think it's still there in Lubuntu.

---

