---
title: "ctrl-alt-backspace"
date: 2009-05-01
forum: General Help
---

### Post by twiz86 on 2009-05-01
I know they turned this off for 9.04. How can I turn this back on?

Thank you

---

### Post by mb_webguy on 2009-05-01
Put the following in your /etc/X11/xorg.conf file:```
Section "ServerFlags"
   Option "DontZap" "false"
EndSection
```

OR, you can enter the following command in the terminal:```
sudo apt-get install dontzap && sudo dontzap --disable
```

---

### Post by webkris on 2009-05-01
mb_webguy:
In editing the xorg.confg -

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

When I ran the command - it removed the edit you suggested.

What are the consequences of editing this and not having the xorg.conf update itself any more?

Thanks!
- Kris

---

### Post by mb_webguy on 2009-05-01
To which command are you referring?  The one that installs and runs dontzap, or "sudo dpkg-reconfigure -phigh xserver-xorg".  If it's the latter, that creates the xorg.conf file according to settings based on your detected hardware, and wipes any custom settings you've added.  The xorg.conf file isn't like the GRUB menu.list where you change options then run a command.

---

### Post by webkris on 2009-05-01
Okay -
The first suggestion was to edit the xorg.conf and add lines -

Section "ServerFlags"
   Option "DontZap" "false"
EndSection

INSIDE the xorg.conf it basically says:
If you change this file, it will no longer automatically update with xserver-xorg package upgrades.

To which my question is:
**What are the consequences of editing this and not having the xorg.conf update itself any more?**

I guess since the package just adds those lines anyway, it's not a big issue, but the fix was to edit a file that said "once you edit this, it will no longer update" and thus made me ask the somewhat obvious question.

That's all. Thanks!
- Kris

---

### Post by mb_webguy on 2009-05-02
The message at the beginning of the xorg.conf file isn't a warning not to edit it as much as it is a confirmation that any changes you make to it won't be overwritten by an update, and if you make any changes, you can manually update it by running that command.  It's not to warn you off, but to reassure you.

---

### Post by asbesto on 2009-05-02
> **twiz86 said:**
> I know they turned this off for 9.04. How can I turn this back on?

Thank you

And now my question is: 

                       **WHY ?!?!?!?!?!**

With so much problems to solve, WHY change things that people use from YEARS without any kind of problem? 

I really can't understand this way of doing stuff :confused:

---

### Post by Seventh Reign on 2009-05-02
> **asbesto said:**
> And now my question is: 

                       **WHY ?!?!?!?!?!**

With so much problems to solve, WHY change things that people use from YEARS without any kind of problem? 

I really can't understand this way of doing stuff :confused:

Because its sooooooooo easy to 'accidentally' press 3 keys, 1 of which is all the way at the other end of the KB, at the same time.  lol

---

### Post by webkris on 2009-05-02
I have stumbled across many threads that suggest that as an emergency help command. A place to start. With easy troubleshooting - you have to start somewhere and trying to get a brand new user to get comfortable with the magic sysreq keys could be too much...

Since I have started using Ubuntu (5 months now) it has saved my *** 3 or 4 times.
*Webcam crashed in skype.
*Lost desktop and gnome with desktop switcher.
*Pulled up a folder with a gajillion files and timed out Nautilus and then froze the machine.

I think it's the stigma of a reset command - more then a "you could accidentally hit this" that may be the issue. 
For example - old macs had problems with P-RAM. So there was this crazy key-stroke to clear it - next thing you know, every mac user was jamming that command in when EVER anything went wrong...

I strongly feel that we need it - I'll take up the cause.
- Kris

---

### Post by hardskinone on 2009-08-05
I know this is an old bloated topic but I would like to know serious reason why this combo has been disabled by default.

Does Ubuntu director board really think average user pass its time to beat hands over keyboard?

No, the "edit-that-frucking-xorg.conf" argumentation it is not a serious workaround. What about all machine where people does not have root privileges?

I really would like to know the name of who decided this crap.

---

### Post by webkris on 2009-08-05
hardskinone is absolutely correct.
Time for a constructive rant.:popcorn:

**This right here** - the CTRL-ALT-Backspace issue is one of the reasons Ubuntu will never gain as much ground as a commercial OS. EVERY time a release comes out - Someone HAS to tweak the crap out of it. CTRL-ALT-Backspace WASN'T BROKEN. There was no bug report that said that it wasn't a viable option for getting control back. Seriously - A user could accidentally hit it? With this logic - a user could accidentally open a terminal and type del *.* - Will those functions be taken away?? 

I'm sorry, but this decide by everyone, listen to no-one, nothing is sacred, style of OS updates is useless. Bring back CTRL-ALT-BACKSPACE!!!

Core functions - off the top of my head that should NEVER* be touched. *only last resort - if the change is 90% called for.
* The Application, System, and Prefs menu.
* Sys-Request or OS Function Keys
* Default Icons and major scheme layout
* File, Edit, View
* Copy, Paste, Cut
* I know you can think of others.

Last week I was fooling with Compiz - and AGAIN the key stoke would have saved me from hard rebooting about 4 times!
- Kris

---

### Post by hardskinone on 2009-08-12
The person(s) who decided this crap does really now how many time in a week an IT assistent would *really* need of CTRL+ALT+BACKSPACE in a mid size (>15 workstation) office?

Again, does this person knows how is really helpful for poor IT assistant to teach the user that if something get wrong could always used CTRL+ALT+BACKSPACE to "soft" reset machine *without* stress the IT assistant above with useless calls?

---

### Post by clubsoda on 2009-08-13
> **webkris said:**
>  ...the CTRL-ALT-Backspace issue is one of the reasons Ubuntu will never gain as much ground as a commercial OS. I think this issue will affect all of the distros which include Xorg, not just Ubuntu.

And it gets worse... In Karmic, xorg.conf has been removed completely and **dontzap** has been omitted from the package repository.  You can drop to a recovery console and "Xorg -configure" to generate a new xorg.conf, copy that to /etc/X11 and add in the dontzap lines manually but do you think that makes a difference?  Xorg.0.log includes a line about DontZap but ctrl-alt-backspace still doesn't work!!

[quote=hardskinone]I really would like to know the name of who decided this crap.[/quote]A couple of people bombarded the developers' mailing list with complaints about how they were fumble-fingered and kept losing their work by "accidentally" logging out.  Repeatedly.  And about how it hurt to have so many staples through their fingers because they handn't learned not to do that yet either. :)  Or something.

We should post a feature request in the appropriate place, for amusement if nothing else.

---

### Post by User_Name_Taken on 2009-08-14
> **mb_webguy said:**
> Put the following in your /etc/X11/xorg.conf file:```
Section "ServerFlags"
   Option "DontZap" "false"
EndSection
```

OR, you can enter the following command in the terminal:```
sudo apt-get install dontzap && sudo dontzap --disable
```


So I tried this and I still get nothing.  I would really like this feature to work again.  Any ideas?

I know I only have one bean, and that's because I can usually find the answer in the forums so I don't really ever need to post anything.  But I assure you I'm not a noob...


EDIT:  Nevermind.  I got it to work but if I'm using emerald, it stops working...

---

### Post by stinkeye on 2009-08-14
Can't you do the same thing with ctrl-alt-SysRq-k

---

### Post by User_Name_Taken on 2009-08-14
No.  None of those nifty keyboard shortcuts work anymore.  And I really wouldn't be able to tell you why either...

I have a feeling it has something to do with one of the decorators though.  Like emerald or compiz.  Can't guarantee it though...

---

