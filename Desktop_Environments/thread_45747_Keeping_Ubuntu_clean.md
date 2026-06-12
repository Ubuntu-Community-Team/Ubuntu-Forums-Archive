---
title: "Keeping Ubuntu clean"
date: 2005-07-01
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2005-07-01
It is now a couple of moths since I've installed Ubuntu, and I really like it, so now I mostly use linux. Being a linux newbie I didn't know exactly what applications would fit my needs, so I have installed and uninstalled a lot of things. In windows I would have been able to manually remove all the garbage which accumulates in the filesystem and in the registry. But I don't know linux a lot, so I had to rely on synaptic. The result is that:
1) Some packages which were marked for the complete uninstall didn't uninstall completely, and I can see their config files in my home, but I don't know if there are other files.
2) Often to install a package synaptic resolved its dependencies and installed a lot of other things. Then I removed the package, but all the dependencies were left.

I'd like to hear if someone has got any advice on how to regain control. My system now occupies about 3GB, which is a lot, in my opinion.

Thank you
Andrea

---

### Post by intangible on 2005-07-01
Look into "deborphan" it will find library packages without dependencies on your system.
Also, look into "localepurge"  it will save you lots of diskspace by deleting language files you don't need on your system.

When you dpkg --purge package  or remove with configuration files, that will not remove config files in home directories, only system-wide config files.  Also, if there are new files in the config directories, dpkg will not remove the non-empty directories after removing the package.

Also, try "sudo apt-get clean"  it will clear out your package cache now instead of waiting.

---

### Post by foxy123 on 2005-07-01
[QUOTE=Nonno Bassotto]
I'd like to hear if someone has got any advice on how to regain control. My system now occupies about 3GB, which is a lot, in my opinion.

Thank you
Andrea[/QUOTE]

mine is 3.7Gb

---

### Post by pdpi on 2005-07-01
After tons of crud, mine has ascended to 8 Gigs. But that includes quake 3 and ut2004...

---

### Post by Sionide on 2005-07-01
[QUOTE=intangible]Also, look into "localepurge"  it will save you lots of diskspace by deleting language files you don't need on your system.[/QUOTE]

Is localepurge as risky as it makes out to be in the description?? Looks useful but I don't want to accidentally muck anything up...

---

### Post by intangible on 2005-07-01
I've used localepurge since my days with Debian, never had any problems.  Just make sure you don't delete your primary language :D  en, en_US, en_US.utf8  are the ones I keep.   Never tried deleting en, so I don't know what would happen if someone did :confused:

---

### Post by Lunde on 2005-07-01
Here's a nice howto:
[http://ubuntuforums.org/showthread.php?t=24403](http://ubuntuforums.org/showthread.php?t=24403)

---

### Post by bw32 on 2005-07-01
my is 4.3G, you can also delete the configure files manually by using rm from a console

---

### Post by Nonno Bassotto on 2005-07-10
Thank you all. The HowTo seems really useful. Deborphan is nice; I was wondering if I could add it to the menus using Smeg. The problem is that the terminal windows closes as soon as the list is terminated, that is, half a second after I click. Is there a way to let the terminal open after the execution? For what concerns manual removal of the configure files: where do i find them? And which are safe to remove?

Andrea

---

### Post by gammyhand on 2005-07-15
[QUOTE=Nonno Bassotto]Thank you all. The HowTo seems really useful. Deborphan is nice; I was wondering if I could add it to the menus using Smeg. The problem is that the terminal windows closes as soon as the list is terminated, that is, half a second after I click. Is there a way to let the terminal open after the execution? For what concerns manual removal of the configure files: where do i find them? And which are safe to remove?

Andrea[/QUOTE]
 I am situation in the UK...what is my default language?? There are about a billion on deborphan!

---

### Post by doclivingston on 2005-07-15
[QUOTE=gammyhand]I am situation in the UK...what is my default language?? There are about a billion on deborphan![/QUOTE]
I'd leave "en", "en_UK" and "en_UK.UTF8", you *should* be fine removing the rest (unless you want another language).


I think this should also speed up loading Gnome slightly, due to gconfd not having to load all the translated schemas.

---

### Post by gammyhand on 2005-07-16
[QUOTE=doclivingston]I'd leave "en", "en_UK" and "en_UK.UTF8", you *should* be fine removing the rest (unless you want another language).


I think this should also speed up loading Gnome slightly, due to gconfd not having to load all the translated schemas.[/QUOTE]
 OK...where does deborhpan appear in my applications menu? Thanks for that advice :)

I would also like to know where localepurge appears ;)

---

### Post by intangible on 2005-07-20
When you install localepurge, it should've asked if you want it to run automatically after installing new applications, that's the best way to use it.

If you selected the wrong option **sudo dpkg-reconfigure localepurge** should re-set it up.

localepurge and deborphan are both meant to be ran from the command line, in a terminal.  So just open a terminal and type **sudo deborphan**  It only shows you libraries that aren't required by programs in your system, it doesn't remove them for you.  **man deborphan** should give you some insight.

---

### Post by gammyhand on 2005-07-21
[QUOTE=intangible]I've used localepurge since my days with Debian, never had any problems.  Just make sure you don't delete your primary language :D  en, en_US, en_US.utf8  are the ones I keep.   Never tried deleting en, so I don't know what would happen if someone did :confused:[/QUOTE]
Well as I have just deleted en by mistake I will let you know what happens a bit later  :grin:

---

### Post by gammyhand on 2005-07-21
[QUOTE=gammyhand]Well as I have just deleted en by mistake I will let you know what happens a bit later  :grin:[/QUOTE]
 How does one re-install a language??

---

### Post by gammyhand on 2005-07-21
[QUOTE=gammyhand]How does one re-install a language??[/QUOTE]
 Running localepurge configure got it back...I don't have the balls to restart without en installed :)

Sudo deborphan gives me this:

ralph@ralph:~$ sudo deborphan
libdivx4linux
gstreamer0.8-lame
gstreamer0.8-ffmpeg
ralph@ralph:~$
ralph@ralph:~$

Surely I need the divx library? How reliable is deborphan? Maybe it is what deleted something crucial to GAIM (I had to reformat and reinstall to get GAIM to sign in to msn again).

---

### Post by intangible on 2005-07-25
deborphan only tells you what libraries are required by programs on your system, libdivx4linux isn't "required" by any programs on your system, but maybe it is "required" by you.  That's why it doesn't remove anything, only tells you what you have that nothing explicitly needs.  If you do a lot of development, you'd see lots of libraries there.

---

### Post by ubuntp on 2005-07-25
A better way to use deborphan is through synaptic, Make a custom search filter only checking "orphaned (requires deborphan)". Now when you click on custom and then search it will show all packages deborphan found and you can easily remove them or find out more about them.

---

### Post by matthew on 2005-07-27
Great idea! Thanks.
> A better way to use deborphan is through synaptic, Make a custom search filter only checking "orphaned (requires deborphan)". Now when you click on custom and then search it will show all packages deborphan found and you can easily remove them or find out more about them.

---

