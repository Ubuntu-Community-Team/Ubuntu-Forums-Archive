---
title: "No fonts in firefox"
date: 2006-05-14
forum: Desktop Environments
---

### Post by cromestant on 2006-05-14
Just noticed this, I have no fonts in firefox...

I 'm doing a small project for my university, and just realized that firefox only displays it's default fonts... even if I change the css ( and check it with the css plugin for firefox), the font-family property of the element changes, but not the displaying of it....

How can I resolve this, I need to have all fonts available on firefox

Thank you
Charles

You can see what I mean here
[http://charz.homelinux.org/~charz/labati/](http://charz.homelinux.org/~charz/labati/)
the menu on the left, should be in comic sand ms, I get no such thing... nothing ever changes, even if I change the property... tried verdana, arial, courier.. nothing changes..
thanks

---

### Post by deanjm1963 on 2006-05-14
i found it to work here, I could see Comic Sans in the left hand menu box... do you have the fonts installed?

---

### Post by cromestant on 2006-05-14
That's just it, it displays it for others, and not for me... I don't know if the fonts are installed, how do I check this?
they work in open office..
Thank you for your reply.

this is what I see :

---

### Post by deanjm1963 on 2006-05-15
It could be your firefox settings, I think there's a setting to allow firefox to use "other fonts", so check to make sure that's enabled.

---

### Post by cromestant on 2006-05-15
The setting is enabled....
I appreciate the help by the way, I need to have this working properly, since I hate php, mysql, and apache under windows, but if I don't have a choice, I might have to revert back to it.. This is strange, I don;t know if it's a dapper bug, but it's really anoying not to be able to see diferent fonts on firefox.
i searched the forums for this problem, and all I found were references to : BIG fonts, small fonts, and sucky fonts...

My problem is that I have only one type of font , and it's serif counterpart..

Thanks again, hope we can find a fix to this.

---

### Post by cromestant on 2006-05-16
Ok, fixed it, finally...
So the problem is that ubuntu does not install all fonts... even if oo does install a lot of them... so Now i'm thinking that maybe OO does not use the system fonts... if any of you out there know this to be true, please tell me, either on the forum or PM.

Now, I just installed the core fonts package through synaptics, and restarted gdm ( ctrl +alt+f1, login as user or root, then sudo /etc/init.d/gdm restart ... don't do sudo if you are root..)

this is the link where i found the info:

[https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

thanks again for the help...

charles

---

