---
title: "Cannot login"
date: 2012-11-15
forum: Desktop Environments
---

### Post by JoeHallenbeck on 2012-11-15
Hi all,

There is a situation I can't resolve myself or find anything similar anywhere.

When  I try to log in from the first login form that comes up after  successfully booting Xubuntu up, only a blank page with the standard  wallpaper comes up, nothing else. Neither processor nor the hard drive  does anything noticeable at that moment.

No matter if I choose Xfce or Xubuntu as sessions. When I check .xsession-errors, it contains a number of lines like: 

```

No protocol specified
xprop:  unable to open display ':0.0'

```Loggin via TTY doesn't work either. It displays an error:

```

xvinfo: unable to open display ':0.0'

```There clearly is a problem only with my account as logging in as a guest is still possible.  I've tried to remove .Xauthority or .ICEauthority but that didn't change anything.

The most likely cause of this issue is that I had an external monitor connected to my laptop through a display port and tried to suspend (put into sleep) the PC.  It didn't come through and froze - I had to reset the computer. Since then the problem with logging in occurs. Connecting the monitor back before trying to log in doesn't help.

So the question is: Is there a way to reset which display should be opened upon a login?

Thanks a lot for any sort of help!

---

### Post by JoeHallenbeck on 2012-11-18
Allright guys I know this probably isn't an easy one but I would really appreciate if there was a different solution from a re-install...

---

### Post by steeldriver on 2012-11-18
I can only guess here - and I don't have a Xubuntu box I can try it on - but is there a ~/.config/xfce4-session file you can delete to get back to default session settings?

Also if you were playing with monitors there may be a bad monitors.xml file somewhere?

---

### Post by JoeHallenbeck on 2012-11-19
There is a  ~/.config/xfce4-session directory which is empty...

But there is a file ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml which contains a description of a couple of displays (specifically the ones connected using the Display port).

I tried to remove the file, which didn't help. I also tried to replace it with the same one from a working Xubuntu installation (on the same computer), which contains only one entry for the laptop built-in display. Sadly that didn't help either.

However the  .xsession-errors now contains information that xprop wasn't called with proper arguments, and TTY logging in  gives: "xvinfo: unable to open display".

So apparently playing with the displays.xml caused xprop being called without some necessary arguments and there must be some other files which need to be edited, too...

What would you do now?

Thanks for your help!

---

### Post by JoeHallenbeck on 2012-11-24
What exactly am I to do now? Noone's replying because they didn't see this thread or don't know any possible solution?

Should I now re-post the issue, or add posts like "BUMP" or what? I wouldn't like to lose all the faith in such a (great) service as soon as I bring up the very first question to which I couldn't find the answer anywhere else.

---

### Post by steeldriver on 2012-11-24
Again, I'm guessing and can't try it but I think my next step would be to delete the contents of the session cache - I *think* that's 

```
rm -rf ~/.cache/sessions/
```but have a look around and see if that looks right

I don't really know what would be calling xprop during the session startup - and I definitely don't know why xvinfo is being called in the VT login (unless it's something related to a frambeuffer device?)

That's the best I can do - it's a free bump, at least :|

---

### Post by JoeHallenbeck on 2012-11-25
The fact that it's likely to be weird that xvinfo gets started during the VT login gave me the idea to look around where it's actually started from.

I found it in lightsOn.sh ([https://github.com/iye/lightsOn](https://github.com/iye/lightsOn)), where it's used to garther info about displays currently in use. Since xvinfo wasn't for some reason (related to the original cause) doing what it was expected to do, the script was getting stuck in place.

Now it's all fine, and to be honest I'm quite astonished we put it together. Thanks!

---

### Post by steeldriver on 2012-11-25
Well done! glad you got it fixed

---

