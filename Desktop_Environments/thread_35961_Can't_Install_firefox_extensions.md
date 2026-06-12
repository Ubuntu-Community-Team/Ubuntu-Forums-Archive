---
title: "Can't Install firefox extensions"
date: 2005-05-21
forum: Desktop Environments
---

### Post by sparky100 on 2005-05-21
my current version of firefox is 

Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.7.8) Gecko/20050513 Firefox/1.0.4 (Ubuntu package 1.0.4~5.04ubp1+1.0.2)

I can access the Mozilla extension page ... however whenever I try an install I get no response? This works fine under windows?

Any suggestions

Simon

---

### Post by f.prisson on 2005-05-21
What extensions do you want to install? I never do it this way, have a look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) there are good descriptions for installing every plugin.

---

### Post by derrick1985 on 2005-05-21
You HAVE to have v1.0.4 of firefox to get entensions anymore, and even then, if you get the ubuntu version from backports, you have to change a certain line. Check out [www.ubuntuguide.org](www.ubuntuguide.org) for adding backports and get the latest firefox from there, then read on below:

Regretably, when the Ubuntu Firefox was built, they forgot to put in the proper version number, which the extensions page looks for.

type about:config

Scroll down until you find genera.venderagent.vendersub

double click and change it from 1.0 to 1.0.4

Enjoy

---

### Post by sparky100 on 2005-05-21
i have already set 

general.useragent.vendorSub to 1.0.4

I can access the extensions page they just don't seem to want to install ??

Simon

---

### Post by sparky100 on 2005-05-21
[QUOTE=f.prisson]What extensions do you want to install? I never do it this way, have a look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) there are good descriptions for installing every plugin.[/QUOTE]

it's a problem with any of the extensions on 

[https://addons.mozilla.org/extensions/moreinfo.php?id=220&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=220&application=firefox)

cheers

simon

---

### Post by wjfcraig on 2005-05-21
You may want to look at:
Edit
Preferences
Web Features

and make sure 'Allow Web Sites to Install Software' is checked.

Bill

---

### Post by sparky100 on 2005-05-21
Thanks for the suggestion... however

 'Allow Web Sites to Install Software' is checked. and

web site is set up to allow installation?


Arrrgh...


Simon

---

### Post by tlepes on 2005-05-23
I am having problems with my extensions too since upgrading to 1.0.4 (hoary)

#1 )  I had to edit that vendorsub string in about:config but it is not persistent for me.  When I close and re-open ffox it is reset!!!!

#2 )  Many of my extensions got disabled, and I can't install most any of them either!

I remember before that when ffox version number changes, all the extensions have to do an update for the installers to work.  There is a way to edit the installer files manually or maybe to "repackage" them, but I can't find the howto out there.  Anyone know?

Man, there has got to be a better system for Firefox to deal with compatibility on extensions.  Isn't it possible to have extensions track a major version number for compatibility and ignore the minor version numbers?  It would really help if there was some separation or security updates are going to be the bane of extension authors!!!

Peace,
Tim

---

