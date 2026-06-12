---
title: "Accidentally installed wrong version of ubuntu tweak, Now I can't remove it."
date: 2009-09-14
forum: Desktop Environments
---

### Post by Truckerpunk on 2009-09-14
Hi. I need help: 

I accidentally installed the version of ubuntu tweak for Karmic on my Jaunty distro, and it has messed up my menu's. Not that bad, just made them semi-transparent, but still annoying. So i wanted to remove it again, by typing;

$ sudo apt-get remove --purge ubuntu-tweak

And I get an error: 
 
Do you want to continue [Y/n]? y
(Reading database ... 232262 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas how to get rid of this foul presence? Thanks in advance. 

Cheers.

---

### Post by hal10000 on 2009-09-14
i suggest you open synaptic and look for broken packages (on the right side click on [COLOR="Red"]userdefined[/COLOR] Filters and then look into [COLOR="Red"]broken[/COLOR] packages. if you can find it there, then right-click on the package and choose reinstall.
If you can't find it there then search for ubuntu-tweak and reinstall it.

---

### Post by steveneddy on 2009-09-14
> **Truckerpunk said:**
> Hi. I need help: 

I accidentally installed the version of ubuntu tweak for Karmic on my Jaunty distro, and it has messed up my menu's. Not that bad, just made them semi-transparent, .

From the ubuntu tweak web page:


[LIST]
[*]> Compiz Fusion settings, Screen Edge Settings, Window Effects Settings,**  Menu Effect Settings**
[/LIST]
Yet you call it a **foul presence**?
You didn't read about it **before** installation?

[COLOR=Red]**Do you have CCSM installed?**[/COLOR]

You can get rid of the transparencies using CCSM if you know where to look.

try this to uninstall:

[http://ubuntuforums.org/showpost.php?p=7037172&postcount=4](http://ubuntuforums.org/showpost.php?p=7037172&postcount=4)

```
sudo dpkg -r ubuntu-tweak
```

---

### Post by Truckerpunk on 2009-09-14
I can't reinstall it from synaptic.. I can only choose "mark for removal" or "mark for complete removal" witch just gives the error described, as does the suggested terminal-command. "Foul presence" might be a bit harsh.. Sorry 'bout that, but I just don't like transparent menus. I do have CCSM installed... But I don't see anything that has anything to do with the menus. (I do not have opacity enabled). Unfortunately. No luck so far. Thanks for your suggestions though. I'll keep on looking for a solution, or perhaps wait 'till Karmic, install that, and then remove ubuntu-tweak...  Witch seems like bit off a detour.

---

### Post by steveneddy on 2009-09-14
> **Truckerpunk said:**
> I can't reinstall it from synaptic.. I can only choose "mark for removal" or "mark for complete removal" **witch** just gives the error described, as does the suggested terminal-command. "Foul presence" might be a bit harsh.. Sorry 'bout that, but I just don't like transparent menus. I do have CCSM installed... But I don't see anything that has anything to do with the menus. (I do not have opacity enabled). Unfortunately. No luck so far. Thanks for your suggestions though. I'll keep on looking for a solution, or perhaps wait 'till Karmic, install that, and then remove ubuntu-tweak...  **Witch** seems like bit off a detour.

1. the word is spelled which, not witch

2. open CCSM and go to the Opacity, Brightness and Saturation plugin

change or delete the circled settings I have circled in my pic

I think that is where Ubuntu Tweak puts the settings

some folks like transparent menus (I do) others don't

This is the place where you control those settings

If you want to install a different version - completely uninstall the previous version and install the correct version

---

### Post by Truckerpunk on 2009-09-14
Hey again. I got rid of tweak by manually deleting some files. But the transparent menus are still here.... Damn it. My CCSM doesn't look like yours, and I don't have a Opacity, Brightness and Saturation-tab. Only an Opacity-tab, and that isn't enabled. strange and annoying. Where did you install you CCSM from? 

Thanks for helping out.

---

### Post by Truckerpunk on 2009-09-14
tried some more now. Enabled Opacity in CCSM, and set the values for the windows that are now transparent to 100, but they are still transparent. Looks like I'll have to live with these menus. Or perhaps I've put the wrong window-types in, but I'm pretty sure that should be it. Damn it. Running out of ideas here.

---

### Post by steveneddy on 2009-09-14
From your snapshot on post #6

I circled it

go in there and change the values there

---

### Post by Truckerpunk on 2009-09-14
Sorry mate... Blind and tired. (It's 5 O'clock in the morning here). Well.. I got it fixed. I installed the correct version of Tweak, and found a way to disable the transparency from there. Appreciate your help. Finally nice solid menus!!! Yeah!!

---

### Post by steveneddy on 2009-09-14
> **Truckerpunk said:**
> Sorry mate... Blind and tired. (It's 5 O'clock in the morning here). Well.. I got it fixed. I installed the correct version of Tweak, and found a way to disable the transparency from there. Appreciate your help. Finally nice solid menus!!! Yeah!!

Glad I could help.

Now go get some sleep.

I'm a trucker, too, in the US.

Live in Texas but hanging in Kansas tonight and will be in Illinois tomorrow nite.

---

### Post by Truckerpunk on 2009-09-14
I will... Keep on truckin'!!

---

