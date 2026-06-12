---
title: "Weird error trying to run Beryl on ATI laptop"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by davidalves on 2007-03-26
I have the Feisty beta on my laptop. I've followed the howto guides to try to get beryl running. I've downloaded fglrx, xgl, beryl, and emerald-themes using the packages from the official feisty repository (Can't use the open driver because it's an X1400). I made the /usr/bin/startxgl.sh script and the corresponding /usr/share/xsessions/xgl.desktop file. So after doing all this, I can start an Xgl session everything seems to work normally. Now what? I read somewhere that I should run beryl-manager after I start my Xgl session,  but when I do that it floods the console with this error message:

** (beryl-manager:7379): CRITICAL **: can't execute beryl-xgl: Resource temporarily unavailable

The beryl icon appears in the system tray, but it's unresponsive. So... what do I need to do differently to get beryl running?

Any help is appreciated, thanks in advance. =)

---

### Post by davidalves on 2007-03-26
Incidentally, from what I've seen in other places, beryl-xgl is a program that you're supposed to run to use beryl on xgl. I don't seem to have it installed, typing beryl-xgl on the command line tells me command not found. Am I missing a package or something? I have beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-bindings, etc. These are all version 0.2.1  So I really don't know what package I could be missing. =P

---

### Post by AtrejuT on 2007-03-26
I think the beryl packages in the universe repos are broken for xgl.
At least they are for me - Try using the repos at
```

[http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

```
and force all beryl and emerald packages to 0.2.0

atreju

---

### Post by getaceres on 2007-03-27
Great, the last update broke compiz too. I'm now without desktop effects waiting for a fix in either beryl or compiz.

---

### Post by PriceChild on 2007-03-27
Ubuntu's beryl was not built for xgl due to its inline mesa.

Please use```
deb http://ubuntu.beryl-project.org feisty main
```

---

### Post by 5ilver5urfer on 2007-03-29
Hi,
I got beryl-working back using the right repo and deselecting universe repos.
But if i reuse universe repos, my beryl version (=0.2.0) will be upgraded, right?
How can I use universe repos and keep my current beryl version? :confused: 

Thanks

---

### Post by eode on 2007-03-29
After adding the ubuntu.beryl.org repository as mentioned in other messages, do the following:

```
sudo gedit /etc/apt/preferences
```


and add the following text.  I've heard you are not to have any blank lines at the beginning of the file, but I don't know if this is accurate.  Better  not to chance it.

```
Package: *
Pin: release o=lupine
Pin-Priority: 1001
```

Then, if the beryl packages are already installed, do an update/upgrade.  Otherwise, install the package "beryl".

Finally, if you want to be able to force-install to an ubuntu version without it automatically downgrading to the beryl repositories in the future, go back in and change:

[FONT="Courier New"]Pin-Priority: 1001[/FONT]

to:
[FONT="Courier New"]Pin-Priority: 1000[/FONT]

You can remove this entire Package/Pin/Pin-Priority entry in the future to go back to 'normal' behaviour (f.e, if/when ubuntu comes out with a functional beryl-xgl).



Explanation of the entry in /etc/apt/preferences:
"Package: *" tells it to apply this to all packages in the repository.
"Pin: release o=lupine" tells it to we're choosing packages by origin "lupine" (which is the origin name beryl-project packages have)
"Pin-Priority: 1000" tells it to prefer the beryl repository to the ubuntu repository, but not so much that it downgrades from ubuntu packages if you have some already installed.  Setting to 1001 causes it to prefer beryl repositories to the ubuntu ones so much that it downgrades.
Setting it to 1000 is useful because you might want the newer beryl-manager, for example, even though you're using the older beryl.  With some finagling, you should be able to install the 2.1 version of most everything except beryl/beryl-core.

---

### Post by 5ilver5urfer on 2007-03-29
:lol: Works perfectly.
Thanks ;)

---

### Post by eode on 2007-03-29
NP, glad to be of service.  No one who *can* have a nifty beryl desktop should really be without.  ;-)

---

### Post by PriceChild on 2007-03-29
Oh by the way... the Ubuntu packages will not support beryl-xgl in its current form for various reasons. Don't expect it to be fixed for feisty.

---

### Post by eode on 2007-03-29
..thanks for the info.  ..mebbee I'll write this up and post it as a howto.

---

### Post by getaceres on 2007-03-30
> **eode said:**
> After adding the ubuntu.beryl.org repository as mentioned in other messages, do the following:

```
sudo gedit /etc/apt/preferences
```
and add the following text.  I've heard you are not to have any blank lines at the beginning of the file, but I don't know if this is accurate.  Better  not to chance it.

```
Package: *
Pin: release o=lupine
Pin-Priority: 1001
```Then, if the beryl packages are already installed, do an update/upgrade.  Otherwise, install the package "beryl".

Finally, if you want to be able to force-install to an ubuntu version without it automatically downgrading to the beryl repositories in the future, go back in and change:

[FONT=Courier New]Pin-Priority: 1001[/FONT]

to:
[FONT=Courier New]Pin-Priority: 1000[/FONT]

You can remove this entire Package/Pin/Pin-Priority entry in the future to go back to 'normal' behaviour (f.e, if/when ubuntu comes out with a functional beryl-xgl).



Explanation of the entry in /etc/apt/preferences:
"Package: *" tells it to apply this to all packages in the repository.
"Pin: release o=lupine" tells it to we're choosing packages by origin "lupine" (which is the origin name beryl-project packages have)
"Pin-Priority: 1000" tells it to prefer the beryl repository to the ubuntu repository, but not so much that it downgrades from ubuntu packages if you have some already installed.  Setting to 1001 causes it to prefer beryl repositories to the ubuntu ones so much that it downgrades.
Setting it to 1000 is useful because you might want the newer beryl-manager, for example, even though you're using the older beryl.  With some finagling, you should be able to install the 2.1 version of most everything except beryl/beryl-core.

Thanks. Seeing that it won't be fixed and ATI won't support AIGLX in the near future, I don't think I would lower that value to 1000. I hope beryl developers don't make something strange with their packages that breaks some others...

---

### Post by eode on 2007-03-30
It's still OK to lower the value to 1000 - that's still within the range where it will *prefer* beryl-project packages to the Ubuntu ones.  It's just that if you manually install a package, using, for example, "Package" Menu/Force Version in Synaptic, it won't automatically downgrade it to the Beryl repositories on the next system update.  Using 1001 *insists* on the beryl version.  The reason you might still want to use 1000 is if you want to mix up the versions a bit.  This might lead to instability if there's some change in how the different programs/libraries interface with each other, but I think for the most part is a Good Thing(tm), and may even have the advantage of greater stability that newer versions may provide.  I, for example have a bunch of packages as 0.2.1, but the core beryl packages as 0.2.0.

---

### Post by payuco on 2007-04-25
> **PriceChild said:**
> Oh by the way... the Ubuntu packages will not support beryl-xgl in its current form for various reasons. Don't expect it to be fixed for feisty.


I had beryl-xgl working just fine before upgrading to feisty.  Now the command won't run and I don't have beryl.

---

