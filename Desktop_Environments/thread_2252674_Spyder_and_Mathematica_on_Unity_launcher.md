---
title: "Spyder and Mathematica on Unity launcher"
date: 2014-11-13
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2014-11-13
Hi, I have a strange problem. I have spyder2 (from Ubuntu backport update) and Mathematica installed on my system (in my $HOME with a symlink to /usr/bin) Now whenever I open spyder a blank icon with description 'Welcome to Wolfram Mathematica' appears in the unity bar instead of the icon of spyder lighting normally like when an application is in use. 

Any hint? Thanks.

Ubuntu 14.04 64 bit unity.

Edited: I reinstalled Mathematica, it was normal but after I rebooted this is happening again.

---

### Post by monkeybrain20122 on 2014-11-13
I fixed it but it is still kind of mysterious to me.

Here is the fix. 

First open mathematica, then run in the terminal
```
xprop|grep WM_CLASS
``` 
place the cross on Mathematica's window and click and it comes back on the terminal as XMathematica
Then edit Mathematica's desktop file by appending

```
StartupWMClass=XMathematica
```

After this when Mathematica is running the second grey icon (Welcome to Wolfram Mathematica) no longer appears and the normal launcher icon behaves as it should.

However, when I run spyder this grey icon still appears exactly like the screenshot in my first post and the normal spyder icon does nothing.

Running xprop|grep WM_CLASS on spyder resulted in "' '" or something like that. I figured that may be for the grey launcher. So I edited spyder's desktop file by simply adding

```
StartupWMClass=
``` (i.e an empty string for StartupWMClass)

Now it all works (screenshot)

But it is still a mystery why this happened to spyder and spyder only and I needed to fix it by adding the StartUPWMClass line even after I fixed Mathematica's desktop file. It is a bit unsettling.

I am leaving this thread open for a while and see if there is any explanation. Thanks.

---

### Post by monkeybrain20122 on 2014-11-16
Any theory?

---

