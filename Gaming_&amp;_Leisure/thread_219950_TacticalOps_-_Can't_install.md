---
title: "TacticalOps - Can't install"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by Sciamano on 2006-07-20
Hello everybody.
I received my copy of TacticalOps this morning, so I tried to install it on my Ubuntu Linux box.
I used the files that I found [here]("http://icculus.org/%7Eravage/tacticalops/") as installer (the european files, since I've got a European CD).

I launch "sudo sh ./tacticalops-3.1.9-install-x86.run" and this is what happens:

```
luca@luca-desktop:~/TacticalOps$ sudo sh ./tacticalops-3.1.9-install-x86.run
Verifying archive integrity... All good.
Uncompressing Tactical Ops: Assault On Terror for Linux (European Version)............................................................................

Extracting Tactical Ops files
```
The installer loads, it asks me for the directories where I want to install. I select /usr/local/games/TacticalOps and hit "install".
At this stage, a Cedega window opens! Why's that?
I obviously close it, since I don't want TacOps to run in Cedega, and this is what happens next:

```
mv: cannot move `/tmp/selfgz2902129644/fail/tacticalops' to `TACTICALOPS_SETUP/bin/Linux/x86/glibc-2.1/tacticalops': No such file or directory
mv: cannot move `/tmp/selfgz2902129644/fail/ucc' to `TACTICALOPS_SETUP/bin/Linux/x86/glibc-2.1/ucc': No such file or directory
Unable to find file 'System'
Unable to find file 'TacticalOps'
Unable to find file 'Web'

```
The installer ignores all this and go to the end. But then, if I try to launch the game this is what happens:

```
dirname: missing operand
Try `dirname --help' for more information.
Couldn't run Tactical Ops: Assault On Terror (to-bin). Is TO_DATA_PATH set?
```
What went wrong? Any suggestion?


**-------EDIT---------**

I found this in a FAQ:

> Q) During installation, I get some error in my shell and then this:
Unable to find file 'System'
Unable to find file 'Textures'
Unable to find file 'TacticalOps'
Unable to find file 'Web'

A) This currently applies to the European installer only, or the old USA installer. You will have to install wine from here or here. If you have wine, winex or cedega installed, it will be used instead of the binaries I include with the installer. Once you have installed either wine, winex or cedega, you should be able to run the installer sucessfully.
Problem is that even if both Cedega and Wine are installed on my system, it won't change.

I tried with the following

```
export WINE_EXEC=/usr/bin/wine
sudo sh ./tacticalops-3.1.9-install-x86.run
```
To make the installer use wine, but still I get the same errors as before.

Please help!
Thanks a lot.
Luca

---

### Post by vem0m on 2006-07-20
another thing u might try is running it and telling it to install into ur home directory somewhere that way u don't need to use sudo and the settings for ur user account will be used :)

---

### Post by Sciamano on 2006-07-21
ven0m, I tried that but the errors are the same.
It looks like the problem is Wine/Cedega. Cedega starts with the setting wizard, and does not seem to do the operations required by TacticalOps. Wine does not even seem to work, at least nothing visible happens.

---

