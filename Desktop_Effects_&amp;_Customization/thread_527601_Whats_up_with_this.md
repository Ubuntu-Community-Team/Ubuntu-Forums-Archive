---
title: "Whats up with this?"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by ErusGuleilmus on 2007-08-16
When I run compiz or beryl, i get no window broders. i was told to run this command;
```

compiz --recplace -c emerald --replace
```

but I get this output;

```
william@william-laptop:~$ compiz --recplace -c emerald --replace
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: Couldn't load plugin '--recplace'
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
inotify_add_watch: No such file or directory
```

Emerald is installed, I have th icon in syste/prefrences

What is going on?

---

### Post by z0phi3l on 2007-08-16
Your command should read like this:

```
compiz --replace -c emerald --replace
```

---

### Post by ErusGuleilmus on 2007-08-17
that did not work then. :( I still had no window borders

---

### Post by neaeo on 2007-08-17
try this:
compiz --replace &
emerald --replace &

---

### Post by ErusGuleilmus on 2007-08-19
this did not work either

---

### Post by AndrewGene on 2007-08-19
I helped you last time.  Sorry for the misspelling.  That didn't help you I know.  But try "compiz --replace -c emerald --replace &" (i triple checked the spelling) ;)
Actually I only have the fusion-icon set to launch on start up and that alone launches compiz and emerald for me.

---

### Post by ErusGuleilmus on 2007-08-19
```
william@william-laptop:~$ compiz --replace -c emerald --replace &
[1] 9117
william@william-laptop:~$ /usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
inotify_add_watch: No such file or directory
```

Same exact problem, and Emerald is for sure installed.

---

### Post by Happy_Man on 2007-08-19
No, the command is ```
compiz --replace -c emerald &
```


EDIT: Ooooh, I'm late. How did you install?

---

### Post by ErusGuleilmus on 2007-08-19
I installed via ```
Sudo apt-get install emerald
```

---

### Post by ErusGuleilmus on 2007-08-19
Did I install this wrong?

---

### Post by FuturePilot on 2007-08-19
What repos did you get Compiz-Fusion from? Some might not have Emerald in them and then you end up installing the Emerald version that's in the Ubuntu repos and that one won't work with Compiz-Fusion.

---

### Post by ErusGuleilmus on 2007-08-19
I don't remember what repos I got it from. can we give beryl a go? i right clcik on the icon and open emerald, but nothing works.

---

### Post by psyopper on 2007-08-19
Do you get borders if you do NOT specify Emerald in the launcher?
```
 compiz --replace
```

If not, what video card are you using?

---

### Post by ErusGuleilmus on 2007-08-19
No dice on the compiz, I get this message.

```
william@william-laptop:~$  compiz --replace
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
inotify_add_watch: No such file or directory
```

As far as not specifiying emerald goes, I still get no borders.

My Graphics Card is a Nvidia GeForce go 6100 i believe. OpenArena and google earth run with out a hitch.

---

### Post by ErusGuleilmus on 2007-08-20
As you can see, beryl "works", but I have no window borders.

Edit: sorry, the .png was to large, you'll just have to believe me on the fact that it is working.

---

### Post by ErusGuleilmus on 2007-08-20
Any thoughts?  Thanks.

---

### Post by buzzmandt on 2007-08-20
for beryl i use to have the no borders thing,

I started using beryl-manager and to load beryl or metacity as needed and i no longer have an issue
as far as compiz goes, i've never had good luck with it

---

### Post by z0phi3l on 2007-08-20
You should probably reinstall Beryl or try out Compiz Fusion, like you said, Baryl "works" but the error is preventing beryl to reall work and without that working Emerald won't work either

---

### Post by seren6ipity on 2008-01-07
> **ErusGuleilmus said:**
> When I run compiz or beryl, i get no window broders. i was told to run this command;
```

compiz --recplace -c emerald --replace
```

but I get this output;

```
william@william-laptop:~$ compiz --recplace -c emerald --replace
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: Couldn't load plugin '--recplace'
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
inotify_add_watch: No such file or directory
```

Emerald is installed, I have th icon in syste/prefrences

What is going on?

I get this error, every time I launch compiz. The reason probably is that gtk-window-decorator does not run due to this error.
If you run gtk-window-decorator from /usr/bin it should provide you with window's border.

---

