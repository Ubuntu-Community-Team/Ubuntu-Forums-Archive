---
title: "This LUA installation is making me cry."
date: 2009-02-22
forum: General Help
---

### Post by Hellstudios on 2009-02-22
Literally, CRY. and smashing my fists against my Keyboard.


PLEASE HELP ME. I DONT THINK MY KEYBOARD CAN TAKE MUCH MORE ABUSE. D:


anywase i switched to Ubuntu not even a week ago and i like it, besides for the fact that it hates me and doesnt want any of my software on it.

i downloaded LUA 5.1.3 three days ago....its still sitting there on my desktop, waiting to be installed..... i finally google how to install apps on ubuntu, and i keep hearing "do make" or "make" and im like WTF? WHERE DO I TYPE MAKE? i tried terminal and it just comes back with errors. 


so please, PLEASE. post step by step instructions on how to install stuff. and if you do, i will internally greatful and i will stop crying that i completely uninstalled XP. 


my computer specs are:
compaq presario
intel celeron d 3.16ghz processor
512 MB ram
umm....(built in?) video card....(i dont know)
80gb HDD (that has nothing to do with it, but ok...)
and a dvd RW drive. (either does that)




------------------------


PLEASE HELP ME.

:(

---

### Post by Hellstudios on 2009-02-22
wow. 1300 users online. and bump. my topic is going down the list fast.

---

### Post by arubislander on 2009-02-22
Hi, welcome to Ubuntu.

You do not mention if you downloaded the sources or the binaries for LUA. Did you by chance take a look at: [http://luabinaries.luaforge.net/installation.html](http://luabinaries.luaforge.net/installation.html) ?

If you're still stuck after you read this, post another message.

---

### Post by jpeddicord on 2009-02-22
Are you sure you want to install Lua from a download? Ubuntu has the same version in the software repositories, which are much easier to use. To use them, open Synaptic (System > Administration > Synaptic Package Manager). Next, go to Settings > Repositories and make sure "Community-maintained open-source software (universe)" is checked. Close the window, and then click the Reload button in Synaptic.

Then, click the Search button, and search for **lua5.1** which should give you a nice long list. Double-click on any of the packages you want to install. If you're building your own Lua app, you'll probably need the regular Lua binaries: **lua5.1**. When you're done, click Apply, and the necessary Lua libraries will be installed.

If you're *sure* you want to build Lua from scratch in a source download, see the following links for a general overview:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

(Also, please do not bump your topic until at least 24 hours have passed. Old threads *do* get looked at by many users.)

---

### Post by taurus on 2009-02-22
You know there is a lua version (5.0.3-3) in the repos.  So, install it from the repos unless you have a reason to compile the new version!

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install lua50
```

---

### Post by Hellstudios on 2009-02-22
REPLY TO FIRST POST: (i was typing while you guys replied)



i am completely new to ubuntu. PLEASE. i do not understand that guide at all. D: i have no idea what they mean by 

> 
$SYS_BINDIR (System executables, usually in /usr/local/bin)
    lua5.1
    luac5.1
    bin2c5.1

$SYS_LIBDIR (System libraries, usually in /usr/local/lib)
    liblua5.1.so
    liblua5.1.a

$LUA_INC (Lua include files, usually in /usr/local/include)
    lauxlib.h
    lua.h
    lua.hpp
    luaconf.h
    lualib.h




please dude. this is extremely annoying for me. (why cant ubuntu have .exe setups like in windows? WHY!?)


its like showing a 12 year old advanced calculus. he wont get it no matter how hard you try unless you explain EACH STEP. D:

---

### Post by taurus on 2009-02-22
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by arubislander on 2009-02-22
OK, forget the LUA download...

As jacobmp mentioned, LUA is in the repositories. That makes installing it just as easy as a windows exe. Follow the steps in his post and you'll be good to go.

---

### Post by Hellstudios on 2009-02-22
Thank you very much. Oh my god i am forever grateful.

---

### Post by Hellstudios on 2009-02-22
> **taurus said:**
> You know there is a lua version (5.0.3-3) in the repos.  So, install it from the repos unless you have a reason to compile the new version!

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install lua50
```

about that.... the terminal doesnt allow me to enter any characters when it asks for the password..anyway around this?


and how do i find the app when its finished installing from the repository?:(

---

### Post by jpeddicord on 2009-02-22
> **Hellstudios said:**
> about that.... the terminal doesnt allow me to enter any characters when it asks for the password..anyway around this?

That's intentional to not show your password. Just continue typing it in and hit Enter.

---

### Post by sdowney717 on 2009-02-22
use synaptic use the menu at the top
goto system-admin-synaptic

type it into the search field

check to install

all automatic for you

---

### Post by Hellstudios on 2009-02-22
how do i find the app after i installed it from the repository..? :(

---

### Post by jpeddicord on 2009-02-22
Lua, from what I gather, does not have a graphical interface, it is just a command-line parser. Open a terminal and type 'lua' to use a console or run a script.

```
usage: lua [options] [script [args]].
Available options are:
  -        execute stdin as a file
  -e stat  execute string `stat'
  -i       enter interactive mode after executing `script'
  -l name  load and run library `name'
  -v       show version information
  -P       suppress the setting of LUA_PATH. If not specified
           very early, this setting may not take effect.
  --       stop handling options

```

---

