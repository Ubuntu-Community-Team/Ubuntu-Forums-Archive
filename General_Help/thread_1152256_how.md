---
title: "how?"
date: 2009-05-07
forum: General Help
---

### Post by polskimoose on 2009-05-07
how do i run an application through the command line?

---

### Post by riza hylviu on 2009-05-07
open the terminal from applications/accessories/terminal then type the  application's name for example gimp and then hit enter

---

### Post by baseface on 2009-05-07
type the name of it.

---

### Post by Alterax on 2009-05-07
by typing its path and name.  Paths depend on where the program is installed.

example:  To start iceweasel:
```

**alterax@nifelheim:/$** /usr/bin/iceweasel

```
Now if you're trying to run one that you've downloaded, go to the directory it's in and use the ./ identifier.  That means "in this directory:"

```
**alterax@nifelheim:/home/alterax/$ ** ./myprogram

```
If that doesn't work, you may have to set the execute bit, then try to run it.
```
**alterax@nifelheim:/$** chown a+x ./myprogram
```
```
**alterax@nifelheim:/home/alterax/$ ** ./myprogram

```

---

### Post by sisco311 on 2009-05-07
Type the name of the application and hit Enter(Return).

i.e.
```
firefox

gedit

nautilus

```

What are you trying to accomplish?

---

### Post by polskimoose on 2009-05-07
> **sisco311 said:**
> Type the name of the application and hit Enter(Return).

i.e.
```
firefox

gedit

nautilus

```

What are you trying to accomplish?

im trying to accomplish this (but no one responded):

[http://ubuntuforums.org/showthread.php?p=7234362#post7234362](http://ubuntuforums.org/showthread.php?p=7234362#post7234362)

---

### Post by albinootje on 2009-05-07
> **polskimoose said:**
> im trying to accomplish this (but no one responded):

[http://ubuntuforums.org/showthread.php?p=7234362#post7234362](http://ubuntuforums.org/showthread.php?p=7234362#post7234362)

Try for example :
```

wine .wine/path_to_your_installed_n64_emulator/n64_emu.exe

```

But.. with Wine it is possible you have to "cd" into the directory where you want to run the application, so you can try this e.g. :
```

cd .wine/path_to_your_installed_n64_emulator/
wine ./n64_emu.exe

```

Apart from this I recommend PlayOnLinux :
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
With that you can fairly easy switch between different Wine versions. This can be handy when a programs runs best with a certain Wine version.

---

