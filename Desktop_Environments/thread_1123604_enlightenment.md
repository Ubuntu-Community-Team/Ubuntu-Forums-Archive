---
title: "enlightenment?"
date: 2009-04-12
forum: Desktop Environments
---

### Post by mtgmutton on 2009-04-12
I just switched to E16 :)

but I can't figure out some things... :(

I've seen beautiful screenshots like these:

[http://www.lynucs.org/index.php?screen_type=1&screen_id=1286531384713214c78eb4&m=screen](http://www.lynucs.org/index.php?screen_type=1&screen_id=1286531384713214c78eb4&m=screen)

[http://www.lynucs.org/index.php?screen_type=1&screen_id=79522129549669be51e2e0&m=screen](http://www.lynucs.org/index.php?screen_type=1&screen_id=79522129549669be51e2e0&m=screen)

But I need some help setting up some of these things.

1. how do I get that little panel/bar on the bottom of the screen in the middle?

2. how do I change themes?

3. how do I get the uptime, cpu and memory usage, etc. in the top bar?

any help is greatly appreciated. thank you in advance :)

---

### Post by Dawei87 on 2009-04-19
1: To make the bottom panel in the middle just right click it and go to shelf Settings>Advanced and under layout make sure it is set to middle, and under size make sure it is set to shrink to content size. 

2: To change themes just click on the desktop and go to Settings>Theme and select. If you want to download you can go to either exchange.enlightenment.org or e17-stuff.org. After you download its easy, from theme select screen just cleck import and navigate to the download. 

3: To add gadgets to the shelves you must first make sure the module is loaded. Click on the desktop and go to Settings>Modules and under the shelf section load whatever you need. then once you have done that you can right click your shelf and go to Shelf Settings>Configure Contents... and add what you want to the shelf. To move a gadget on the shelf right-click the gadget you want to move and click Begin move/resize this gadget, then click and drag where you want. When finished right click and select Stop move/resize this gadget.

Edit: Oh. I just noticed you said you were using e16. Not sure if it works the same as e17, that's what I'm using and I have not tried e16.

---

### Post by Tux Aubrey on 2009-04-20
Yeah, I'm pretty sure those screenies are of e17 - and a fairly recent build too.

---

### Post by mtgmutton on 2009-04-20
thanks for the replies!

These being e17 would explain my confusion :)

how would I go about installing e17?

---

### Post by Tux Aubrey on 2009-04-21
Right now, without switching distros to OpenGeu, the "best" way to get e17 is to compile it from source.  

That's not as scary as it sounds!

There's a script that does all the legwork for you - see [THIS POST]("http://ubuntuforums.org/showthread.php?t=916690").

A variation on that How-To that adds a few more tools and some extra desktop options is the basis for OzOS. You can cut and paste all the commands from [HERE]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os").

The e17 source code should be fine right now - it is having a freeze this week in preparation for a snapshot that will eventually make its way into various repositories - including Debian experimental, but probably _not_ Ubuntu (the previous snapshots have not been packaged officially for Ubuntu - hence OpenGeu and OzOS).  You _could _wait a few weeks for the .deb to appear somewhere if you don't like the idea of a source code install.

I think a lot of people will be surprised at how far e17 has come since currently available packages came out.  While still not a "fully featured" DE like Gnome and KDE, it is very usable and beautiful.  It does take a bit of getting used to as it is VERY configurable.

If you have any problems or questions post in that first thread or on the cafelinux forums (link in my sig).

---

### Post by mtgmutton on 2009-04-21
thank you very much!

minor problem...

```
sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: librsvg2-dev but it is not going to be installed
E: Broken packages
```

what should i do?

---

### Post by Tux Aubrey on 2009-04-21
> **mtgmutton said:**
> thank you very much!

minor problem...

```
sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: librsvg2-dev but it is not going to be installed
E: Broken packages
```

what should i do?

That's strange.  librsvg2-dev is a standard library in the Ubuntu main repository.  What version of Ubuntu are you using?

---

### Post by mtgmutton on 2009-04-21
I'm using Linux Mint.

---

### Post by Tux Aubrey on 2009-04-21
> **mtgmutton said:**
> I'm using Linux Mint.

I'm not sure about the implications of enabling the Ubuntu repos in Mint.  You might check out the Mint Forums.  I do remember that someone reported successfully using e17_svn on Mint but I'm not sure how they got all the dependencies met.

---

### Post by mtgmutton on 2009-05-01
thank you very much for your help :)

---

