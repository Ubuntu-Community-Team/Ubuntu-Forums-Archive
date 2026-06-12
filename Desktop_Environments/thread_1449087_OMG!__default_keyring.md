---
title: "OMG!  default keyring"
date: 2010-04-07
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-04-07
This is the single biggest issue I have had with gnome and ubuntu in recent times.
The default keyring prompt every login.

I have been using Linux Mint for some time and I finally made the problem go away by refusing to use any app that brings up the prompt.  I even stopped using wireless and went back to ethernet because of it.

So I have decided to try ubuntu to see how things have changed since last time I used it and this thing is still here.

I have also been trying the lucid beta and I really liked the whole  "social networking" menu thing but again I was blighted by this stupid  keyring.

I have done a search and found literally hundreds of articles and forum threads on the subject and have tried various workarounds but so far nothing is working on this install.

So what is the recommended way of dealing with this problem these days?

I don't want to be asked for a password at login and I don't want to be asked for a password every time I launch an app.
I want to turn on my comp, go make a cuppa and come back to a fully loaded desktop and launch apps without hassle but I also don't want to have to go installing alternate apps every time I install an OS either.

Back in the day, linux was all about the OS working how you wanted it to work but it seems every new install I do I have to jump through more hoops to make it work how I want.

As it is I am about to switch over to KDE on Linux Mint, the keyring thing being a major factor in that decision but I do really prefer Gnome.

---

### Post by mcduck on 2010-04-07
It's really simple. Just remove the keyring password. Of course that means that all your keys will be stored unencrypted, but since you are already using automatic login that doesn't really make much of a difference and you probably aren't concerned about such security features  anyway.

Go to *Applications/Accessories/Passwords and Encryption Keys*, right-click the "*Passwords:login*"-keyring and select "*Change Password*". Type your current password but leave the fields for new password empty.

Linux is still, just like back in the old days, about OS working the way you want it to. And just like in the old days, you have to do some work to configure it like you want to, and perhaps sometimes do a quick Google search to find out how to do that. I mean, really, "a quick search for remove keyring password" would have solved your problem immediately so I have no idea what the hundreds of articles and forum threads you've been reading might have been about.. ;)

---

### Post by doas777 on 2010-04-07
> **x-shaney-x said:**
> 

Back in the day, linux was all about the OS working how you wanted it to work but it seems every new install I do I have to jump through more hoops to make it work how I want.

sounds like you pine for the days when desktop linux was a really simple system that didn't do a lot. thats fine, I have minimalist inclinations sometimes myself. ubuntu however is not a distro for minimalists (nor is it for people that don't care about minimal security procedures). you might be happier using an more minimalist/build-up distro like arch, debian, slack,  or whatever. 

you can also tell the keyring not to automatically unlock at login, but if you mount samba shares or whatever, you will have to either enter your username/password to connect, or forgo authentication on the samba side. personally i just put in my password. only takes a second.

---

### Post by x-shaney-x on 2010-04-07
Probably didn't word things very well (I was ranting after all).
It's not so much I don't appreciate what linux does for me these days it just seemed much simpler to MAKE it do what I want but I guess that is the price of having a less fiddly and more reliable OS.

It's more frustration that I face this same issue every time I install ubuntu or Mint.
Just not really sure how to get my point across.

@ mcduck
I don't see a blank password is really a solution.

The fact is, it IS possible to keep the password without having to get rid of it altogether or enter it every time it just seems there is no solution that works everywhere for everyone.
I have seen many suggested solutions, from editing pam files to removing files in the home directory and recreating them and many others.

This is a typical example of one of the threads I was talking about: [http://forums.linuxmint.com/viewtopic.php?f=90&t=21071](http://forums.linuxmint.com/viewtopic.php?f=90&t=21071)

I have tried a suggested solution I found on my Mint install since my first post:
Going to passwords & encryption keys and changing login and default passwords so they are the same.
I did this (the passwords were the same anyway, I just used the same ones when re-entering).
Now I still have passwords but it does not ask me anymore when I launch empathy/evolution etc.

Tried exactly the same on my new ubuntu AND lucid testing installs and it didn't work on either.

---

### Post by mcduck on 2010-04-07
> **x-shaney-x said:**
> 
@ mcduck
I don't see a blank password is really a solution.


It's the exact solution you were asking for.

If you set the password blank then the keys will be stored unencrypted and the keyring manager will never ask you for a password.

Setting login & keyring passwords to same is just the default setup, that's what you get right out-of-the-box, and that only unlocks the keyring automatically if you actually *use* the login password. If you don't use login password then the keyring can't be unlocked automatically for you and you end with the keyring manager asking for keyring password as soon as any program tries to access the keyring.

---

### Post by x-shaney-x on 2010-04-07
I get what your are saying but I don't understand why I am able to (now) have encrypted passwords in Mint, without having to enter passwords on login or when I launch apps.

So looking at things a different way, if I go for a blank password so I can do away with the keyring prompts, is this any different to using say, Thunderbird rather than Evolution or Pidgin rather than Empathy?

Thunderbird and Pidgin both save my passwords without the need for the keyring manager so would using a blank keyring password make Evolution or Empathy less secure than Thunderbird or Pidgin?

---

### Post by mcduck on 2010-04-07
> **x-shaney-x said:**
> I get what your are saying but I don't understand why I am able to (now) have encrypted passwords in Mint, without having to enter passwords on login or when I launch apps.

So looking at things a different way, if I go for a blank password so I can do away with the keyring prompts, is this any different to using say, Thunderbird rather than Evolution or Pidgin rather than Empathy?

Thunderbird and Pidgin both save my passwords without the need for the keyring manager so would using a blank keyring password make Evolution or Empathy less secure than Thunderbird or Pidgin?

If the apps don't use Gnome's keyring to store their passwords, but instead do it on their own, then of course keyring manager has nothing to do with their passwords. :D

If you go for a blank keyring password, the passwords stored in that keyring will not be any more vulnerable than any other file stored in your home directory, including those passwords stored by Pidgin and Thunderbird. Of course they *will* be more vulnerable than if they were stored in encrypted format and protected by the keyring manager.

In other words, setting a blank keyring password wouldn't make the programs that use keyring any *less* secure than all the apps that don't use the keyring. it would just make them *exactly as insecure* as apps like Pidgin are.

edit: I think I should add that all this security talk is of course about *local security*, so not using a login password makes it all pretty much irrelevant anyway.

---

### Post by x-shaney-x on 2010-04-07
> **mcduck said:**
> it would just make them *exactly as insecure* as apps like Pidgin are.

Perfect!  :)

Ok so this "problem" really comes down to laziness vs security.
I must admit I am now veering towards the blank password idea since I'm not THAT security conscious and I don't exactly have the secrets of the universe on my comp.

I am curious to know though, do the majority of users really enter that keyring pass every time they boot up and use Evo or something?

---

### Post by mcduck on 2010-04-07
> **x-shaney-x said:**
> Perfect!  :)

Ok so this "problem" really comes down to laziness vs security.
I must admit I am now veering towards the blank password idea since I'm not THAT security conscious and I don't exactly have the secrets of the universe on my comp.

I am curious to know though, do the majority of users really enter that keyring pass every time they boot up and use Evo or something?

No, everybody either uses the login password (which unlocks the keyring automatically for you) or sets an empty keyring password.

Actually using an automatic login *with* a keyring password wouldn't make much sense in any situation I can think of right now. Same work as using the login password, but would only protect the keyring instead of protecting your whole home directory and user account like the login password does.

---

### Post by x-shaney-x on 2010-04-07
You make a lot of sense.

I have seen the gnome keyring thing as a hassle for so long without actually looking into it.
The main reason I have auto login is so the missus doesn't have to enter the password (and the reason I gave earlier about making a cuppa) and she is the only other person who has physical access to the computer so the blank password option shouldn't be a problem.

---

### Post by doas777 on 2010-04-07
I have a media box in the living room that the kids use, so I set it to autologin, but i don;t give them the passwd. i just set the keyring to a different password (which I shared with them), so they can't sudo, but can get to the fileserver. they unlock it at boot as needed, but it isn;t needed often as the box only seems to get rebooted after kernel upgrades anyway, when I'm there to reinstall the vid card drivers. it works out pretty well.

---

### Post by mcduck on 2010-04-07
> **x-shaney-x said:**
> You make a lot of sense.

I have seen the gnome keyring thing as a hassle for so long without actually looking into it.
The main reason I have auto login is so the missus doesn't have to enter the password (and the reason I gave earlier about making a cuppa) and she is the only other person who has physical access to the computer so the blank password option shouldn't be a problem.

Yeah, if it's a home computer (or a laptop but you don't carry it around) and only people you trust have access to it (and you aren't storing any national secrets or other stuff like that ;)) then using automatic login and unencrypted keyring should be just fine.

---

### Post by mcduck on 2010-04-07
> **doas777 said:**
> I have a media box in the living room that the kids use, so I set it to autologin, but i don;t give them the passwd. i just set the keyring to a different password (which I shared with them), so they can't sudo, but can get to the fileserver. they unlock it at boot as needed, but it isn;t needed often as the box only seems to get rebooted after kernel upgrades anyway, when I'm there to reinstall the vid card drivers. it works out pretty well.

You could save yourself (and the kids) from the trouble of having to type the keyring password simply by creating a normal user account for your kids to use, and setting Ubuntu to log automatically into *that* account, instead of letting them use the admin account.

---

### Post by doas777 on 2010-04-07
> **mcduck said:**
> You could save yourself (and the kids) from the trouble of having to type the keyring password simply by creating a normal user account for your kids to use, and setting Ubuntu to log automatically into *that* account, instead of letting them use the admin account.

it's the account on the file server that i am worried about protecting in that scenario. 
the account is probably a touch over privledged, in certian parts of my network. I need to get arround to studying ACLs. this ugo limitation is becoming a little cumbersome. better get my learning on.

---

### Post by x-shaney-x on 2010-04-11
So I went ahead and used blank passwords for the keyring on all my installations (with the autologin I was using before).
This has been working wonderfully for me until I decided to try Evolution again (switched over to T-bird a while ago because of this keyring issue).
Set an account up and next boot, as soon as I checked for messages it asks for a keyring password saying the LOGIN keyring was not unlocked (rather than the usual default password prompt).

Evolution is the ONLY thing bringing this up, even when I have started other apps that normally use gnome-keyring before launching Evo.

---

### Post by x-shaney-x on 2010-04-16
So an update on this.
As I mentioned before, evolution was STILL asking for the login keyring (not default) every time I launched it so I eventually decided to change the login keyring to a blank password as well as the default one.
This has finally been working well enough but, although I'm not the most security conscious person in the world, this whole idea of blank passwords as a workaround doesn't really sit well with me.

So I have done another install but this time decided to do away with autologin (since that seemed to be the big problem).
So now every time I boot up I login to the desktop which isn't actually much hassle.
The problem is, empathy, evo etc are asking for the default keyring again, even though it is the same as the login one.

AARRGGHH!! I don't mind having to keep on entering a password for root access but having to enter a pass for login then again a few seconds later when I launch something is ridiculous, I may as well do away with storing passwords and just enter them individually per app.

I want security but I also want a fair bit of convenience and it seems these days there is no way to get both :(

---

