---
title: "dpkg Error"
date: 2009-02-02
forum: General Help
---

### Post by lms5yc13 on 2009-02-02
Hi,

I am trying to get my wireless card to work via the Hardware Updater and whenever I try to "enable" the card I get some error saying, "E: dpkg was interrupted, you must manually run 'dpkg --config -a' to correct the problem. 
E:_cache->open() failed, please report."

Does anyone know what this means and how I can go about fixing this error? I'm new to Ubuntu so you'll have to spell everything out for me, sorry : / Thanks for the help!

---

### Post by Crafty Kisses on 2009-02-02
Have you tried running the following?
```
sudo dpkg --config -a
```

---

### Post by lms5yc13 on 2009-02-02
It gives the option to open 'aptitude' but I don't really know what to do from there. I don't really know what error even means...

---

### Post by DirtDawg on 2009-02-02
Yes, open the teminal via applications>teminal and copy/paste the command codename suggested .

---

### Post by lms5yc13 on 2009-02-02
That didn't make much sense. What do you mean by "command codename?" Keep in mind I know NOTHING about Ubuntu. Except for the fact that it keeps giving me this error when I try and download and install anything. If you can give an example of what you're talking about that would be swell.

---

### Post by DirtDawg on 2009-02-02
> **lms5yc13 said:**
> That didn't make much sense. What do you mean by "command codename?" Keep in mind I know NOTHING about Ubuntu. Except for the fact that it keeps giving me this error when I try and download and install anything. If you can give an example of what you're talking about that would be swell.

Okay,  codename is the name of the first forum member who answered you. The command is the one in he posted in the grey box (er,  he or she). Copy that command and paste it into the teminal you open through applications>accesories>teminal. This should fix your error and you can continue with what you were doing.

---

### Post by lms5yc13 on 2009-02-02
Ok well I've tried that but it didn't really do much for me. I it gives me other options with this dpkg. Like I can run aptitude, or get help (which ironically didn't help), and I can do other things that didn't make much sense. This is what I get when I run that command.

"Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
I'm not really sure what is even causing this error, or what it means for that matter. I tried to run aptitude but I don't know where to go from there.

---

### Post by taurus on 2009-02-02
Shouldn't it be

```
sudo dpkg **--configure** -a
```

---

### Post by DirtDawg on 2009-02-02
> **taurus said:**
> Shouldn't it be

```
sudo dpkg **--configure** -a
```
Yes, Taurus is correct (thank you). I didn't look closely enough at the original command post, sorry about that. 

When you run this, you will be prompted for your password. You may also see a small grey gear-looking icon for a minute or two, but no need to click it. That is there to indicate your package manager is working. When it is finished you should be able to finish whatever project you started before this error.

Your package manager is what installs and uninstalls programs onto your computer. Normally, you will not need to use the dpkg command from a terminal, but instead use the menu option Applications>Add/Remove.

---

