---
title: "KleanSweep and junk cleaning"
date: 2009-03-02
forum: General Help
---

### Post by Paskinel on 2009-03-02
Related to **[COLOR="DarkRed"]Ubuntu 8.10[/COLOR]**:

1) Which are the [COLOR="Red"]Safe-to-Delete[/COLOR]
entries that **KleanSweep** finds?
In other words, which items should I check
[COLOR="Red"]_before_[/COLOR] **KleanSweep** begins Searching for junk files?

2) Is **KleanSweep** enough by itself
or should I use another program? Which one?

3) Are there any ready-made commands for junk-file cleaning
I can run through the Terminal?

---

### Post by Rallg on 2009-03-02
I presume you ran

sudo apt-get autoremove

which gets rid of some packages that are not needed in your system. You can also use Synaptic to get the "deborphan" package. When you run deborphan from Terminal, it looks for other files that are not needed.

Unless you are very tight on space, that is probably not worth your effort. But if you have Ubuntu on a 4Gb Dell mini 9, it might be worth it.

However, the above methods do not look for things such as backup copies of edited files, or other items that might store privacy information.

---

### Post by Paskinel on 2009-03-02
> **Rallg said:**
> You can also use Synaptic to get the "deborphan" package. When you run deborphan from Terminal, it looks for other files that are not needed.

How can I use Synaptic to get the "deborphan" package?
Sorry, but I'm New to Ubuntu...

---

### Post by Rallg on 2009-03-02
In the System menu, go to Administration, Synaptic Package Manager. This feature comes with Ubuntu, so it should be there (not sure about variants such as Kubuntu or Xubuntu - it might be called something else).

Synaptic is a program that shows a list of available stuff. If you don't know what you want, you can search by name or description. Synaptic will attempt to match partial spelling. So you can search for a package named "deborphan". If you did not kinow the correct spelling, searching for "debor" would also give the result (and maybe others).

When you use Synaptic to add a package, it will also advise you regarding support files that must be added.

After installing deborphan, open a Terminal, like this:

yourname@yourcomputer:~$ deborphan

Back will come a list of files (if any) that are installed, but are not used by any application you have. These files can be removed:

yourname@yourcomputer:~$ sudo apt-get remove an-orphan-file another-orphan and-so-forth

where you would put the various file names discovered by deborphan.

The autoremove and deborphan are not privacy tools. They do not look for backup copies of your own documents (which may be hidden). They do not make file information unrecoverable. They only look for installed system files that serve no purpose in your setup, and make the space free.

In my earlier post, I referred to autoclean and clean. When you install something, you download an installer package (in many cases). After the installer runs, it may leave behind the download, which is not longer needed unless you intend to reinstall that package. If you need the extra space, using autoclean and clean removes the leftover downloads.

---

### Post by Paskinel on 2009-03-02
> **Rallg said:**
> In the System menu, go to Administration, Synaptic Package Manager. This feature comes with Ubuntu, so it should be there (not sure about variants such as Kubuntu or Xubuntu - it might be called something else).

Synaptic is a program that shows a list of available stuff. If you don't know what you want, you can search by name or description. Synaptic will attempt to match partial spelling. So you can search for a package named "deborphan". If you did not kinow the correct spelling, searching for "debor" would also give the result (and maybe others).

When you use Synaptic to add a package, it will also advise you regarding support files that must be added.

After installing deborphan, open a Terminal, like this:

yourname@yourcomputer:~$ deborphan

Back will come a list of files (if any) that are installed, but are not used by any application you have. These files can be removed:

yourname@yourcomputer:~$ sudo apt-get remove an-orphan-file another-orphan and-so-forth

where you would put the various file names discovered by deborphan.

The autoremove and deborphan are not privacy tools. They do not look for backup copies of your own documents (which may be hidden). They do not make file information unrecoverable. They only look for installed system files that serve no purpose in your setup, and make the space free.

In my earlier post, I referred to autoclean and clean. When you install something, you download an installer package (in many cases). After the installer runs, it may leave behind the download, which is not longer needed unless you intend to reinstall that package. If you need the extra space, using autoclean and clean removes the leftover downloads.

Thank you!!! =D>
:P

---

### Post by Rallg on 2009-03-02
Also, you can run deborphan several times. Each time you remove some unnecessary files, there may be additional unnecessary files - they could not be removed the first time.

---

