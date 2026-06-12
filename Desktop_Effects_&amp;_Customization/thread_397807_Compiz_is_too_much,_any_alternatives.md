---
title: "Compiz is too much, any alternatives?"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by alextj on 2007-03-31
Hi!
I really like a couple of features in Compiz (or Beryl for that matter), but it is too big, slow and buggy, not really worth running because of two small features. I don't need 90% of what it does.

I really like to be able to see all opened windows at once on my screen (when I move mouse to TopRight corner) and sometimes I use it to adjust transparency of windows/panels. Those are about the only things that I really need from Compiz.

I know I can probably manage to change transparency of windows somehow without Compiz (I used to use some pathetic script to do this on FVWM on Gentoo).... Though, I have no idea how to show all opened windows at once on screen.

Are there any lightweight alternatives of Compiz/Beryl, without much eyecandy, but with some useful productivity features?
Is it possible to implement those two features, that I mentioned above, with some scripts?

Thanks!

---

### Post by synss on 2007-03-31
AFAIK, Beryl works with plug-ins, i.e. just disable the plug-ins you do not want and you are done.

Now, is all you want is translucency and expose-like, you can have a look at skippy, expose-clone and such.

---

### Post by alextj on 2007-03-31
Thanks Synss for reply!
Yes, skippy is what I was looking for. Though, from people's comments, it is really slow :P Haha, well, not exactly what I am looking for afterall? :P

I just can't seem to get it to work. It installs, I can start it (at least it doesn't give any error when I type skippy in terminal), but nothing happens when I press the button (default was F11, but that didin't work, I change to Scroll_Lock as someone suggested, not working. Nothing else worked either).

Maybe I'll try to fix it a little more, but if nothing else, I'll try beryl and see how frustrating it is going to be :D

Thanks!

---

### Post by ben.s on 2007-03-31
Synss is right when he says you can strip beryl down by turning off all the features you don't need.  The lastest versions (running out of Feisty, I'm not sure if Edgy is tracking the same version or not) have been pretty stable for me.  Then again, Feisty is so unstable, other things tend to crash before beryl :-)

---

### Post by lsutiger on 2007-04-12
I tried installing skippy with apt-get install...It installed but I get an error:
```
Get:1 http://archive.ubuntu.com dapper/universe skippy 0.5.1rc1-4 [28.6kB]
Fetched 28.6kB in 1s (28.0kB/s)
Selecting previously deselected package skippy.
(Reading database ... 109863 files and directories currently installed.)
Unpacking skippy (from .../skippy_0.5.1rc1-4_i386.deb) ...
Setting up skippy (0.5.1rc1-4) ...

complexity@complexity-laptop:~$ skippy
WARNING: Couldn't load config file '/home/complexity/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.

```


??

---

### Post by bornagainpenguin on 2008-03-17
> **lsutiger said:**
> I tried installing skippy with apt-get install...It installed but I get an error:
```
Get:1 http://archive.ubuntu.com dapper/universe skippy 0.5.1rc1-4 [28.6kB]
Fetched 28.6kB in 1s (28.0kB/s)
Selecting previously deselected package skippy.
(Reading database ... 109863 files and directories currently installed.)
Unpacking skippy (from .../skippy_0.5.1rc1-4_i386.deb) ...
Setting up skippy (0.5.1rc1-4) ...

complexity@complexity-laptop:~$ skippy
WARNING: Couldn't load config file '/home/complexity/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.

```


??

Try [this]("https://wiki.ubuntu.com/Skippy") it really helped me figure out that issue!  Now does anyone know any other alternatives to compiz I can use?  I promised my sister special effects on her "new" (used) computer after seeing me run Ubuntu on my laptop, but none of my spare video cards will run desktop-effects.  So I'm looking for alternatives...any ideas?

--bornagainpenguin

---

### Post by ShodanjoDM on 2008-03-17
Hmm, if you're not looking for the 3d and wobbly windows effects, xcompmgr will give you drop shadows and IIRC transparencies.

Or you can install enlightenment for fantastic eye candies that even my old Thinkpad T-21 laptop can run.

---

