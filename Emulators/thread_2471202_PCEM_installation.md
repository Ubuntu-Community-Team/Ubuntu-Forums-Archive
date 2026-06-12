---
title: "PCEM installation"
date: 2022-01-23
forum: Emulators
---

### Post by demonenero84 on 2022-01-23
I wanted to install PCEM but I need to install these dependencies :
SDL2
wxWidgets 3.x
OpenAL
CMake
Ninja (Recommended, but you can use a Makefile generator if you prefer)

any suggestions?
thanks in advance

---

### Post by schragge on 2022-01-23
The names of the packages in Ubuntu are:

SDL2: **libsdl2-dev**
wxWidgets: **libwxgtk3.0-gtk3-dev**
OpenAL: **libopenal-dev**
CMake: **cmake**
Ninja: **ninja-build**

---

### Post by demonenero84 on 2022-01-24
thanks a lot, just one more question, how do I know the name of an ubuntu package of a specific library ?

---

### Post by schragge on 2022-01-24
Good question. Compared to other distributions, Debian is notorious in changing package names from their upstream forms in order to comply to [Debian policy]("https://www.debian.org/doc/debian-policy"). This brings advantages as well as disadvantages. Debian packages are much more consistently named (e.g. names of all library packages start with **lib**). OTOH, the Debian names often differ from what is specified in upstream documentation. All this applies to Ubuntu and other Debian derivatives because they follow Debian naming conventions.

Quoting from Debian policy, [5.6.1. Source]("https://www.debian.org/doc/debian-policy/ch-controlfields.html#source"):
> Package names (both source and binary, see [Package]("https://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-package")) must consist only of lower case letters (a-z), digits (0-9), plus (+) and minus (-) signs, and periods (.). They must be at least two characters long and must start with an alphanumeric character.

Now, from [8.1. Run-time shared libraries]("https://www.debian.org/doc/debian-policy/ch-sharedlibs.html#run-time-shared-libraries"):
> Normally, the run-time shared library and its SONAME symlink should be placed in a package named libraryname*soversion*, where *soversion* is the version number in the SONAME of the shared library. Alternatively, if it would be confusing to directly append *soversion* to libraryname (if, for example, libraryname itself ends in a number), you should use libraryname-*soversion* instead.
The latter probably sounds confusing to you. As a matter of fact, if you often build from source, you'll get the hang of it pretty quickly.

To find out the name of a package, I find **apt-cache pkgnames** very useful. Actually, I have an alias for it
```
[COLOR=green]$[/COLOR] alias acn[COLOR=green]
alias acn='apt-cache pkgnames'[/COLOR]
```

So, back to your question. First, as I said all library packages start in **lib**. Next, headers and symlinks needed to link against a library when building from source are in **-dev** packages.
```
[COLOR=green]$[/COLOR] acn libsdl2|grep dev$[COLOR=green]
libsdl2-mixer-dev
libsdl2-image-dev
libsdl2-gfx-dev
libsdl2-dev
libsdl2-ttf-dev
libsdl2-net-dev[/COLOR]
```
```
[COLOR=green]$[/COLOR] acn libopenal|grep dev$[COLOR=green]
libopenal-dev[/COLOR]
```
```
[COLOR=green]$[/COLOR] acn ninja[COLOR=green]
ninja-build[/COLOR]
```
Finding the package for **wxWidgets** is a bit more involved. If **acn** doesn't give me any results or they're not immediately obvious, I use **apt-cache search** (aliased to **acs**):
```
[COLOR=green]$[/COLOR] alias acs[COLOR=green]
alias acs='apt-cache search'[/COLOR]
```
```
[COLOR=green]$[/COLOR] acs wxWidgets dev|grep ^lib[COLOR=green]
libwxbase3.0-dev - wxBase library (development) - non-GUI support classes of wxWidgets toolkit
libwxgtk-media3.0-gtk3-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK 3 media library development)
libwxgtk-webview3.0-gtk3-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK 3 webview library development)
libwxgtk3.0-gtk3-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK 3 development)
libwxsqlite3-3.0-dev - Development files for wxSQLite3
libwxsvg-dev - Development files for wxSVG[/COLOR]
```
The description usually will give you a clue. If you are not sure which one of the displayed packages you need then just install all of them.

Sometimes, rather than building from scratch you just want to build a newer version of a package that is already present in Ubuntu. In this case, use **apt build-dep <package_name>** to install its dependencies.

---

### Post by demonenero84 on 2022-01-24
thanks a lot, very interesting but I need some time to "digest" these tricks :)

---

