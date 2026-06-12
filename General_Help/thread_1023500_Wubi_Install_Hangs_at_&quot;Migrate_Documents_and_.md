---
title: "Wubi Install Hangs at &quot;Migrate Documents and Settings&quot;"
date: 2008-12-28
forum: General Help
---

### Post by buckscaper on 2008-12-28
Hi, 
Totally clueless, Ubuntu/Linux newbie here.

Ran Wubi on a Dell Inspiron with WinXP to "hopefully" set up a dual boot without doing any partitioning, etc. 

Wubi ran, the machine rebooted, dual boot options appeared on screen, and after booting into Ubuntu, and the system running a while, a dialog box appeared to "Migrate Documents and Settings". It showed only 1 of the 4 Windows user accounts that are on the machine. That's no big deal as I wasn't sure I was going to migrate anything anyway.

However, whether I clicked the box next to the user account or did not, the only button that was not grayed out at the bottom of the dialog box was the QUIT button. 

The NEXT (continue) button and the BACK button would not become active no matter what I did. 

The only way out of the dialog was to click the QUIT button which then asked if I wanted to cancel the installation (which I didn't realize was still not complete). I clicked YES and it proceeded to open a Ubuntu desktop.

In the upper right corner of the screen it says "Live Session User". Something's not right but I'm not sure what and I know I wasn't supposed to "QUIT" the installation.

Can someone please help me get past the Migrate screen?

Oh, and please, I've read other posts and help FAQs and I have no idea what the heck is going on with all the answers like "just type -x a--b...."   I do not know Linux or Unix or anything like that - I don't even know where one is supposed to do all that typing.

While I'm a reasonably knowledgeable computer user (windows), I really need any answer in this case to be dumbed down to the most basic basic beginner level.

Thanks very much,
Buck
<UPDATE>
Machine just restarted and evidently the last install really did fail completely. The dual boot options appeared on restart, I chose Ubuntu, and the thing just cranked and cranked and when it was done, the MIGRATE SETTINGS dialog appeared again, still broken (no way to click any button other than QUIT).

I clicked QUIT, confirmed it, and it opened a new Ubuntu desktop (Live Session User) again. None of the settings I'd changed during the prior session were saved. 

So the install is definitely failing.

Help?
Thanks

---

### Post by Jammanuser on 2008-12-30
> **buckscaper said:**
> 
In the upper right corner of the screen it says [COLOR="Red"]"Live Session User[/COLOR]". Something's not right but I'm not sure what and I know I wasn't supposed to "QUIT" the installation.


Huh...sounds like a weird problem! :D It sounds like Wubi is mistaking itself for a Live Session (boot from a LiveCD)! :P 

Sorry I can't be of any further help. I've never had a problem like that before...and this is the first time I've heard of one like that! :D

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by brainstuff on 2009-01-06
Hey, quick note to say hello, I'm having the same issue on a thinkpad T21 that I've had previous Ubuntus (6 and 7 natively installed not through Wubi) running on before with some tweaking of the graphics settings (xorg). I gotta say the machine is a bit flakey as it's not done too well with Fedora 10 or Linux Mint 6 either this time round. I'll let you know if I work out a workaround.

BTW Wubi on 8.04 quits out during the Windows install with the least helpful error I've ever seen "Error: could not continue" or some similar b*ll*cks :)

Cheers
Tom

---

### Post by rben13 on 2009-01-09
Is it at all possible that you have a Live CD in the CDROM drive when this happens? I know that's probably not it, I'm just trying to make sure it's not something that was just overlooked. Please don't take offense.

---

