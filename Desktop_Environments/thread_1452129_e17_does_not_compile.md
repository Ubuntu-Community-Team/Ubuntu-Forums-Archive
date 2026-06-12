---
title: "e17 does not compile"
date: 2010-04-11
forum: Desktop Environments
---

### Post by zaptec on 2010-04-11
Hello, I'm  new on this forum :) but not on ubuntu ;).

This after-noon, I tried to compile e17 but I got the following line :

```

louis@zaptec:~$ cd /home/louis/Téléchargements
louis@zaptec:~/Téléchargements$ ./easy_e17.sh -i
bash: ./easy_e17.sh: Permition Denied
louis@zaptec:~/Téléchargements$ 

```It's don't work in root either.

Any solution please?

Thank.

---

### Post by kellemes on 2010-04-11
Is this helping?
[http://www.objectivelytrue.com/uncategorized/2010/01/19/ubuntu-karmic-and-enlightenment-e17-via-easy_e17-sh/]("http://www.objectivelytrue.com/uncategorized/2010/01/19/ubuntu-karmic-and-enlightenment-e17-via-easy_e17-sh/")

---

### Post by zaptec on 2010-04-11
Ok, thank you for responding so quickly.

for the moment, the installation seems work well.

and thanks again :)

---

### Post by zaptec on 2010-04-11
Ho noooooo:

```
------------------------------- Easy_e17.sh 1.3.2 ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti
--------------------------------------------------------------------------------
  Updates:         http://omicron.homeip.net/projects/#easy_e17.sh
  Support:         #e.de, #get-e (irc.freenode.net)
                   morlenxus@gmx.net
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------


----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /home/louis/e17_src/
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Source mode:     packages
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Packages:        eina eet evas ecore efreet e_dbus embryo edje exchange e

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- e_dbus ..................... ok          
- embryo ..................... ok          
- edje ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for gcc option to accept ISO C89... (cached) none needed
checking whether to build documentation... yes
checking for doxygen... no
WARNING:
The doxygen program was not found in your execute path.
You may have doxygen installed somewhere not covered by your path.

If this is the case make sure you have the packages installed, AND
that the doxygen program is in your execute path (see your
shell manual page on setting the $PATH environment variable), OR
alternatively, specify the program to use with --with-doxygen.
configure: WARNING: no doxygen detected. Documentation will not be built
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LUA... no
checking for LUA... no
checking for LUA... no
checking for LUA... no
configure: error: unable to find Lua
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/edje.log'!

louis@zaptec:~/Téléchargements$ 

```

:shock:

---

### Post by kellemes on 2010-04-11
You probably need to install "liblua5.1-0-dev".

---

