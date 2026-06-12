---
title: "how to change locales/languages?"
date: 2004-12-06
forum: Desktop Environments
---

### Post by burlap on 2004-12-06
**This is an amended version - some problems were solved but they produced other problems...** 

I have posted my problems with setting locale (see below, where I quote my original post) but after my system "rebooted" (when I turned my computer back on - I do not reboot Linux that often, except for occassional kernel updates) they seem to be fixed. That is: I can choose a language in GDM and I have the user interface I want. 
But:
[list]I cannot set LANG in the console - "LANG=es_ES foo" does not cause foo to be in Spanish;[/list]
[list]after I logged in with my original language again (Polish), some panel applets are still in Spanish (don't tell me it is going to change after I reboot, as it is not the way to do it);[/list]

Normally, I would not care about these small problems (applets), but I would like to recommend Ubuntu to my non-Linux-using friends (I thought about FC3, but it crashed  a lot during only one week of testing) and with flaws like that, they are not likely to use it for long...

> I went through wiki (the appropriate section on Everydayusage is missing) and forums (they are quite chaotic - development ideas on packages mixed with partial solutions), but my question remains: how to include other user interface languages? 

The first problem: 
I have Polish as my main (and only) language (pl_PL), but I need the interface also in Spanish (Spain). 

I ran

```
sudo dpkg-reconfigure locales
```
to generate different Spanish locales (all of them - es_ES.*encoding*)

However - if I choose Spanish from Language menu in gdm I get a message "there is no es_ES language, using system default" (rough translation from Polish) and GNOME starts in Polish. How to change it? 

Other related problem:

I got used to all-languages-in-one distros (redhat/fedora based) and sometimes I use LANG variable to run different programs in different languages. It does not work - whether I put simply LANG=en_US or LANG=en_US.UTF-8 (the same with Spanish).

If it helps, some listings:

```
/etc/environment

LANGUAGE="pl_PL:pl:en_GB:en"
LANG=pl_PL
```
```
$locale -a

C
en_GB
en_GB.iso88591
en_GB.utf8
en_US
en_US.iso88591
en_US.iso885915
en_US.utf8
es_ES
es_ES@euro
es_ES.iso88591
es_ES.iso885915@euro
es_ES.utf8
es_ES.utf8@euro
pl_PL
pl_PL.iso88592
polish
POSIX
spanish

```


Regards 
Rafa&#322; Próchniak

---

