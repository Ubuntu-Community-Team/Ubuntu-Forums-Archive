---
title: "Edit Compiz settings w/o ccsm, possible?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by hictio on 2009-04-30
**Short**:
Where are the Compiz settings stored?
I want to edit a few of those without installing compizconfig-settings-manager (if that is possible)

**Long**:
I have Jaunty installed on a Compaq F700, everything is just golden and working just fine. Right now I have my "Visual Effects" set to "Normal", which is a nice middle ground for my current liking, at least at the moment.
But nevertheless, there are a few of the default enabled gizmos that I would like to tweak, or disable.

So is there a Compiz setting configuration file I can edit? I have searched on my $HOME as well as on /etc, but found nothing relevant.

As usual, TIA :D

---

### Post by Fifoxtasy on 2009-08-20
~/.gconf/compiz

but it's not a text file there are lots of .xml files in that folder.
editing it with a text editor is a pain, but certainly possible.

i would rather suggest you use gconf-editor (Configuration Editor in start menu under administration).



i don't know if you are using compiz with the "normal settings", maybe you are running Metacity. you can edit metacity configurations the same way. have fun.
i use the ccsm myself, i think it's great. there is also a simple compiz config program called simple-ccsm, you might want to check that out too. another suggestion: fusion-icon is a handy little program that let's you switch between window managers (compiz, metacity)

---

### Post by hictio on 2009-08-20
It has been a while, I have already installed ccsm, thanks nevertheless, but, I don't have that directory on my .gconf dir:

```

~$ ls -lsaht ~/.gconf/
total 20K
4.0K drwx------  5 esteban esteban 4.0K 2009-08-20 07:43 .
4.0K drwxr-xr-x 56 esteban esteban 4.0K 2009-08-20 03:42 ..
4.0K drwx------ 28 esteban esteban 4.0K 2009-07-20 20:09 apps
4.0K drwx------  4 esteban esteban 4.0K 2009-05-20 01:26 system
4.0K drwx------  3 esteban esteban 4.0K 2009-04-25 18:19 desktop

```

---

### Post by enli on 2009-08-20
I know this is not helpful comment but I couldn't stop wondering why you don't want to install ccsm?

~/.gconf/apps/compiz and
~/.gconf/apps/compizconfig

The settings are inside those folder trees, I believe.

---

### Post by hictio on 2009-08-20
> **enli said:**
> I know this is not helpful comment but I couldn't stop wondering why you don't want to install ccsm?

~/.gconf/apps/compiz and
~/.gconf/apps/compizconfig

The settings are inside those folder trees, I believe.

Thanks, it was just a wild idea, just to see if it was possible :) No big idea behind the whole thing.
As I stated on the Fifoxtasy reply, I had installed ccsm since opening this post.

---

### Post by mgmiller on 2009-08-23
You could try installing:
```
sudo apt-get install simple-ccsm
```

This will give you a very slimmed down but very useful gui front end for compiz.

If you have not installed the full ccsm, it will install it as a dependency.  

Look for it in System > Preferences > Simple CompizConfig Settings Manager

---

### Post by hictio on 2009-08-24
Thanks!
I'll give that one a shot on the next release.

---

### Post by hariks0 on 2009-12-16
Follow this link for a general idea.

[http://equivocation.org/node/88](http://equivocation.org/node/88)

---

