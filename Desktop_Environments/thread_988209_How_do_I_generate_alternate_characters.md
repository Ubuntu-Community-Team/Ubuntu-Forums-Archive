---
title: "How do I generate alternate characters?"
date: 2008-11-20
forum: Desktop Environments
---

### Post by JimGvo on 2008-11-20
I need to generate some Spanish text and need to figure out how to get the ñ (enya) and accented vowels generated since I have the US keyboard without those letters.  I know how to do it in Word and even Windows, but I don't use them unless I'm forced into it.

Thanks,
Jim.

---

### Post by amauk on 2008-11-20
right click on the top panel, and add the "character palette"

selecting characters from the palette will copy them to the clipboard,
Just paste them into whatever you're doing

*edit*
Oops,
just seen the Kubuntu tag
oh well, for any Gnome users you can use the above
not sure about KDE

---

### Post by chejose on 2008-11-20
A better way is to use the us International (with dead keys) keyboard. The right alt + n = ñ, and the same for all the letters that have accents. Also for letters with accents that will allow you to hit the ' key first then the letter and it will print with accent.

José

---

### Post by joey-elijah on 2008-11-20
i asked a question similar yesterday but for swedish umlauts and french accents.

I use a British layout (I'm not ready to give up my "@" and ' " ' placings! The character palette option sucks, tbh. I don't have time to be copy and pasting from it when i'm on MSN etc. Is there a way to get the *windows* like 'ALT + Letter' in Ubuntu? (Gnome, not KDE for me)

---

### Post by DonQuichote on 2008-11-20
Formerly, this used to be in /etc/X11/xorg.conf, but that has changed with Intrepid. Now you have to edit /etc/default/console-setup (as root).

There is an entry called XKBOPTIONS. If you change this to
```
XKBOPTIONS="compose:rwin"
```
your right windows key becomes a "compose key". You can use this for "foreign" characters, like [compose] = E is a euro sign (just type the compose key. do not hold it down like you would do with shift). For the list of combinations, see: [http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co](http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co)

This only comes into effect after you have restarted the X server by either [control]+[alt]+[backspace] (kills all open programs in the graphic environment, take care) or restarting your PC.

---

### Post by JimGvo on 2008-11-28
> **DonQuichote said:**
> Formerly, this used to be in /etc/X11/xorg.conf, but that has changed with Intrepid. Now you have to edit /etc/default/console-setup (as root).

There is an entry called XKBOPTIONS. If you change this to
```
XKBOPTIONS="compose:rwin"
```
your right windows key becomes a "compose key". You can use this for "foreign" characters, like [compose] = E is a euro sign (just type the compose key. do not hold it down like you would do with shift). For the list of combinations, see: [http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co](http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co)

This only comes into effect after you have restarted the X server by either [control]+[alt]+[backspace] (kills all open programs in the graphic environment, take care) or restarting your PC.

Good idea but it pretty much killed my X session.  I couldn't log in with that setting.  I couldn't even get a command console to come up.  I had to reboot into single user mode and edit the file, removing that.

Jim.

---

