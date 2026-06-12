---
title: "kontact Questions"
date: 2005-04-26
forum: Desktop Environments
---

### Post by jhuff on 2005-04-26
Have have a few questions on kontact.

I can not get the spell checker to work.  I receive the follow error:
"ISpell/Aspell could not be started. Please make sure you have ISpell or Aspell properly configured and in your PATH."

Every time I click on a web link konqueror starts up.  I would like to make Firefox be the default browser.

Any suggestions?

---

### Post by Morgoth on 2005-04-27
Not sure about the spell checker, but you can change your default web browser in KDE by opening 
Control Center->KDE Components->Component Choser
On the right hand side click on Web Browser, then choose the mighty Firefox

---

### Post by jhuff on 2005-04-27
Thanks,

I got firefox setup as the default now.  I still can not figure out what is wrong with the spell checker.  Other than that I think kontact works great.

---

### Post by troywill1 on 2005-04-27
[QUOTE=jhuff]Have have a few questions on kontact.

I can not get the spell checker to work.  I receive the follow error:
"ISpell/Aspell could not be started. Please make sure you have ISpell or Aspell properly configured and in your PATH."

Every time I click on a web link konqueror starts up.  I would like to make Firefox be the default browser.

Any suggestions?[/QUOTE]
 You don't have ISpell/ASpell installed, most likely, they are not installed by default.  Use Synaptic/Kynaptic to install ISpell (or Aspell, whatever) and Kontact will start to work auto-magically,  Hope this helps.

Troy

---

### Post by thumper on 2005-05-06
[QUOTE=troywill1]You don't have ISpell/ASpell installed, most likely, they are not installed by default.  Use Synaptic/Kynaptic to install ISpell (or Aspell, whatever) and Kontact will start to work auto-magically,  Hope this helps.

Troy[/QUOTE]
Hmm...  I have the same problem but I have aspell installed.

[INDENT]tim@spike:~$ type aspell
aspell is /usr/bin/aspell[/INDENT]

---

### Post by jhuff on 2005-06-02
All I needed to do was install ispell and everything works great.  aspell had been installed but kmail must need ispell in order to work.

---

### Post by thumper on 2005-06-03
[QUOTE=jhuff]All I needed to do was install ispell and everything works great.  aspell had been installed but kmail must need ispell in order to work.[/QUOTE]

Thanks.  I might try that when I get back home.

Edit:  Yep, that worked.  I wonder why it mentions aspell in the message if it doesn't look for it?

---

### Post by PremiumName on 2008-05-22
This is a strange KDE-on-Debian bug. (I am not sure about it&#8217;s status, but it is definitely broken in Debian stable.)

To use Aspell without having ISpell installed, you have to do the following:

# aptitude install aspell aspell-en
# aptitude install ispell ibritish

Then you have to go to Spell check under Components in KControl, and select an Aspell dictionary as your default dictionary.

Then you can clean up by running:

# aptitude remove ispell ibritish

For some reason, KDE relies on ISpell to detect Aspell dictionaries. I do not know why, and have not been able to figure out of it either. If you make KDE aware of Aspell&#8212;by choosing it as KDE&#8217;s spell checking engine when ISpell is installed&#8212;you can safely remove ISpell afterward.

---

