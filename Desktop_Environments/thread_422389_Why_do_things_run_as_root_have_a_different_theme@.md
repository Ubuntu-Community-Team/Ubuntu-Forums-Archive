---
title: "Why do things run as root have a different theme?@"
date: 2007-04-25
forum: Desktop Environments
---

### Post by rich.bradshaw on 2007-04-25
When I run things as root they have a horrible grey theme, when I run normally they are nice and pretty!

Why?

I want it to look the same!

Rich

[IMG]http://i16.tinypic.com/2wom6ir.png[/IMG]

---

### Post by coolclassic on 2007-04-25
It's one way of recognising root from user.

---

### Post by rejser on 2007-04-25
It's because when you change theme you change for your user. You don't change for every user on the computer. And especially don't change roots theme.
Start the theme manager as root from terminal and change it.

---

### Post by rich.bradshaw on 2007-04-25
I changed my theme to something different and it does change the theme for everything - think it was just a broekn theme I had applied.

Think the theme is done by Metacity which isn't run as root - but does draw root windows.

---

### Post by hesoez on 2007-04-25
Just link the themes and icons folders to the root directory.
```

sudo ln -s /home/<yourusername>/.themes /root/.themes
sudo ln -s /home/<yourusername>/.icons /root/.icons

```
the root windows will use your selected theme and change to the new theme if you select another in the theme-manager.
If you have custom fonts you can link the fonts dir too.
```

sudo ln -s /home/<yourusername>/.fonts /root/.fonts

```

---

### Post by ComplexNumber on 2007-04-25
> **rejser said:**
> It's because when you change theme you change for your user. You don't change for every user on the computer. And especially don't change roots theme.
Start the theme manager as root from terminal and change it.
don't do that. its not necessary.


[B]
rich.bradshaw[/B]
put all your themes in /usr/share/themes. the reason why that happens to you is because you have the theme that you're using stored in ~/.themes directory in your home directory.

---

### Post by jzwill on 2007-04-25
I would imagine this is to discourage you from logging in as root. It is not like you can't customize it, right?

---

### Post by ComplexNumber on 2007-04-25
> **jzwill said:**
> I would imagine this is to discourage you from logging in as root. It is not like you can't customize it, right?
its not. its for the reasons that i've stated. when a theme is in ones own home directory, no other account(not even root) can access it. the only way for themes to be accessed by all is to place them in /usr/share/theme because thats for system-wide application of themes.

all my themes are stored in /usr/share/themes, but  look what happens when i move the Afterhours theme from /usr/share/themes to my own home directory. see screenshot1. then look what happens when i revert to my normal theme which is stored in /usr/share/themes (see screenshot 2). 
notice how synaptic(ie a root application) is unthemed in the 1st screenshot when the theme is in my home directory and not in /usr/share/themes.

---

### Post by turezky on 2008-02-12
10x, ComplexNumber...
Worked out really smooth :)

---

