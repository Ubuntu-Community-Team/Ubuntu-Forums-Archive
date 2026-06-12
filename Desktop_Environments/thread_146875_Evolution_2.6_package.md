---
title: "Evolution 2.6 package?"
date: 2006-03-19
forum: Desktop Environments
---

### Post by GrumpyBob on 2006-03-19
Is there an Evolution-2.6 package available somewhere for 5.10 Breezy?
I don't fancy compiling from source if Dapper will be along soon!

Robert

---

### Post by dermotti on 2006-03-19
Hmmm, its definatly in the dapper repos. Maybe you need to enable the universe?

---

### Post by GrumpyBob on 2006-03-19
Well, I'm running Breezy - is it wise to add Dapper repos to the sources.list?

Robert

---

### Post by dermotti on 2006-03-19
No it is not wise.

---

### Post by dermotti on 2006-03-19
hmmmm, do you have the universe enabled?

[http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.6.0-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.6.0-0ubuntu3_i386.deb)

---

### Post by GrumpyBob on 2006-03-19
What syntax would I use for that repo in sources.list?
I'm not familiar with the sources.list syntax.

Robert

---

### Post by VictorE on 2006-03-21
Assuming that one had enabled the universe, how would you get and install evolution 2.6?  i have tried the "add application" and the "synaptic package manager".  both only list the current, 2.4, version of evolution.

---

### Post by mxsteini on 2006-03-21
hmmmm, universe enabled.
evolution 2.6 not found.
@dermotti:
Your package couldn't be installed. Many dependecy-error under breezy:cry: :
 evolution hängt ab von libavahi-client3 (>= 0.6.0); aber:
  Paket libavahi-client3 bereitstellt, ist nicht installiert.
 evolution hängt ab von libavahi-common3 (>= 0.6.9); aber:
  Paket libavahi-common3 bereitstellt, ist nicht installiert.
 evolution hängt ab von libavahi-glib1 (>= 0.6.0); aber:
  Paket libavahi-glib1 bereitstellt, ist nicht installiert.
 evolution hängt ab von libbonobo2-0 (>= 2.13.0); aber:
  Version von libbonobo2-0 auf dem System ist 2.10.1-0ubuntu1.
 evolution hängt ab von libcairo2 (>= 1.0.2-2); aber:
  Version von libcairo2 auf dem System ist 1.0.2-0ubuntu1.
 evolution hängt ab von libcamel1.2-8 (>= 1.6.0); aber:
  Paket libcamel1.2-8 bereitstellt, ist nicht installiert.
 evolution hängt ab von libdbus-1-2 (>= 0.60); aber:
  Paket libdbus-1-2 bereitstellt, ist nicht installiert.
 evolution hängt ab von libdbus-glib-1-2 (>= 0.60); aber:
  Paket libdbus-glib-1-2 bereitstellt, ist nicht installiert.
 evolution hängt ab von libebook1.2-5 (>= 1.6.0); aber:
  Version von libebook1.2-5 auf dem System ist 1.4.1-0ubuntu3.
 evolution hängt ab von libecal1.2-3 (>= 1.6.0); aber:
  Version von libecal1.2-3 auf dem System ist 1.4.1-0ubuntu3.
 evolution hängt ab von libedataserver1.2-7 (>= 1.6.0); aber:
  Paket libedataserver1.2-7 bereitstellt, ist nicht installiert.
 evolution hängt ab von libedataserverui1.2-6 (>= 1.6.0); aber:
  Version von libedataserverui1.2-6 auf dem System ist 1.4.1-0ubuntu3.
 evolution hängt ab von libgcrypt11 (>= 1.2.2); aber:
  Version von libgcrypt11 auf dem System ist 1.2.1-3.
 evolution hängt ab von libglib2.0-0 (>= 2.9.3); aber:
  Version von libglib2.0-0 auf dem System ist 2.8.3-0ubuntu1.
 evolution hängt ab von libgnomeui-0 (>= 2.13.0); aber:
  Version von libgnomeui-0 auf dem System ist 2.12.0-0ubuntu1.
 evolution hängt ab von libgnomevfs2-0 (>= 2.13.92-0ubuntu4); aber:
  Version von libgnomevfs2-0 auf dem System ist 2.12.1-0ubuntu2.
 evolution hängt ab von libgnutls12 (>= 1.2.5); aber:
  Paket libgnutls12 bereitstellt, ist nicht installiert.
 evolution hängt ab von libgpg-error0 (>= 1.1); aber:
  Version von libgpg-error0 auf dem System ist 1.0-1.
 evolution hängt ab von libgtkhtml3.8-15 (>= 3.10.0); aber:
  Version von libgtkhtml3.8-15 auf dem System ist 3.8.1-0ubuntu1.
 evolution hängt ab von libkrb53 (>= 1.4.2); aber:
  Version von libkrb53 auf dem System ist 1.3.6-4.
 evolution hängt ab von libnotify1; aber:
  Paket libnotify1 bereitstellt, ist nicht installiert.
 evolution hängt ab von libpango1.0-0 (>= 1.12.0); aber:
  Version von libpango1.0-0 auf dem System ist 1.10.1-0ubuntu1.
 evolution hängt ab von libsoup2.2-8 (>= 2.2.91); aber:
  Version von libsoup2.2-8 auf dem System ist 2.2.6.1-0ubuntu1.
 evolution hängt ab von libtasn1-2 (>= 0.2.13); aber:
  Version von libtasn1-2 auf dem System ist 0.2.10-4.
 evolution hängt ab von libxml2 (>= 2.6.23); aber:
  Version von libxml2 auf dem System ist 2.6.21-0ubuntu1.
 evolution hängt ab von gconf2 (>= 2.12.1-4ubuntu1); aber:
  Version von gconf2 auf dem System ist 2.12.0-0ubuntu1.
 evolution hängt ab von evolution-data-server (>= 1.5.5); aber:
  Version von evolution-data-server auf dem System ist 1.4.1-0ubuntu3.

Sorry for the german-version.

Any ideas?

Michael

---

### Post by nocturn on 2006-03-21
Evolution 2.6 is a part of Gnome 2.14, which is only available in Dapper.

To get it, you will have to wait for Dapper (or upgrade to the current development release).

---

