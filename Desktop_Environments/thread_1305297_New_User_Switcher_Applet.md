---
title: "New User Switcher Applet"
date: 2009-10-29
forum: Desktop Environments
---

### Post by Doughy on 2009-10-29
The new 9.10 release messed up the user switcher applet.  My wife and I switch sessions quickly through the switcher applet, but now her name is not listed when we try to switch.  We have to click on "Switch user..." then it drops back to the GDM, then enter password.  It used to be possible to immediately switch.  Anyone know how to revert back to the old way?

---

### Post by Doughy on 2009-11-01
Does anyone know of any plans to change this back to the original "FAST" user switcher?  This is killing me.  Doesn't anyone else have a problem with this?

---

### Post by petri on 2009-11-02
> **Chauncellor said:**
> Canonical has dubbed this a "missing feature" in Karmic to be re-implemented in Lucid.

Sucks, I know... I hate that new applet.

"missing feature"?  - that was stupid... yeah I know I don't have to pay for Ubuntu but still. :---)

---

### Post by tom17 on 2009-11-02
I too am missing this feature. It seems that it's a commonly used feature for living room pc's with multiple users.

It now takes a lot longer to switch between my wife & I as it takes time for the GDM login screen to load up and then we need to enter the password.

The previous functionaly, though somewhat lax in the security dept, was ideal for this kind of usage.

I understand it is planned to be fixed in Lucid, but i'd rather not wait. Is there a way to get it working again in Karmic?

Thanks,

Tom...

---

### Post by petri on 2009-11-05
Barking at wrong tree maybe? On my laptop with Nvidia I can change user and on my stationary with Atis crossfire I can't.

This problem was present with Jaunty to september this year so I blame AMD on this one.

Edit: the fast-user-switcher or what-ever-it's-called isn't present for Karmic and the source.tar.gz or what.ever.it's.called didn't work for me.

---

### Post by JohnFr on 2009-11-09
This is a showstopper for me.  I upgraded an old machine to
9.10 to try it out.  I immediately ran into this issue  -- no
fast user switcher.  I won't be upgrading my other machines until
this is resolved.  For a home machine login security is achieved
by physical access restriction.  The inability to switch users
without going through the login process is crucial.

---

### Post by tom17 on 2009-11-09
Chauncellor,

That doesn't do the exact same thing as the old fast user switch applet. It does the same thing as the existing applet in Karmic, which doesn't help.

Tom...

---

### Post by JimiGoth on 2009-11-11
Just throwing my hat in the "not having the fast user switch stinks" camp.  The upgrade from 9.04 went so smooth, I was so psyched, and that's the first thing I saw.  Big bummer.

---

### Post by JimiGoth on 2009-11-11
Here's a workaround: use the terminal keyboard shortcuts; it asks for the password once, but the next time it just switches, no problem.

For me, ctrl-alt-F7 is the first login, then ctrl-alt-F9, ctrl-alt-F10, etc, for subsequent logins.

Seems to me, if you can do this, you should be able to do it from an applet...

---

### Post by tom17 on 2009-12-25
Does anyone know if there is a fix for this yet?

Tom...

---

### Post by hariks0 on 2009-12-26
Is it possible to change the order of the items in the User Switch Applet ?

---

### Post by tom17 on 2009-12-26
Thanks Chauncellor.

Guess i'll just have to wait till march before I upgrade :(

Tom...

---

### Post by tom17 on 2010-03-24
Do we know if this is actually fixed in Lucid?

Tom...

---

### Post by tom17 on 2010-03-24
Sweet, i'll check out the beta today then.

Tom...

---

### Post by tom17 on 2010-03-25
Confirmed.

Slightly different than before, but hell, it works!

not sure if I like the new window control location though :)
</offtopic>

Tom...

---

### Post by tom17 on 2010-03-25
Yeah I saw it a few days ago as it was all over /.

I aint going there lol, Mark has made his stance quite clear.

Anyway, I guess this thread is pretty much done now. Thanks for your help.

Tom...

---

### Post by spillz on 2010-04-14
> **tom17 said:**
> Confirmed.

Slightly different than before, but hell, it works!

not sure if I like the new window control location though :)
</offtopic>

Tom...

I tried to install fast-user-switcher-applet and got an error. Is there something else I'm supposed to install instead?

---

### Post by BlackShift on 2010-05-14
> **Doughy said:**
> The new 9.10 release messed up the user switcher applet.  My wife and I switch sessions quickly through the switcher applet, but now her name is not listed when we try to switch.  We have to click on "Switch user..." then it drops back to the GDM, then enter password.  It used to be possible to immediately switch.  Anyone know how to revert back to the old way?

Identical situation here.

It is still not fixed in Lucid, the 'wishlist' bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/501864](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/501864)

I added a comment there on how I fixed it by disabling locking the screen entirely by using gconf-editor to set /desktop/gnome/lockdown/disable_lock_screen to True.

That way it is not possible to lock the screen at all anymore, but that is fine for me.

Another way is to setup the login to not require a password and use 'Switch From ..' to switch users, but this is slightly slower.

---

