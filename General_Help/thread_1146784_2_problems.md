---
title: "2 problems"
date: 2009-05-02
forum: General Help
---

### Post by Ness10122 on 2009-05-02
Ok so when I try to install a .deb file I get the error that says: Wrong Architecture 'i386' and I have installed everything through terminal so far. Is there a way I can install the Atlantis plugin and Virtual Box through terminal? Thanks:)

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> Ok so when I try to install a .deb file I get the error that says: Wrong Architecture 'i386' and I have installed everything through terminal so far. Is there a way I can install the Atlantis plugin and Virtual Box through terminal? Thanks:)

Your running 64bit i guess?

---

### Post by doas777 on 2009-05-02
you have the wrong version of the installer for your version of ubuntu. i386 is 32bit whereas x86_64 is for 64 bit systems. you can install 32 bit software on a 64bit system, but you cannot install 64bit softeware on a 32 bit one.

good luck

---

### Post by doas777 on 2009-05-02
> **garythegoth said:**
> Your running 64bit i guess?
that should work fine. I believe he has 64 bit software and a 32 bit system. the error message is stating the system found not the one looked for.

---

### Post by Ness10122 on 2009-05-02
> **doas777 said:**
> you have the wrong version of the installer for your version of ubuntu. i386 is 32bit whereas x86_64 is for 64 bit systems. you can install 32 bit software on a 64bit system, but you cannot install 64bit softeware on a 32 bit one.

good luck


I have an amd64 so I downloaded that version of virtual box and it worked. (Never knew my processor supported 64bit o_o) anyways back to the atlantis plugin now. Help please? There was never a .deb in the first place but I don't know how to install it since I just got a tar.gz file

---

### Post by doas777 on 2009-05-02
> **Ness10122 said:**
> Ok so when I try to install a .deb file I get the error that says: Wrong Architecture 'i386' and I have installed everything through terminal so far. Is there a way I can install the Atlantis plugin and Virtual Box through terminal? Thanks:)
check out this install guide for vbox
[http://www.howtoforge.com/virtualbox_ubuntu]("https://help.ubuntu.com/community/VirtualBoxhttp://ubuntuforums.org/newreply.php?do=newreply&p=7201856")

---

### Post by garythegoth on 2009-05-02
> **doas777 said:**
> that should work fine. I believe he has 64 bit software and a 32 bit system. the error message is stating the system found not the one looked for.

Not really. I tried to install Skype on 64bit 8.04. The only way to do it was by forcing the install.

@the OP, if you want to force an install to run "sudo apt-get -f install xxx"

xxx represneting the name of the thing/program you want to install.

---

### Post by Ness10122 on 2009-05-02
now that I installed it, how do I open it?

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> now that I installed it, how do I open it?

VirtualBox?

---

### Post by Ness10122 on 2009-05-02
by it, I meant WINE and virtualbox

---

### Post by Ness10122 on 2009-05-02
I also installed compix fusion. How do I open that? Restart?

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> I also installed compix fusion. How do I open that? Restart?

What? No! This isnt Windows 95!

---

### Post by doas777 on 2009-05-02
ok, wine does not open by itself. you run a windows program "through" wine. you can find it's configuration in your applications menu. if you look at your systems tools menu, you should find virtual box.

if you can't find it, use Alt + F2 and enter "virtualbox"

your compiz settings are in the System->Preferences -> Appearence
if you want advanced controls, you need to install the gnome-compiz-settings-manager
(search in synaptic for compiz settings)

---

### Post by Ness10122 on 2009-05-02
> **doas777 said:**
> ok, wine does not open by itself. you run a windows program "through" wine. you can find it's configuration in your applications menu. if you look at your systems tools menu, you should find virtual box.

if you can't find it, use Alt + F2 and enter "virtualbox"

your compiz settings are in the System->Preferences -> Appearence
if you want advanced controls, you need to install the gnome-compiz-settings-manager
(search in synaptic for compiz settings)
ok, last question:

how do you install tar.gz files?

---

### Post by Ness10122 on 2009-05-02
also when I open an exe I get this error:

[/home/brian/Documents/CombatArmsSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/brian/Documents/CombatArmsSetup.exe or
          /home/brian/Documents/CombatArmsSetup.exe.zip, and cannot find /home/brian/Documents/CombatArmsSetup.exe.ZIP, period.

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> also when I open an exe I get this error:

[/home/brian/Documents/CombatArmsSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/brian/Documents/CombatArmsSetup.exe or
          /home/brian/Documents/CombatArmsSetup.exe.zip, and cannot find /home/brian/Documents/CombatArmsSetup.exe.ZIP, period.

Tar.gz files are like zip files.

---

### Post by Ness10122 on 2009-05-02
> **garythegoth said:**
> Tar.gz files are like zip files.

I know that but I don't know how to install them. also are tar.gz2 the same?

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> I know that but I don't know how to install them. also are tar.gz2 the same?

What is the file/program your trying to install?

---

### Post by Ness10122 on 2009-05-02
> **garythegoth said:**
> What is the file/program your trying to install?


the first one is dolphin 64 bit

2nd one is atlantis

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> the first one is dolphin 64 bit

2nd one is atlantis

What is this Atlantis thing? And by Dolphin I take you mean the file manager?

---

### Post by Ness10122 on 2009-05-02
> **garythegoth said:**
> What is this Atlantis thing? And by Dolphin I take you mean the file manager?


the atlantis plugin
[http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

and no, dolphin the emulator
[www.dolphin-emu.com](www.dolphin-emu.com)

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> the atlantis plugin
[http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

and no, dolphin the emulator
[www.dolphin-emu.com]("http://www.dolphin-emu.com")

Oh the compiz fish thing ok, I didnt know it was called that.

As for Dolphin the **Gamecube** emulator I guess you have to compile it.

---

### Post by Ness10122 on 2009-05-02
> **garythegoth said:**
> Oh the compiz fish thing ok, I didnt know it was called that.

As for Dolphin the **Gamecube** emulator I guess you have to compile it.


ok well how do I compile it? (it also emulates wii btw xD) and what do I do with the atlantis plugin?

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> ok well how do I compile it? (it also emulates wii btw xD) and what do I do with the atlantis plugin?

To be honest I dont know. I never use Compiz. 

As for the Dolphin thing, Ill take a look and report back in a minute...

---

### Post by Ness10122 on 2009-05-02
> **doas777 said:**
> ok, wine does not open by itself. you run a windows program "through" wine. you can find it's configuration in your applications menu. if you look at your systems tools menu, you should find virtual box.

if you can't find it, use Alt + F2 and enter "virtualbox"

your compiz settings are in the System->Preferences -> Appearence
if you want advanced controls, you need to install the gnome-compiz-settings-manager
(search in synaptic for compiz settings)


when I typed in virtualbox, it said It couldn't find it

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> when I typed in virtualbox, it said It couldn't find it

Are you using the normal Ubuntu with gnome?

If so go to Applications=>System Tools=>VirtualBox

The Dolphin thing looks like it needs some old lib files. Which means you may have to hunt round for them. I dont know though sorry.

---

### Post by Ness10122 on 2009-05-02
> **garythegoth said:**
> Are you using the normal Ubuntu with gnome?

If so go to Applications=>System Tools=>VirtualBox

The Dolphin thing looks like it needs some old lib files. Which means you may have to hunt round for them. I dont know though sorry.


Nevermind I did a restart and it works.

---

### Post by garythegoth on 2009-05-02
> **Ness10122 said:**
> Nevermind I did a restart and it works.

That is seriously weird. What version of Ubuntu are you using?

---

### Post by Ness10122 on 2009-05-02
> **doas777 said:**
> ok, wine does not open by itself. you run a windows program "through" wine. you can find it's configuration in your applications menu. if you look at your systems tools menu, you should find virtual box.

if you can't find it, use Alt + F2 and enter "virtualbox"

your compiz settings are in the System->Preferences -> Appearence
if you want advanced controls, you need to install the gnome-compiz-settings-manager
(search in synaptic for compiz settings)

what's synaptic and how do I get it?

---

### Post by Ness10122 on 2009-05-03
I just got gnome compiz manager 0.9.14 and I don't know how to compile it (its a tar.gz)

---

### Post by Ness10122 on 2009-05-03
also how do I get a 'skydome' as referenced here
[B][http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

[/B]I want my ubuntu to be just like his :P

---

### Post by Ness10122 on 2009-05-03
> **garythegoth said:**
> That is seriously weird. What version of Ubuntu are you using?
I put it in my profile now :P

---

### Post by Ness10122 on 2009-05-03
and could someone with compiz experience tell me how to install the atlantis 'fish thingy' plugin?
[http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

---

### Post by Ness10122 on 2009-05-03
help please

---

### Post by Ness10122 on 2009-05-03
PLEASE someone help

---

