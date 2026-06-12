---
title: "Debian 3.0 Release"
date: 2005-06-08
forum: Debian
---

### Post by s0c0 on 2005-06-08
Has anyone tried the new Debian?  I'd like to hear some reviews on it.  I can't wait to try it out this weekend  \\:D/

---

### Post by maspro on 2005-06-08
I think you mean Debian 3.1 instead of 3.0. 

Besides bleeding edge software and stability differences, what is the difference between Ubuntu and Debian?

Is Debian also a distro that "just works", like Ubuntu? Or do I have to manage my way through all kinds of config files to get things working?

---

### Post by s0c0 on 2005-06-08
Meh 3.0 and 3.1, who cares.  I'm talking about the new Debian release.  There really isn't much dfference between he two.  The most glaring differences (aside from their history and things like that) I can think of is in the installer.  In Ubuntu you can take the default or do a "server" install.  In Debian, the default install is Ubuntu's "server" install.  Debian also provides other advanced installation types like expert26.  I'm not sure if Ubuntu has these options, not that I ever use them.
Debian works, but you have to manage your way through some config files to ge there.  Come on though, apt makes things easy.  Half the fun of some operating systems is having to configure them.  Take a look at FreeBSD sometime!

Anyways I am just wondering if anyone has tried the new Debian and what they think.

---

### Post by jdong on 2005-06-08
[QUOTE=s0c0]Meh 3.0 and 3.1, who cares.  I'm talking about the new Debian release.  There really isn't much dfference between he two. [/quote]
KDE 2.x.x vs KDE 3.4.x? The up-to-dateness is a big difference!

> 
 The most glaring differences (aside from their history and things like that) I can think of is in the installer.

Right. Debian really revamped their installer. BTW, this is the same installer that Ubuntu uses.
>   In Ubuntu you can take the default or do a "server" install.  In Debian, the default install is Ubuntu's "server" install.  Debian also provides other advanced installation types like expert26.  I'm not sure if Ubuntu has these options, not that I ever use them.

Ubuntu does provide "expert" options, that nag you every step of the way. Ubuntu uses the 2.6 kernel by default, while Sarge uses 2.4 (compatibility with other archs) while offering 2.6.
> 
Debian works, but you have to manage your way through some config files to ge there.  Come on though, apt makes things easy.  Half the fun of some operating systems is having to configure them.  Take a look at FreeBSD sometime!

Well, Ubuntu is a preconfigured Debian plus newer/different packages and faster release cycles. FreeBSD/Gentoo are a different variety.
> 
Anyways I am just wondering if anyone has tried the new Debian and what they think.
Not yet, but I do plan on building an embedded router sometime soon, and Debian Sarge will probably be the choice OS.

---

### Post by az on 2005-06-08
[QUOTE=s0c0]Has anyone tried the new Debian?  I'd like to hear some reviews on it.  I can't wait to try it out this weekend  \\:D/[/QUOTE]

Debian is a general-purpose distribution.  Chances are, if you are an Ubuntu fan and have just heard about debian, nothing there will interest you.

Since Ubuntu uses cutting-edge software and makes life easy for desktop users, Debian will probably dissapoint the average Ubuntu user.  They may find it bland.

It is sort of like eating a really sweet apple after having downed a chocolate milkshake.  Your tase buds are nummed and the experience is not what you would expect.

---

### Post by jerome bettis on 2005-06-08
[QUOTE=azz]Debian is a general-purpose distribution.  Chances are, if you are an Ubuntu fan and have just heard about debian, nothing there will interest you.

Since Ubuntu uses cutting-edge software and makes life easy for desktop users, Debian will probably dissapoint the average Ubuntu user.  They may find it bland.

It is sort of like eating a really sweet apple after having downed a chocolate milkshake.  Your tase buds are nummed and the experience is not what you would expect.[/QUOTE]

that's a good way of putting it.  if you're looking for a distro where you can put the cd in and expect everything to work automatically 20 minutes later, debian is not what you want.  i tried installing it a couple days ago and it was a big mess.

but i've waited so long to see this i can't let it beat me.  i'm going to try it again when i have more patience and am better prepared.  actually i think i'm going to install woody again since i've successfully done that before (still have the config files :grin: ) and then i'll dist-upgrade to sarge.

---

### Post by defkewl on 2005-06-09
I wouldn't recommend Debian for an end user. Debian is not like Ubuntu. And yes there are big difference between Debian 3.0 and 3.1

---

### Post by mtron on 2005-06-09
woody was a very good release. we had it on our office server since it was released without one problem running, and running and running. 

Now it's time to make the sarge update, btw. debian ships & maintains apache (1.3.33-6), ubuntu is still on 1.3.33-4. is apache 1.3 not supported any more by ubuntu?

---

### Post by s0c0 on 2005-06-09
I started with Debian, sheesh guys.  If it wasn't for Debian then Ubuntu would be based off some crap distro like Fedora.   The Debian install isn't a mess either it just requires a bit more effort.  Sure there isn't a default gui, instead you need to do apt-get install x-window-system-core and then actually learn how to configure your xorg or free86.   ](*,)   Yeah, I guess Debian isn't a hold your hand distribution like Ubuntu.  :-# 

Anyways did Debian every upgrade to xorg over xfree86?

---

### Post by poofyhairguy on 2005-06-09
[QUOTE=s0c0]

Anyways did Debian every upgrade to xorg over xfree86?[/QUOTE]

No. And from what I've heard, they aren't going to do it Ubuntu's way. The differences begin...

---

### Post by az on 2005-06-09
[QUOTE=mtron]woody was a very good release. we had it on our office server since it was released without one problem running, and running and running. 

Now it's time to make the sarge update, btw. debian ships & maintains apache (1.3.33-6), ubuntu is still on 1.3.33-4. is apache 1.3 not supported any more by ubuntu?[/QUOTE]

Debian ships with apache 1.3 and apache2.  Ubuntu just ships with apache2.


The thing that just occurred to me is that people do not realise that in debian, EVERYTHING in universe is now stable.

That means that all packages are stable and maintained.  Ubuntu has a handful of people looking after all the packages in Universe.  Debian supports every single one of them.  Debian has thousands of Developers, where Ubuntu has dozens.

It is not possible to coordinate so many people to release and keep the packages as current as the small subset of packages in Ubuntu.


S0c0:  About your Fedora comments, please do not bash any distro here.  We do not tolerate it...

---

