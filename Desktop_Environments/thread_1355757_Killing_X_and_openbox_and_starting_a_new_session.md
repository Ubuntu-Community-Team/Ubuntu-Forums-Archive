---
title: "Killing X and openbox and starting a new session"
date: 2009-12-15
forum: Desktop Environments
---

### Post by prupert on 2009-12-15
EDIT

So, I figured it out, openbox is a windows manager and although XBMC was closed, I can still access a menu via mouse right-click to get a menu.

I should be able to use lirexec to launch an app to do what I want. 

Talk about needing to RTFM ;)

Hi All

I know a fair bit about Ubuntu, but not so much about some of the inner workings, most notably X and Window Managers.

I have a little Atom/ION box running XBMC on a minimal Ubuntu install. It was installed using the script from here:

[http://xbmc.org/forum/showpost.php?p=441887&postcount=118](http://xbmc.org/forum/showpost.php?p=441887&postcount=118)

From what I can see, openbox is used as the Windows Manager, which auto-launches XBMC on startup. Everything works perfectly, but I would also like to run Boxee on the same box, preferably without XBMC running in the background.

All my attempts so far seem to have failed, as the XBMC session is using the X server, so even when I kill XBMC, there is then no way to kill the X server session it seems.

Can anyone point me to some good resources so I can learn more about X and how to use it with openbox and can thus come to a solution?

I doubt anyone can just post a solution straight out for me, but if they could that would be awesome... ;)

When XBMC is running, I can exit out of it, but then I am left with a blank screen with a mouse cursor in the middle, but I can't access any menus or anything, since Gnome or KDE isn't running. I can access a new login window using Ctrl Alt F2, and login, but then X is still running and I can't open a new openbox session it seems. Is it possible to kill X from the new login or not?

I guess I am just new to what openbox is and how it works, since it comes with no underlying desktop behind it. So any help or suggestions or guidance would be useful.

---

### Post by MooPi on 2009-12-15
Do you know what display manager is working. Is it xdm? If it is, I don't think it supports session changes as does gdm. Not certain but default doesn't.

---

### Post by prupert on 2009-12-15
I think it is xdg, as that is where the openbox config is stored.

In any event, I realise I don't need to change the session, since I didn't realise that openbox continues to run even when you exit XBMC, so I just need to sort out a shortcut to load boxee when XBMC is closed.

Thanks for the response though ;)

---

