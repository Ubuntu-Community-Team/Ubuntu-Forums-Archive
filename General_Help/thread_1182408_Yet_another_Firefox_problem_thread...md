---
title: "Yet another Firefox problem thread.."
date: 2009-06-08
forum: General Help
---

### Post by Mirge on 2009-06-08
So, I'm having to pretty constantly restart Firefox now, which is becoming more & more of a hassle. It seems to be only Firefox that's having the issue too...

Only add-on is Firebug.

I'll be just browsing the forums or looking up work related resources, playing Mafia Wars on facebook or what have you...

Then I open a new tab, click Home button (which takes me to [http://www.google.com/](http://www.google.com/)).. it'll say "Looking up........" and stay at that for quite a while (10, 15, 20, 30 seconds or more). If I press the Home button again, it'll say "Stopped", but the tab still shows "Loading". Nothing happens.

I close the tab, open a new tab, click Home.. nothing happens. Restarting firefox fixes it... it almost sounds like a DNS issue, but if that were the case, I'd suspect it'd be like that with every browser (tried Opera and Konquerer).

Using Firefox 3.0.10 from Ubuntu repo's... and have ipv6 disabled in about:config. Any thoughts? Thanks!

---

### Post by Pork_Samichez on 2009-06-08
I can think of few things...

-Check out the errors on the command line after launching firefox in a terminal
-install wireshark if you have access to root and check out what's being reported when firefox is stalled.
-ctrl+shift+j will bring up the error console for firefox which may reveal something

Edit:  Also Flash could be causing problems since you said you were messing around with facebook apps

---

### Post by Mirge on 2009-06-08
Thanks for the suggestions. I'll give those a shot & post back with my findings the next time it errors on me.

---

### Post by Mirge on 2009-06-09
> **Pork_Samichez said:**
> I can think of few things...

-Check out the errors on the command line after launching firefox in a terminal
-install wireshark if you have access to root and check out what's being reported when firefox is stalled.
-ctrl+shift+j will bring up the error console for firefox which may reveal something

Edit:  Also Flash could be causing problems since you said you were messing around with facebook apps

Firefox error console didn't show anything useful, just JS errors from previous sites is all I could see.

Wireshark was running, and this is what I saw when the "Looking up...." took forever. It's happening both with Pandora (flash) and without any flash.

You can see the screenshot at: [http://img151.imageshack.us/img151/5861/wireshark1.jpg](http://img151.imageshack.us/img151/5861/wireshark1.jpg)

---

