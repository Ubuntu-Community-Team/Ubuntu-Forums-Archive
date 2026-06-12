---
title: "&quot;error: Cannot find X11 library&quot;"
date: 2006-07-04
forum: Desktop Environments
---

### Post by SEMW on 2006-07-04
Hi, all.

I'm a new Linux user, as of yesterday.

I like using mouse gestures (I used [Strokeit]("http://www.tcbmi.com/strokeit/") in Windows), so I'm trying to find a Linux equivalent.  The only one I can find is [Wayv]("http://www.stressbunny.com/wayv/index.shtml").  However, the current version is only available as source code.

So I downloaded it, read the instructions, opened the terminal, got to the right folder, typed in "./configure"...

```
No acceptable cc found in $path
```

So I search the forums, and found that some suggest installing "gcc".  It wasn't in "Add/remove Programs", but it was in Synaptic, so that was duly installed.

So I opened the terminal, got to the right folder, typed in "./configure"...

```
C compiler cannot create executables
```

So I search the forums, and found that some suggest installing "build-essential".  It wasn't in "Add/remove Programs", but it was in Synaptic, so that was duly installed.

So I opened the terminal, got to the right folder, typed in "./configure"... 

```
error: Cannot find X11 library
```

So I search the forums, and found... well, in a break with tradition, nothing.

So, any ideas?

---

### Post by jimbob on 2006-07-04
The way I have cured this in the past ( when installing a kde app on a gnome box) is to issue:

 apt-get build-dep k3b  ( change k3b to wayv here )

This seems to pull in all the dependencies including X-libraries that are needed.

I don't know if it will work for wayv but it is worth a try.

If not, try explicitly installing the X-related packages mentioned on wayv's web page.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by SEMW on 2006-07-04
That looks like a very useful tip; thanks.  As it happens, you're just slightly too late -- I finally got it to work by installing something Syaptic called "libx11-dev" -- but your tip definitely seems like it'll save a lot of time and searching in the future, so many thanks.

---

