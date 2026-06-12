---
title: "[Lubuntu 13.10] Why won't this work/run"
date: 2013-11-23
forum: Emulators
---

### Post by cdoublejj on 2013-11-23
[http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

So in Lubuntu it is already marked as run as executable but, nothing happens. is there something i am missing? does it need packages i don't know abuot? i lcick it and absolutely nothing happens.

---

### Post by QIII on 2013-11-23
*Moved to **Emulators***

Hello!

Can you start the emulator via the terminal?

---

### Post by cdoublejj on 2013-11-24
I do not know how to do that. :(

---

### Post by QIII on 2013-11-27
My guess would be to open a terminal and issue

```
kega
```

But I've never used it.

---

### Post by cdoublejj on 2013-11-27
just type in kega? wouldn't terminal need to know where it is?

---

### Post by BigSilly on 2013-11-27
The command is -

```
Fusion
```

And yes I would first cd into the directory where you keep the Kega Fusion executable, via the terminal. If you don't know how let us know.

The chances are though that you are running a 64 bit install, and Kega Fusion is resolutely a 32 bit program. You probably need to install a few 32 bit libraries to get it to run, as Ubuntu no longer provides the simple meta package ia32-libs that used to fix it one fell swoop.

If I remember correctly, the libraries it needs are installed via the command below -

```
sudo apt-get install libglu1-mesa:i386 libgtk2.0-0:i386 libasound2:i386 libsm6:i386 libasound2-plugins:i386
```

You may also want to install something to make it look a bit better, as it can look pretty ropey without the theme it uses -

```
sudo apt-get install gtk2-engines-oxygen:i386
```

Try this and see if it helps. I'm sure this fixed it for me.

---

### Post by cdoublejj on 2013-11-30
"Ubuntu no longer provides the simple meta package ia32-libs that used to fix it one fell swoop."

wwwwhhhhhhhhhyyyyyyyyyyyyyyyyyyyyyyyyyyy? Do they not want more people to use linux? it's bad enough the repository or horribly outdated. /rant

---

### Post by BigSilly on 2013-11-30
It's not a problem really, but I would like to see it return.

Did it work for you?

---

### Post by cdoublejj on 2014-01-13
> **bigsilly said:**
> the command is -

```
fusion
```

and yes i would first cd into the directory where you keep the kega fusion executable, via the terminal. If you don't know how let us know.

The chances are though that you are running a 64 bit install, and kega fusion is resolutely a 32 bit program. You probably need to install a few 32 bit libraries to get it to run, as ubuntu no longer provides the simple meta package ia32-libs that used to fix it one fell swoop.

If i remember correctly, the libraries it needs are installed via the command below -

```
sudo apt-get install libglu1-mesa:i386 libgtk2.0-0:i386 libasound2:i386 libsm6:i386 libasound2-plugins:i386
```

you may also want to install something to make it look a bit better, as it can look pretty ropey without the theme it uses -

```
sudo apt-get install gtk2-engines-oxygen:i386
```

try this and see if it helps. I'm sure this fixed it for me.

it works!!!

---

### Post by BigSilly on 2014-01-15
> **cdoublejj said:**
> it works!!!

Ah cool. Always nice to hear when something that didn't work before, suddenly does. ;)

Have fun. It's a great emulator imho.

---

### Post by cdoublejj on 2014-06-11
IT WORKS!!! This time with Lubuntu 14.04 LTS 64 bit.

---

### Post by Matt_klimmer on 2014-06-25
How can Kega be installed just via command line?  Just unzip and drop in to /usr/bin?

---

