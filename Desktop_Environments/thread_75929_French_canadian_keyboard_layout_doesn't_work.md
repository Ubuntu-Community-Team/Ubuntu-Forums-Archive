---
title: "French canadian keyboard layout doesn't work"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ironphil on 2005-10-14
I tried to select it in gnome but it doesn't load and tried to put the keyboard layout in xorg.conf but it  also doesn't load. I'm screwed, without the right keyboard layout, this makes it hard to use.

---

### Post by microo on 2005-10-14
[QUOTE=ironphil]I tried to select it in gnome but it doesn't load and tried to put the keyboard layout in xorg.conf but it  also doesn't load. I'm screwed, without the right keyboard layout, this makes it hard to use.[/QUOTE]


Try this my friend in a terminal type..... sudo gedit /etc/X11/xorg.conf and search for InputDevice and at the line Option  XkbLayout put "ca(fr)" instead of what is written and save your things. Do a reboot and surprise your keyboard will be change.

I got this trick from a genius 

I hope this will help you

---

### Post by ironphil on 2005-10-14
Thanks, that solved it. I use to do the same thing except that I used "ca_enhanced" instead of "ca(fr)". I use to do this for every distro that didn't support the french canadian keyboard (the right one!) out of the box. But this time it didn't work, I don't know what has changed. Thanks again.

---

### Post by neutro on 2005-10-14
The ca_enhanced layout got borked a few days before the final Breezy release. Somehow it got implemented in the ca layout, fr variant sometimes in the last week.  However ca_enhanced is still damaged.

Keyboard layout switcher applet in Gnome still doesn't work for me, though.

---

### Post by toujours on 2005-10-15
w00t !! Thanks for this thread ! I was having grief with my french canadian keyboard and saw this ! :KS :KS :KS :KS :KS 

Merci mille fois !!

---

### Post by Biased turkey on 2005-10-18
Merci a lot for the info guys,
Last weekend the weather was so crappy here in Montreal that it was the perfect conditions for me to get rid of  5.04 and make a complete 5.10 fresh install.
Of course I met the same trouble with my French-Canadian keyboard and using the old ca_enhanced option didn't do the trick.
Just to know, do you have an idea about when will the official fix for that bug be released ?

---

### Post by neutro on 2005-10-18
[QUOTE=Biased turkey]
Just to know, do you have an idea about when will the official fix for that bug be released ?[/QUOTE]

I have no idea. I was accustomed to the very rapid updates of the pre-release era, but they seem to have almost stopped now. Daniel Stone, to whom keyboard bugs seem to be systematicly assigned, asked me for some info recently, but the bug is still in the NEEDINFO phase, and I'm not sure that the problem is isolated to ca_enhanced alone, since there was many thread in these forums about people having problems with their brazilian, polish, italian, etc. keyboard layouts.

---

### Post by Biased turkey on 2005-10-18
[QUOTE=neutro]I have no idea. I was accustomed to the very rapid updates of the pre-release era, but they seem to have almost stopped now. Daniel Stone, to whom keyboard bugs seem to be systematicly assigned, asked me for some info recently, but the bug is still in the NEEDINFO phase, and I'm not sure that the problem is isolated to ca_enhanced alone, since there was many thread in these forums about people having problems with their brazilian, polish, italian, etc. keyboard layouts.[/QUOTE]

About the NEEDINFO phase, I remember when trying to switch keyboard using the GUI there was an error message and the request for sending the listing resulting of a few commands to ( if my memory is correct ) the xorg
I didn't pay any attention to it because I just wanted my system to get installed A.S.A.P. and as I was installing 5.10 on my firewall-router it didn't has the email configured.
I'll retry tonight to see if I can get that error message again and email the results so it'll help the developers.

P.S. Anyone from the St. Laurent area ?

---

### Post by oldforce on 2005-10-18
i can not use speacial trukish characters with loaded turkish keyborad layout..
pls help me and show me a way to correct it

---

### Post by neutro on 2005-10-18
[QUOTE=Biased turkey]About the NEEDINFO phase, I remember when trying to switch keyboard using the GUI there was an error message and the request for sending the listing resulting of a few commands to ( if my memory is correct ) the xorg
I didn't pay any attention to it because I just wanted my system to get installed A.S.A.P. and as I was installing 5.10 on my firewall-router it didn't has the email configured.
I'll retry tonight to see if I can get that error message again and email the results so it'll help the developers.

P.S. Anyone from the St. Laurent area ?[/QUOTE]

Sorry, I'm from Quebec City.

As for the pop-up, if you want it gone, you have to delete the ca_enhanced layout from the layout list. This pop-up appears simply because the setxkbmap command fails with ca_enhanced (try setxkmap -layout ca_enhanced). The information I was asked for was the output of an xkbcomp trial with a specific input. If you're interested in following what's going on with that particular bug (which may in fact be a duplicate of another bug), you can go [there](http://bugzilla.ubuntu.com/show_bug.cgi?id=17246); however I think the developers are now looking up a few things. I'd personnaly wait for  another specific information request, as I think I already spammed this bug enough :P

---

### Post by Biased turkey on 2005-10-18
5 minutes ago I just followed Microo's  "ca(fr)", works nicely. Thanks again.
Now that I have Ubuntu 5.10 working properly with a French-Canadian keyboard, I can  go at my mother's place and replace the Fedora core 3 on her computer with Ubuntu.
Yes, my mom is great, at 81 years old she runs Linux. She never used windows so she never contracted bad habits :)

My next step: install ATI 3D hardware acceleration package ( xorg-driver-fglrx )

---

### Post by ksign on 2008-06-09
hello boys (and grandma too)

I dont know if this will be usefull but I was a bit lost about the french canadian keyboard layout on my brand new eeepc 2g surf and rhaamo on #eeepc-fr on FreeNode told me about this xorg.conf.

I first tried what was written about ca(fr) and ca_enhanced but I still did not get the correct layout.

this my not apply to ubuntu users since I'm on xandros but here is how I finally got what I expected:

[COLOR="Red"]/etc/X11/xorg.conf[/COLOR]

Section "InputDevice"[INDENT]Identifier  "keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbLayout" "ca"
        Option      "XkbVariant" "multi"[/INDENT]EndSection


:guitar:

---

