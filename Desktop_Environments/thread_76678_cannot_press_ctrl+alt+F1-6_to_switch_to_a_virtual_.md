---
title: "cannot press ctrl+alt+F1-6 to switch to a virtual console"
date: 2005-10-15
forum: Desktop Environments
---

### Post by zealubuntu on 2005-10-15
I was using Hoary (5.04), I just upgraded to Breezy (5.10) through aptitude several days ago.  Then I got a problem.  I cannot press ctrl+alt+F1-6 to switch to a virtual console, which was working fine in 5.04.

After some google search, I found that people all mentioned that 

in /etc/X11/xorg.conf :

There is a section called ServerFlags

```

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

```
Comment this and then the problem will be solved.


However,  in my xorg.conf file, there is no such a section at all. I have no such an option to comment.  Then I do not know what to do to solve my issue.

Any idea or suggestions??? 

Thanks very much!

---

### Post by popeye on 2005-10-17
Hi,

I have the same problem, werefore i searched this forum a while ago.

It is reported in thread: 

[http://www.ubuntuforums.org/showthread.php?t=70297&highlight=Ctrl+Alt+Fn](http://www.ubuntuforums.org/showthread.php?t=70297&highlight=Ctrl+Alt+Fn)

and :

[http://www.ubuntuforums.org/showthread.php?t=49038&highlight=switch+console+virtual](http://www.ubuntuforums.org/showthread.php?t=49038&highlight=switch+console+virtual)

But up to today no solution has been found.

I tried changing keyboard layouts, but that did not worked out.

I am running breezy on a acer aspire 1312LC which is reported running well on wiki. Which it is. But this virtual switching came with changing to breezy, that it did not work any more. On hoary it worked normal.

I think that it's something to do with the keyboard mapping because in a terminal Ctrl+Alt+Fn1 gives Capital P, Fn1 single gives the help so the button is working.

I don't know how to file a bug otherwise i would do that.

---

### Post by zealubuntu on 2005-10-17
I filed a report here.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17921](http://bugzilla.ubuntu.com/show_bug.cgi?id=17921)

You probably can confirm it. It may help to find out the reason.

---

### Post by neutro on 2005-10-17
I am curious about which keyboard layout you're using. I'm not sure what the problem is, but about 1 week before the Breezy release, the layout I used (ca_enhanced) suddenly got borked after an update or another. 

The symptoms were pretty much the same as what you describe; in fact, in particular, it was the alt key that had problems. I couldn't produce any of the characters that need the alt key, virtual consoles could not be switched, ctrl-alt-Fn produced strange characters or actions, etc.

I switched to another layout (ca(fr)) and everything is fine now. The ca_enhanced layout that I was using seems broken, at least for me, because when I try adding it in the keyboard preferences, an error pop-ups up; and setxkbmap also generates an error.

I opened a [bug](http://bugzilla.ubuntu.com/show_bug.cgi?id=17246), but if the problem is not found only with the ca_enhanced keyboard, I guess it would be important to pinpoint what's wrong exactly. Also, looking back at threads since Breezy was released, there's lots of "<layout> doesn't work".

---

### Post by wujek on 2005-11-03
Hi,
I've got the same problem.
And found a quick solution:

Edit xorg.conf and hash line with "XkbVariant"

Section "InputDevice"
     Identifier "Generic Keyboard"
     Driver "kbd"
     Option "CoreKeyboard"
     Option "XkbRules" "xorg"
     Option "XkbModel" "pc105"
     Option "XkbLayout" "pl"
**#   Option "XkbVariant" "pl" (that option caused the problem, hash it)**
     Option "XkbOptions" "pl" 

Save file and restart gdm.

Thats's all.

It's possible that Option "XkbVariant" depends on non-UTF8 locale settings, I use pl_PL.
Bye now

---

### Post by mmcev106 on 2007-03-03
I had the same problem on Debian after upgrading to xorg 7.1.  To fix it, all I did was reinstall the xbase-clients and xkb-data packages.

---

### Post by dvo on 2007-12-14
I have the same problem (since upgrading to gutsy). 

It did *not* help to:
* reinstall the xbase-clients and xkb-data packages
* add to the InputDevice section in xorg.conf: Option "XkbDisable" "yes"

Ctrl-Alt-Del, Backspace, etc. work fine though.

---

### Post by bmcatt on 2007-12-18
Bump on this as I just upgraded to Gutsy (from Feisty) and my virtual consoles are gone as well. [And, if I switch to them, I can't even switch back. Have to go to a separate computer, ssh in and restart gdm. *very* annoying at best.]

---

