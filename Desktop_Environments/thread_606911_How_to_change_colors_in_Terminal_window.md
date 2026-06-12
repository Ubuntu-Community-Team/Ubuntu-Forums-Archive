---
title: "How to change colors in Terminal window?"
date: 2007-11-08
forum: Desktop Environments
---

### Post by cddot on 2007-11-08
On the command line, when doing an ls, the files are colored according to the file types. How can we control this. It does not appear to be under Edit, Current profile.

---

### Post by tyfius on 2007-11-08
It should be under the "Colors" tab. There you can change the colors or simply choose another palette.

Added screen shot.

---

### Post by mojoman on 2007-11-08
> **tyfius said:**
> It should be under the "Colors" tab. There you can change the colors or simply choose another palette.

Added screen shot.

I don't think this is correct. Try adding this to your ~/.bashrc file instead (create it if it doesn't already exist):

```

if [ "$TERM" != "dumb" ]; then
eval "`dircolors -b`"
alias ls='ls --color=auto'
fi
```

/mojoman

---

### Post by kellemes on 2007-11-08
> **mojoman said:**
> I don't think this is correct. Try adding this to your ~/.bashrc file instead (create it if it doesn't already exist):

```

if [ "$TERM" != "dumb" ]; then
eval "`dircolors -b`"
alias ls='ls --color=auto'
fi
```

/mojoman

It is correct because it **does** work indeed.. but only in Gnome-terminal, and that's the downside.
And so I agree configuring .bashrc is preferred since it's terminal-independent.

---

### Post by mojoman on 2007-11-09
> **kellemes said:**
> It is correct because it **does** work indeed.. but only in Gnome-terminal, and that's the downside.
And so I agree configuring .bashrc is preferred since it's terminal-independent.

Oh, didn't know that but then again, I gave up on Gnome a long time ago. Well, at least I learned something new. :)

---

### Post by TubaTodd on 2007-11-09
If you google linux bash colors you will find a variety of sources. There was a GREAT website that I ran across through "StumbleUpon" that I thought I bookmarked, however I can't seem to find it. I will post it if I find it.

---

