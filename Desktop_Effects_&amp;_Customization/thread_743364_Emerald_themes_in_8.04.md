---
title: "Emerald themes in 8.04"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by Naatan on 2008-04-02
Hi, I've installed emerald on my Ubuntu 8.04 setup but when I change a theme in Emerald it doesn't update in ubuntu (not even after restarting compiz)

I'm guessing something must have changed in 8.04.. anyone that can tell me "what" ?

---

### Post by overdrank on 2008-04-02
> **Naatan said:**
> Hi, I've installed emerald on my Ubuntu 8.04 setup but when I change a theme in Emerald it doesn't update in ubuntu (not even after restarting compiz)

I'm guessing something must have changed in 8.04.. anyone that can tell me "what" ?

Hi and have you tried the command ```
emerald --replace 
``` using the alt, F2 keys.

---

### Post by JBAlaska on 2008-04-02
Emerald themes are only in the feisty repo's, you can d/l them for other versions here:
```
http://packages.ubuntu.com/feisty/x11/emerald-themes
```

---

### Post by Tripy-devo on 2008-04-03
Hey, I also have the same problem, and emerald --replace works for me.

But how can you make it work after reboot?

I stay Vista-ish untill i reboot :(

---

### Post by medivh on 2008-04-03
You can add the command to sessions to start automatically.
System->Preferences->Sessions
Press ADD button and fill in the blanks
Name: Emerald
Command: emerald --replace
Comment: Anything you want or empty

---

### Post by overdrank on 2008-04-03
> **Tripy-devo said:**
> Hey, I also have the same problem, and emerald --replace works for me.

But how can you make it work after reboot?

I stay Vista-ish untill i reboot :(

Hi and you can add it to start up, system, preference, sessions then click the add.

---

### Post by Naatan on 2008-04-03
I managed to change the theme by going into the gconf editor and changing the theme under apps > metacity

---

### Post by nathonix on 2008-04-06
thank you so much! emerald --replace worked awesomely.

---

### Post by moong on 2008-04-17
Hello,

Goto compiz gnome manager > Window Decoration > Command

replace
 
/usr/bin/compiz-decorator

for

/usr/bin/emerald

reboot and go.

---

### Post by Arathon on 2008-04-17
> **moong said:**
> Hello,

Goto compiz gnome manager > Window Decoration > Command

replace
 
/usr/bin/compiz-decorator

for

/usr/bin/emerald

reboot and go.

This doesn't seem to work for me.  The tooltip for that says "Decorator command line that is executed if not decorator is already running."  I assume that metacity is somehow getting started before they get to this point, or something.  I'd rather not add something else to my Session since it will mean starting up metacity, then starting up emerald.  I'd rather metacity didn't start at all.  How do I get that to happen?

---

### Post by Thundera on 2008-04-17
Oh how odd, I Used Ubuntu twice in my life, and other linux distros, I kept changing constantly so I never got to that. Good Luck though, maybe you can report it as an error if those people's responses don't work.

---

### Post by iEternal on 2008-04-25
> **overdrank said:**
> Hi and have you tried the command ```
emerald --replace 
``` using the alt, F2 keys.

after i enter the command in the terminal, it works... but once I close terminal i get borderless windows. help?

---

### Post by Arathon on 2008-04-25
> **iEternal said:**
> after i enter the command in the terminal, it works... but once I close terminal i get borderless windows. help?

Use Alt-F2 - this opens a terminal "launcher" of sorts.  All programs that you start in a terminal will be closed when you close that terminal...although sometimes you can get around this by typing in a "&" after the command.

You could try this with emerald, by typing 

emerald --replace &

but I won't guarantee that that'll work.

---

### Post by iEternal on 2008-04-25
> **Arathon said:**
> Use Alt-F2 - this opens a terminal "launcher" of sorts.  All programs that you start in a terminal will be closed when you close that terminal...although sometimes you can get around this by typing in a "&" after the command.

You could try this with emerald, by typing 

emerald --replace &

but I won't guarantee that that'll work.

blah, i totally skipped the alt+F2 part. thanks for bringing that to my attention and helpin' a noob out. :)

---

### Post by GammaPoint on 2008-04-25
> **JBAlaska said:**
> Emerald themes are only in the feisty repo's, you can d/l them for other versions here:
```
http://packages.ubuntu.com/feisty/x11/emerald-themes
```

Will emerald-themes be in Hardy Heron's repos soon?

---

### Post by overdrank on 2008-04-25
> **GammaPoint said:**
> Will emerald-themes be in Hardy Heron's repos soon?

HI and yes the emerald is it the hardy repos. :KS

---

### Post by ephemeralDream on 2008-04-25
**Method 1: the brute-force way**

```

System > Preference > Window Decoration > Command

Then replace

/usr/bin/compiz-decorator

for

/usr/bin/emerald --replace


```


**Method 2: the elegant way for me**
In this method, we will make no change in ccsm window decorator command.

/usr/bin/compiz-decorator checks for all available decorators, thus it is able to fall back to other decorators if 1 of them failed.

```

sudo gedit /usr/bin/compiz-decorator

Change line 30 from 

USE_EMERALD="no"

to

USE_EMERALD="yes"

```

done we are ready to go.

Now no need to reboot, Alt+F2, compiz-decorator --replace. =)

Cheer mates,

---

### Post by asmiller-ke6seh on 2008-04-26
> **overdrank said:**
> Hi and have you tried the command ```
emerald --replace 
``` using the alt, F2 keys.

PERFECT!  It worked INSTANTANEOUSLY!!! Thank you.

[CENTER][SIZE="5"][FONT="Arial Black"][COLOR="Blue"]<That was Easy>[/COLOR][/FONT][/SIZE][/CENTER]

---

### Post by GammaPoint on 2008-04-28
> **overdrank said:**
> HI and yes the emerald is it the hardy repos. :KS

Hi, I'm not talking about emerald. I'm using emerald right now. What I want is the package that in the Fedora RPMs is called 'emerald-themes' and allows you to do into 'Emerald Theme Manager' and go to 'edit themes' and change your frame engine.  Is this in the Ubuntu repos, and if so, what is it called?

---

### Post by overdrank on 2008-04-28
> **GammaPoint said:**
> Hi, I'm not talking about emerald. I'm using emerald right now. What I want is the package that in the Fedora RPMs is called 'emerald-themes' and allows you to do into 'Emerald Theme Manager' and go to 'edit themes' and change your frame engine.  Is this in the Ubuntu repos, and if so, what is it called?

If you installed emerald then the theme manager should be installed also under system, preference. Are you using hardy?

---

### Post by GammaPoint on 2008-04-28
> **overdrank said:**
> If you installed emerald then the theme manager should be installed also under system, preference. Are you using hardy?

Okay, maybe it's not actually the frame engine, but the frames that I can't change.  But yes, 'Emerald Themer' is under system->preferences. But if I open that up I have zero themes to choose from.  This is not the case on my Fedora system, where I can choose from, for example, Adonis_mod, sky, adonis, blue satin, etc etc.  

I just don't have any themes to choose from.

---

### Post by overdrank on 2008-04-29
> **GammaPoint said:**
> Okay, maybe it's not actually the frame engine, but the frames that I can't change.  But yes, 'Emerald Themer' is under system->preferences. But if I open that up I have zero themes to choose from.  This is not the case on my Fedora system, where I can choose from, for example, Adonis_mod, sky, adonis, blue satin, etc etc.  

I just don't have any themes to choose from.
Hi and you can download them here
[http://themes.beryl-project.org/themes.php?cat=0](http://themes.beryl-project.org/themes.php?cat=0)
And import with emerald theme manager.

---

### Post by GammaPoint on 2008-04-29
> **overdrank said:**
> Hi and you can download them here
[http://themes.beryl-project.org/themes.php?cat=0](http://themes.beryl-project.org/themes.php?cat=0)
And import with emerald theme manager.

Oh okay cool. I guess it's just a Fedora thing that someone packaged up some themes and put them in the repository. But it looks like downloading straight from the website gives me a much larger selection so that's got its advantages as well!

Thanks!

---

### Post by toupeiro on 2008-04-30
> **GammaPoint said:**
> Oh okay cool. I guess it's just a Fedora thing that someone packaged up some themes and put them in the repository. But it looks like downloading straight from the website gives me a much larger selection so that's got its advantages as well!

Thanks!

It wasn't always just a fedora thing...  7.10 had emerald-themes, but in 8.04 it says they are obsoleted by another package, giving no reference as to what that package is.  So, for now, I'd say hardy repos have no usable emerald themes unless someone knows the magic word to get the right packages?

---

### Post by charlemagne86 on 2008-05-22
ya i second that.....i used gutsy and had default themes in emerald preloaded.....

:)

just hope that someone can get the magic word soon....

---

### Post by charlemagne86 on 2008-05-22
just in case someone else like me wanders off and is wondering where to find that illusive(duh!) "window decoration"...its in the effects part of ccsm!

---

### Post by charlemagne86 on 2008-05-22
> **ephemeralDream said:**
> **Method 1: the brute-force way**

```

System > Preference > Window Decoration > Command

Then replace

/usr/bin/compiz-decorator

for

/usr/bin/emerald --replace


```


**Method 2: the elegant way for me**
In this method, we will make no change in ccsm window decorator command.

/usr/bin/compiz-decorator checks for all available decorators, thus it is able to fall back to other decorators if 1 of them failed.

```

sudo gedit /usr/bin/compiz-decorator

Change line 30 from 

USE_EMERALD="no"

to

USE_EMERALD="yes"

```

done we are ready to go.

Now no need to reboot, Alt+F2, compiz-decorator --replace. =)

Cheer mates,
yay....havent checkd if it works....bt seems to be the right(and elegent) thing to do....the logic looks like it should work anyway.....

i would prefer this file changing setting of /usr/bin/compiz-decorator anyday over the "brute-force" /usr/bin/emerald --replace option..

cheers to ephemeralDream!!!!



UPDATE: It works...though affter a reboot i think.

---

### Post by charlemagne86 on 2008-05-22
btw, dunno if its the right place to post....sorry mods!!

but can anyone direct me to some good looking themes that say out 'linux'......wherever i search (beryl-themes. gnome-look etc...) the themes are either winXP/Vista/MacOS spinoffs..(which i dont want) or either not good enough visualy!!


thnx!

---

### Post by mahiyar on 2008-05-24
Quiet some months back I had written a how to on using emerald with Gutsy, it also works with Hardy the link is here [http://ubuntuforums.org/showthread.php?t=598592](http://ubuntuforums.org/showthread.php?t=598592)

---

### Post by DDRFreak21 on 2008-06-04
For those who are still looking for the package:

[http://packages.ubuntu.com/feisty/all/emerald-themes/download]("http://packages.ubuntu.com/feisty/all/emerald-themes/download")

and choose a mirror to dl the deb from.

Or for the lazy a direct DL link:

[http://mirrors.kernel.org/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb") (SLOW)

---

