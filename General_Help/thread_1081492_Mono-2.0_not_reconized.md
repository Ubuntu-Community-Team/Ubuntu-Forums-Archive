---
title: "Mono-2.0 not reconized"
date: 2009-02-26
forum: General Help
---

### Post by drsandyrae on 2009-02-26
I have installed mono-2.x. 
I attemp to install monodevelop 2.0 beta 1:

[LIST]
[*]I get an error saying I need to install mono 2.0 or greater.
[*]When I go to the mono project and install the ubuntu intall: apt... it says 2.x is already installed.
[*]When running ./configure in the monodevelop I get the above error.
[/LIST]
So, what am I doing wrong?

I thought about installing SuSe 11.1 but don't know how to setup my partitions.

just updated profile: Using ubuntu Intrepid.

Sandy

---

### Post by smani on 2009-02-26
Did you also install the respective -devel packages? i.e. mono-2.0-devel

---

### Post by directhex on 2009-02-26
There is perpetual confusion about version numbers.

MONO version numbers are not the same as .NET version numbers

Mono package NAMES reflect the .NET VERSION

libmono-foo2.0-cil is a .NET 2.0-compatible library, but that doesn't mean it's Mono 2.0 (we've had 2.0 classlib packages since Mono 1.1.8ish)

Only Jaunty has Mono >=2.0

---

