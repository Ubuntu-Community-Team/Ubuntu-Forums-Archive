---
title: "Unmet dependencies with compiz"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by aimran on 2007-06-27
I'm getting the following error:

aimran@aimranlicious:~$ sudo apt-get install compiz  # compiz-gnome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

[b]The following packages have unmet dependencies.
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages[/b]

Anyone else having this problem?

---

### Post by hyperair on 2007-06-27
Do you have trevino's repository enabled? If so, then you need to remove compiz-core and desktop-effects first, then reinstall everything. That's what I did.

```

sudo apt-get remove compiz-core desktop-effects compiz
sudo apt-get install compiz-core desktop-effects compiz

```

---

### Post by aimran on 2007-06-27
I do have trevino's repositories enabled. I can see it when I search for compiz in synaptic. However selecting it for installation gives me the following error:

compiz:
 Depends: compiz-decorator  but it is not installable

Tried to search for compiz-decorator and no results :P

---

### Post by aimran on 2007-06-27
Seems like compiz-decorator is the problem. And a bump :P

---

### Post by kpolice on 2007-06-28
Do you use Ubuntu 64 bit? if you do then there are no packages for you and that's why you have that problem.

---

### Post by hyperair on 2007-06-28
@aimran: Did you try using the commands I gave you in the previous post?

---

### Post by aimran on 2007-06-28
> **hyperair said:**
> @aimran: Did you try using the commands I gave you in the previous post?

Yes I did.

> **kpolice said:**
> Do you use Ubuntu 64 bit? if you do then there are no packages for you and that's why you have that problem.

Ah damn. Thanks mucho! Sticky on the desktop effects and customisation forum for compiz-fusion should have mentioned it :P

Thanks for the effort guys. And bump for those who are encountering this problem and are still wondering why.

---

### Post by jpyanowski on 2007-08-24
Well now I know why Compiz doesn't work for me. Thanks for the info.:(

---

### Post by hyperair on 2007-08-25
WAIT!!! There ARE packages for you. Trevino's repositories has amd64 packages..

Open your /etc/apt/sources.list file:
```
gksudo gedit /etc/apt/sources.list
```

Look for lines like this:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src deb http://download.tuxfamily.org/3v1deb feisty eyecandy

```

Exchange the "eyecandy" with "eyecandy-amd64"
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

```

EDIT: They seem a lil outdated though.

---

