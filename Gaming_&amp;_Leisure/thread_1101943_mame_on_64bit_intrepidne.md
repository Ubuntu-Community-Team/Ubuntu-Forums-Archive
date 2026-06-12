---
title: "mame on 64bit intrepidne"
date: 2009-03-20
forum: Gaming &amp; Leisure
---

### Post by shrndegruv on 2009-03-20
does this work for people?  I installed the latest sdlmame with the latest wahcade frontend and can't play any of my games.  I hit the enter+alt and see the game, but i cant do anything and it just blacks out after a second.  Even trying to run sdlmame on the rom produces the same result.  

Has anyone got this working?  Is there a reliable guide?

---

### Post by hikaricore on 2009-03-20
Run it from a terminal and post the error output.

---

### Post by shrndegruv on 2009-03-20
i don't see any errors.  the game just doesn't play.  hitting enter+left alt causes the game to pop up, but it is gone too fast to do anything..

---

### Post by disturbedite on 2009-03-21
you failed to mention any details of the apps you are using, such as the version numbers...

---

### Post by shrndegruv on 2009-03-21
sdlmame was .130 -- the one that was recently released.  Wah!cade was the developer snapshot, it was listed as the stable one to use.

I actually downloaded the source, did a compile (some page recommended gcc4.2 and with the 64 bit flag, compiled with no issue) and I get the same result.

Some games work (joust) but all the classic beloved ones from my childhood don't.  They don't give the unsupported screen, they just suffer from the "Blank screeen" issue i described above, where enter + left tab shows a still of the game, repeatedly hitting that combo shows the game playing behind the blank screen but it is completely unplayable.  This result happens no matter if i use the wahcase FE or just point the mame executable at the rom...the games failing games are shinobi, double dragon, ninja gaiden, etc...

---

### Post by hikaricore on 2009-03-21
> **hikaricore said:**
> Run it from a terminal and post the error output.

^ this

You may also want to try this packaged version of the latest sdlmame: [http://wallyweek.altervista.org/rel130.php](http://wallyweek.altervista.org/rel130.php)
You'll have to run make uninstall first if you compiled from source or you'll make a mess of things.

---

### Post by shrndegruv on 2009-03-21
thats where i got the binary and the source from.  The make file doesn't have an install so i just ran the executable from the directory to which it was build. 

And like I said, there is no error output when running from the command line....

---

### Post by hikaricore on 2009-03-21
Did you try the packaged version?

---

### Post by shrndegruv on 2009-03-21
yessir, i tried the packaged version, and when it failed i downloaded and compile the source and saw the same issue...

---

### Post by shrndegruv on 2009-03-22
made progress.  I hit the man page and tried software rendering instead of opengl rendering(which is default).  Works.  So now the question is why am i having trouble with opengl rendering.

When i originally tried it and it didn't work i shut compiz down, but that wasn't enough.  

so is it normal for opengl rendering NOT to work?  I have an ati card (mobility 3670 hd) with the fglrx (stock ubuntu) driver.  should this be working?

---

### Post by hikaricore on 2009-03-22
> glxinfo | grep rendering

Should return yes.  If not your video drivers need to be configured/installed properly.

---

### Post by shrndegruv on 2009-03-22
well compiz works fine with all effects, so i imagine that rendering is working good.  I did try to run with opengl enabled with compiz shutdown, and it didn't work -- let me go try that again.

---

### Post by hikaricore on 2009-03-22
Everytime I suggest you try something you seem to ignore it then later on tell me you did it as if I should have magically known.
I can't help someone like this, I'm sorry but best of luck to you.

---

### Post by shrndegruv on 2009-03-22
no man don't take it like that.  Its just that each of your suggestions I had already covered.

here

```

mharris@Ildatch:~$ glxinfo | grep rendering
direct rendering: Yes

```

my non-posting of this earlier stemmed from the fact that if compiz runs, than *implicitly* direct rendering is working...


wrt to errors from terminal output, i ran sdlmame rom.zip and got no errors, so i just reported that and didn't posted the error-less output.

---

