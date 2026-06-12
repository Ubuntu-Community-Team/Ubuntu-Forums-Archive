---
title: "GNOME Do 0.8.1 on Ubuntu 8.04?"
date: 2009-03-17
forum: General Help
---

### Post by jespdj on 2009-03-17
Has anyone got GNOME Do 0.8.1 working on Hardy (64-bit)?

The version in the Ubuntu repository for Hardy is old (0.4.0.1). So I tried [installing from the PPA](http://do.davebsd.com/wiki/index.php?title=Installing_Do), but that's also old (0.5.99 or something). So then I tried compiling it myself, but it needs a package named gnome-keyring-sharp which does not seem to exist in the Ubuntu repository.

Is there a build of GNOME Do 0.8.1 for Hardy (64-bit)?

---

### Post by treesurf on 2009-03-18
Same question here, but looking for 32-bit instead.

---

### Post by scottuss on 2009-03-18
[http://packages.ubuntu.com/source/hardy/gnome-keyring-sharp]("http://packages.ubuntu.com/source/hardy/gnome-keyring-sharp")

Looks like there is a package for it, it's in Universe.

I'd take a look but I'm not using Ubuntu...

Edit: just realised the source is on that page I linked, so you could just compile that

---

### Post by jespdj on 2009-03-18
> **scottuss said:**
> [http://packages.ubuntu.com/source/hardy/gnome-keyring-sharp]("http://packages.ubuntu.com/source/hardy/gnome-keyring-sharp")

Looks like there is a package for it, it's in Universe.
But it's not a built *.deb package, it's only sources to build a *.deb. For some reason there is no *.deb for this in the repository. :confused:

---

### Post by igor. on 2009-03-18
There's a ppa.

[http://do.davebsd.com/wiki/index.php?title=Installing_Do#8.10_.28Intrepid.29](http://do.davebsd.com/wiki/index.php?title=Installing_Do#8.10_.28Intrepid.29)

---

### Post by treesurf on 2009-03-18
I don't know how I didn't see that!  Thank you!

---

### Post by treesurf on 2009-03-19
The PPA only installs version 0.6.1.0 for Hardy.  This does not include Docky which is the whole reason I wanted to install Gnome-Do. :(

Any suggestions on how to get version 0.8.1, or am I out of luck?

---

### Post by Yellow Pasque on 2009-03-19
> **jespdj said:**
> So then I tried compiling it myself, but it needs a package named gnome-keyring-sharp which does not seem to exist in the Ubuntu repository.

Try this before compiling:
```
sudo apt-get libgnome-keyring-dev libgnome-keyring1.0-cil
```

---

### Post by scottuss on 2009-03-19
> **treesurf said:**
> The PPA only installs version 0.6.1.0 for Hardy.  This does not include Docky which is the whole reason I wanted to install Gnome-Do. :(

Any suggestions on how to get version 0.8.1, or am I out of luck?

I'm not overly fussed about the whole dock thing but I find Docky to be very nice, I can see why you want it! :)

---

### Post by jersoncito on 2009-04-02
We need Gnome Do 0.8.1 (64 bit) in Hardy, please.....

I found for Hardy 64 bit only the versions 0.5.99 (PPA) 0.6.0.0 (Get deb) 
I tried to install the Intrepid and Jaunty versions on Hardy. No luck at all.
The people who is still using Hardy want Gnome Do 0.8.1 Please...please, please...
I want it. :(

---

### Post by Yellow Pasque on 2009-04-03
I tried building on a fresh, updated Hardy install, and I figured out all the dependencies and got the configure command to complete successfully. I also needed this .deb: [http://packages.debian.org/lenny/all/libnotify0.4-cil/download](http://packages.debian.org/lenny/all/libnotify0.4-cil/download)

Unfortunately, I'm getting errors in the make process and I'm too tired to troubleshoot them now.

I'll let you know if I figure anything out.

---

### Post by 2dvisio on 2009-04-15
Not compiling also for me:

This just for sake of completeness is the error:

> Compiling Do.exe...
./src/Do.UI/PluginNodeView.cs(170,45): error CS0266: Cannot implicitly convert type `System.Collections.Generic.HashSet<string>' to `System.Collections.Generic.ICollection<string>'. An explicit conversion exists (are you missing a cast?)
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [../build/Do.exe] Error 1
make[1]: Leaving directory `/home/carmelo/Downloads/gnome-do/gnome-do-0.8.1/Do'
make: *** [all-recursive] Error 1
carmelo@abarth3:~/Downloads/gnome-do/gnome-do-0.8.1$ gedit ./src/Do.UI/PluginNodeView.cs


Is a problem of casting not solved (at least it seems), the line of code is the following:

```
ICollection<string> seen = new HashSet<string> ();
```

Has you can see HashSet is different from ICollection so I think also a cast would be needed... or I'm wrong?

Thanks.

Carmelo

---

### Post by 666porcondissaum on 2009-05-21
Gnome Do 0.8.1 + Docky on Hardy Heron 8.04 with no needing of compiling or .deb:

Enable the repository shown in the site below:

[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

Update and Reboot. Doesn't matter if Gnome 0.6* is installed or not. (Maybe if it isn't you'll need to do so... I really don't know). Thks!

---

