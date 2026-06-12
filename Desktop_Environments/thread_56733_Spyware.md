---
title: "Spyware"
date: 2005-08-13
forum: Desktop Environments
---

### Post by dbeckham32 on 2005-08-13
I've recently switched from Windows to Ubuntu -- and am quite happy so far, save for the fact I can't view QuickTime movies in a web browser or see Shockwave annimations.

But my question remains this: Does the spyware problem exist for Linux machines? I know viruses on Linux are all but a non issue, but I've not heard if that's also the case for spyware.

Ciao for now.

---

### Post by autocrosser on 2005-08-13
I'm sure that there will be a problem in the future--those types write garbage as soon as there is enough reason for it--but, Linux is much easier to detect & destroy non-authorized programs that Windows just lets in--remember, with Windows there is always a "breeze" coming thru---

Unix based software allows you the choice to see what is "really" going on in your system & if you are on top of it--not much will ever get thru---Make a habit to look at your System monitor every so often--In "All processes" is the "real" world....

And remember---A BAD day in Linux is better than the Best day with Mr Gates looking over your shoulder!!!!!

---

### Post by obx-jdt on 2005-08-13
[QUOTE=autocrosser]I'm sure that there will be a problem in the future--those types write garbage as soon as there is enough reason for it--but, Linux is much easier to detect & destroy non-authorized programs that Windows just lets in--remember, with Windows there is always a "breeze" coming thru---

Unix based software allows you the choice to see what is "really" going on in your system & if you are on top of it--not much will ever get thru---Make a habit to look at your System monitor every so often--In "All processes" is the "real" world....

And remember---A BAD day in Linux is better than the Best day with Mr Gates looking over your shoulder!!!!![/QUOTE]
Hummm, I just did a forum search about spyware for the same reason. It's my undestanding that spyware is installed by viewing web sites, based on your security settings. Works on the same principal as cookies. If you block all cookies, you'll be blocking 50% of the internet. I block 3rd party cookies, and block popups (not so effectively now-a-days). 
It would be nice to find a program for Linux like "[Ad-Aware](http://www.lavasoftusa.com/software/adaware/)" . Just for peice of mind.

---

### Post by wmcbrine on 2005-08-14
In a word, no.

There would be nothing for a Linux version of AdAware to detect, unless perhaps it also scanned your Windows partition.

Spyware comes in via Internet Explorer, on Windows, running in an Administrator account. You can eliminate two out of three of these weak points even on Windows. (Me, I've never had a spyware infestation in Windows; and there's no reason you should, either.)

In Ubuntu:

1. You're running Firefox, or maybe some other non-IE browser if you're weird. :) I'm not certain, but I don't think there's ever been a spyware infestation delivered via Firefox, even on Windows. When you try to install software from within Firefox, it prompts you several times before it allows it -- there's no automatic installation. And that's for extensions or plugins; it won't install anything else at all.

2. Ubuntu doesn't even create a root account, much less make it the default. Unless you've intentionally changed this (bad idea), you're running in an account that doesn't even have privileges to install software without a password.

3. You're running Linux, not Windows. No extant spyware is written for Linux. And Windows spyware won't run, unless you go out of your way to start it in WINE.

None of these are insurmountable barriers to spyware, in principle. But in practice, they are. Some people (mainly Windows apologists) like to say "If Linux (or Mac OS X) were as popular as Windows, it would have just as much spyware." These people are wrong. Linux is inherently more secure than Windows. The biggest advantages are simple: non-superuser accounts are standard, and there's nothing like ActiveX (nor the mentality responsible for it).

Which brings me to the biggest reason Windows users get infected: Their own ignorance and carelessness. Despite everything I just said, a lot of spyware doesn't come in via ActiveX or IE exploits at all; it comes in when users voluntarily install stupid crap on their systems. But this, too, is something you can easily avoid. First of all, that kind of software has essentially no entree into Linux; there are always decent open-source solutions for anything you want to do. More importantly, by choosing Linux -- or by making *any* OS choice, other than "what came with the computer" -- you've already proven you have some savvy. That's another factor that discourages would-be spyware writers. (Admittedly, this is one point where the effect could be diluted by wider adoption of Linux.)

Rest easy. But remain vigilant. ;)

P.S. To block the resurgent pop-ups, use the Adblock and Flashblock extensions, along with a suitable filterset for Adblock. There's also an about:config setting to add, and then set "false"... something like "privacy.popups.allow_from_plugins", but don't quote me on that. And I'd suggest disabling Java (note: not Javascript) until you need it.

Quicktime movies, at least some of them, should be playable in the browser via mplayerplugin.

---

