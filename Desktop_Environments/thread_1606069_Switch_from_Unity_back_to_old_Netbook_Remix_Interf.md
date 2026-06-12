---
title: "Switch from Unity back to old Netbook Remix Interface"
date: 2010-10-26
forum: Desktop Environments
---

### Post by salukibob on 2010-10-26
Hi Folks,

Like so many people on these forums, having just upgraded to 10.10, I've discovered Unity, and I'm afraid its not for me. I absolutely loved the previous interface, and was quite shocked and saddened to see it disappear. 

But I'd like to keep all the other new software that comes with 10.10. So my question is, can I install the old 10.04 beautiful interface to run on the 10.10 edition? Re-installation is a MS solution, that turned me on to linux in the first place!

Thanks for any help
Rob

---

### Post by kerry_s on 2010-10-26
only the 2d version is available in 10.10, search "netbook" in synaptic.

---

### Post by salukibob on 2010-10-26
Thanks for your reply Kerry. 

Unfortunately, the netbook-launcher package is just to ease transition to unity, and if you try to remove unity, it removes the netbook-launcher package as well. Or am i looking at the wrong package?

Can I just add the 10.04 repository to my sources.list and install the old netbook-launcher?

Thanks
rob

---

### Post by kerry_s on 2010-10-26
it's netbook-launcher-efl

---

### Post by salukibob on 2010-10-26
ahh, thats brilliant. Thanks very much

rob

---

### Post by thelehmanlip on 2010-10-26
i tried uninstalling unity and installing ubuntu-netbook and the netbook-launcher-efl.  when i logged out and logged in, the screen was blank. it was white with a cursor. i reinstalled unity on the command line. 

What am I doing wrong?

---

### Post by thelehmanlip on 2010-10-26
i found my problem: you need to uninstall Unity (which will also uninstall ubuntu-netbook) and install ubuntu-netbook-efl and netbook-launcher-efl

---

### Post by simon_brooke on 2010-10-29
apt-get says

'E: Unable to locate package ubuntu-netbook-efl'

Yes, I've done apt-get update (and apt-get upgrade). I have the same 'blank white screen with cursor' problem described above, and, additionally, alt-f2 does not bring up a launcher typein bar, so I can't launch synaptic.

Ah!

If I kill gdm and then run startx, I get a standard Gnome desktop - a great improvement.

---

### Post by marcus0263 on 2010-10-29
Excellent, I'm going to try it.

I LOVED v10.04 but upgraded to v10.10 as to get trim support and absolutely HATE the new interface.  I've went back to 10.04 and tried installing the maverick kernel and my broadcom drive keeps puking.

I'll try the suggestion in this thread, hope it works.

WTF did they do to the interface?  The old interface was smart, well laid out and worked really well, this new PoS Unity blows major chunks!

---

### Post by marcus0263 on 2010-10-29
Meh, removed Unity, installed netbook elf, it pulled unity back in.  So I removed unity again and it stayed gone.  Interface is lacking what v10.04 had a bit, not as polished.  But the straw that broke the camels back was when it rebooted I get nothing.

Tired of messing with it, going back to v10.04, Unity sucks big time.

---

### Post by Cima Coppi on 2010-10-30
I've messed around myself, and as like the rest of you I don't like Unity that much (as of the current state)

You don't need to uninstall Unity though. Just install the "efl" components mentioned above and re-login. Make sure to choose the right interface on the bottom of the login screen. I get Ubuntu desktop, Ubuntu netbook remix and UNR 2D. Choose the last "2D" and you get something that looks like UNR Lucid. The interface looks a lot like an early alpha, icons are twice as large as needed, somewhat retarded.

Unity could be something if it were more flexible, themeable, hideable and so forth.

I wish you all nice All Hallows weekend!

/Thomas

---

### Post by yakinikku on 2010-11-02
> **Cima Coppi said:**
> I've messed around myself, and as like the rest of you I don't like Unity that much (as of the current state)

You don't need to uninstall Unity though. Just install the "efl" components mentioned above and re-login. Make sure to choose the right interface on the bottom of the login screen. I get Ubuntu desktop, Ubuntu netbook remix and UNR 2D. Choose the last "2D" and you get something that looks like UNR Lucid. The interface looks a lot like an early alpha, icons are twice as large as needed, somewhat retarded.

Unity could be something if it were more flexible, themeable, hideable and so forth.

I wish you all nice All Hallows weekend!

/Thomas

i tried the 2d interface and it didnt work correctly, gnome was overlayed on top of the interface.  i posted a thread and got no help, it is something i can reproduce on another laptop that is running ubuntu desktop edition.  if anyone can help please reply to this thread

[http://ubuntuforums.org/showthread.php?t=1594102](http://ubuntuforums.org/showthread.php?t=1594102)

---

### Post by TheAnachron on 2010-11-02
Kerry, can you please tell me how you did that awesome bar?

---

### Post by benlau on 2010-12-28
> **Cima Coppi said:**
> I've messed around myself, and as like the rest of you I don't like Unity that much (as of the current state)

You don't need to uninstall Unity though. Just install the "efl" components mentioned above and re-login. Make sure to choose the right interface on the bottom of the login screen. I get Ubuntu desktop, Ubuntu netbook remix and UNR 2D. Choose the last "2D" and you get something that looks like UNR Lucid. The interface looks a lot like an early alpha, icons are twice as large as needed, somewhat retarded.

Unity could be something if it were more flexible, themeable, hideable and so forth.

I wish you all nice All Hallows weekend!

/Thomas

I have installed those efl package and removed unity , however, it still don't show the gdm screen , then I need to modify /etc/gdm/custom.conf'session to une-efl.

Then it could show the old netbook interface, but the launched application do not show in full screen mode and use the global menu bar . Anyone know how to fix it?

Thanks.

---

### Post by slorge on 2011-01-05
when I up'd to 10.10 on my Dell mini-9, I hated Unity.  So I switched to the gnome desktop and never looked back.  I'll be checking in on the thread, though.  I liked the 10.04 GUI, just because it gave the mini-9 that true "netbook" look, but to be honest, I'm still much more at ghome with gnome! :p

---

### Post by mdimitro on 2011-02-05
> **benlau said:**
> I have installed those efl package and removed unity , however, it still don't show the gdm screen , then I need to modify /etc/gdm/custom.conf'session to une-efl.

Then it could show the old netbook interface, but the launched application do not show in full screen mode and use the global menu bar . Anyone know how to fix it?

Thanks.

You'll also need to install `window-picker-applet`, `go-home-applet`, and `maximus`. If you selected "Delete" when Gnome complained about the lacking applets, you'll just have to add them back into your menu bar, otherwise they should load the next time you log in. Maximus will also load the next time you log in, or you can just launch it with Alt-F2 (which works!), but it will be automatically added to the auto-run list either way.

Now I just want to know how I can get my icons to look normal-sized again. Still, this is a huge improvement over Unity with Mutter.

---

### Post by CryNGRoad on 2011-02-06
There is also a package called ubuntu-netbook-efl-default-settings, which, for me, put everything back to *normal*.

---

