---
title: "How to uninstall compiz fusion"
date: 2007-08-02
forum: Desktop Environments
---

### Post by tmt345 on 2007-08-02
i decided i dont want compiz fusion it worked kinds of slow for me so please give uninstall instructions and if you can. instructions how to get back desktop effects (because that worked fine) because i had to uninstall it for compiz fusion. oh and im running ubuntu feisty and im still a little new to linux:) so try to give easyish instructions

thanks :)

---

### Post by ThrobbingBrain66 on 2007-08-02
What did you use to install Compiz Fusion?  If you used Trevino's repo, just go into synaptic, search for compiz, and completely remove anything related to it.  After that, remove trevino's repo from your sources. list file and type in a terminal:
```
sudo apt-get update
```

Then go back into synaptic and reinstall desktop-effects.  This should pull in all the packages you need to get regular compiz back.

---

### Post by tmt345 on 2007-08-02
thanks :):):)

---

### Post by sheds on 2007-11-07
Is there an apt-get way to get compiz uninstalled? The howto to install compiz-fusion in gutsy is very simple, like 3 steps and that's it. Can i just roll back on those steps??? Or does that erase things that were there before compiz-fusion got installed?

Thanks for the help.

---

### Post by justinlawrence on 2008-06-02
regarding how to remove stuff with aptitude:

to find packages use:

aptitude search yyy 

and to remove a package:

aptitude remove yyy

or to install a package:

aptitude install yyy


i've had the same problems. i figured i'd try get my laptop looking amazing as a walking advert to all those around me of the amazingness that is linux. i thought compiz might do a great job of impressing them (and hopefully swaying more of them to consider linux), but wow, what frustrating effort this has been.

i've gotten to the point that my windows have lost their decoration as well as my alt-tab cycles through windows and has no preview, rather than it's normal method.

thanks throbbingbrain66, i've tried the aptitude install desktop-effects-kde (which was the closest thing to destkop-effects that apt had) and it hasn't restored the original behaviour.

does anyone know which files to remove / restore to get kubuntu back to it's original behaviour. i chose the debian model of package management and upgrades because i loved the way you never have to reinstall, but it looks like a reinstall might be the quickest way?

thanks a bunch

---

### Post by rated_emman on 2008-06-18
> **ThrobbingBrain66 said:**
> What did you use to install Compiz Fusion?  If you used Trevino's repo, just go into synaptic, search for compiz, and completely remove anything related to it.  After that, remove trevino's repo from your sources. list file and type in a terminal:
```
sudo apt-get update
```

Then go back into synaptic and reinstall desktop-effects.  This should pull in all the packages you need to get regular compiz back.

hey i tried to install the compiz fusion and it messed up my desktop-effects.. now i want it back.. i took all the compiz thingy out as u said and run the code.... 

but when i try to install it, it gives me this :(

```
E: python2.4-minimal: subprocess post-installation script returned error exit status 1
E: python2.4: dependency problems - leaving unconfigured
E: python-all: dependency problems - leaving unconfigured
E: python2.4-dev: dependency problems - leaving unconfigured
E: python-all-dev: dependency problems - leaving unconfigured
```


i need help desperately :(

---

