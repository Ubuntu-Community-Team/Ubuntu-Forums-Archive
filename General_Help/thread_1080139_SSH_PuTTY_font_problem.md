---
title: "SSH PuTTY font problem"
date: 2009-02-25
forum: General Help
---

### Post by cobrietti on 2009-02-25
Hi,
I'm Bolo from Poland. I have a problem with Polish fonts on my Ubuntu server. I have Ubuntu 8.10 server with Polish settings( fonts, etc). When I use ssh Putty I am getting the announcement (e.g):
[B]bolo@srv-lgwwa:~$ sudo apt-get install apache2
[sudo] password for bolo:
Czytanie list pakiet&#258;&#322;w... Gotowe
Budowanie drzewa zale&#313;&#378;no&#313;i
Odczyt informacji o stanie... Gotowe
NastÄpujÄ
ce pakiety zosta&#313;y zainstalowane automatycznie i nie sÄ
 ju&#313;&#378; wiÄcej wymagane:
  debhelper intltool-debian po-debconf libmail-sendmail-perl gettext html2text libsys-hostname-long-perl
Aby je usunÄ
Ä nale&#313;&#378;y u&#313;&#378;yÄ "apt-get autoremove".
ZostanÄ
 zainstalowane nastÄpujÄ
ce dodatkowe pakiety:
  apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libmysqlclient15off libpq5 mysql-common openssl-blacklist ssl-cert
Sugerowane pakiety:
  apache2-doc apache2-suexec apache2-suexec-custom
ZostanÄ
 zainstalowane nastÄpujÄ
ce NOWE pakiety:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libmysqlclient15off libpq5 mysql-common openssl-blacklist ssl-cert
0 aktualizowanych, 11 nowo instalowanych, 0 usuwanych i 59 nieaktualizowanych.
Konieczne pobranie 9935kB archiw&#258;&#322;w.
Po tej operacji zostanie dodatkowo u&#313;&#378;yte 22,9MB miejsca na dysku.
KontynuowaÄ [T/n]? T
Przerwane.
bolo@srv-lgwwa:~$
[/B]
When I am choosing **T** the entire operation is staying finished? WHY :(

---

### Post by geirha on 2009-02-25
Looks like putty is using the wrong encoding. Look through all the options of putty and make sure it uses UTF-8 and not ISO-8859-1 or something like that.

---

