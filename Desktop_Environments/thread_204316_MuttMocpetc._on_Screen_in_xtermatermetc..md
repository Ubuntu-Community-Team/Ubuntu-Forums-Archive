---
title: "Mutt/Mocp/etc. on Screen in xterm/aterm/etc.?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by LadyDoor on 2006-06-26
Hi,

I didn't know where else to put this, but I guess Ratpoison/Screen is kind of my "desktop," I guess.

So, because of my chronic mouse-not-working problems on my laptop, I use Ratpoison WM. I also prefer to use lightweight stuff when possible (because it's a bad laptop...but cheap!). Specifically, I generally like to use console applications for a lot of things like music and email (mocp and mutt, respectively). I would use a console IM application, but centericq doesn't seem to support AIM at all anymore and ptyaim and pork, apparently, cause me to be ignored by people on Windows computers who use the latest AIM (but not previous AIMs). Anyway, I usually run them within screen, because that way I get a bazillion terminals for the price of one. However, I have to use the GNOME Terminal because for some reason, XTerm, ATerm, and all the more minimal terminals seem to screw up screen somehow such that mocp and mutt go crazy and don't work. However, these programs work fine on those terminals if screen is not running. Does anybody know how to fix this? Some configuration option? Anything?

Any help would be much appreciated.

--Door

---

### Post by LadyDoor on 2006-07-01
*Ka-bump*

---

### Post by LadyDoor on 2006-07-02
*bumpety-bump*

---

### Post by allnameswereout on 2006-08-06
Try after screen started export TERM=xterm-color

---

### Post by LadyDoor on 2006-08-08
Hmm, that seems to help in an XTerm (though not aterm). Thanks muchly.

--Door

---

### Post by Riverside on 2006-08-08
> **LadyDoor said:**
> I would use a console IM application, but centericq doesn't seem to support AIM at all anymore and ptyaim and pork, apparently, cause me to be ignored by people on Windows computers who use the latest AIM (but not previous AIMs).apt-cache search -f naim

I haven't tried it, but a FreeBSD using friend uses it daily, and says it's very good.

---

### Post by LadyDoor on 2006-08-09
Thanks...I've actually tried Naim before, but it seems to act funky in combination with GNU screen (or maybe it's just me making a mistake). Lately I've actually been using a combination of bitlbee and irssi, which is *quite* effective. Thanks for everyone's replies, and I hope maybe someone else found this to be useful at some point.

--Door

---

### Post by allnameswereout on 2006-08-14
I'm also using Bitlbee + Irssi works like a charm indeed. There are even Irssi plugins for Bitlbee. For example, there is one allowing you to see when someone is typing a message.

As for Aterm try in Aterm (before starting screen in a fresh Aterm) this:
env | grep TERM
Then do exactly as I said but instead of using xterm-color try the TERM variable Aterm said it had before Screen started. Let me know if this helps.

I have a problem with my TERM variable as well. Somehow, in screen + Mutt, the arrows in Mutt denoting a reply to a msg (useful in long conversations such as mailinglists) is instead a diff character, a weird A. If anyone knows how to solve this I'd like to know.

---

