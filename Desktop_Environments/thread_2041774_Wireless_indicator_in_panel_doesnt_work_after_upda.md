---
title: "Wireless indicator in panel doesnt work after update"
date: 2012-08-13
forum: Desktop Environments
---

### Post by tdlam on 2012-08-13
Hi folks,
I got a weird bug here. I am running Xubuntu 12.04 with xfce 4.10. I ran a series of updates a day or two ago that came up with update manager. After which now my wireless indicator in my panel will not show any connections once it locks on. I can connect to the internet ok but it wont tell me that I am connected. There are no bars just a small icon with the red "X" on it that usually came up when there was no connection. The drop down menu also doesn't show that I am connected. It does show me available wireless networks though and lets me choose them and once chosen I can connect to them but again no indication that I am actually connected. Its weird and a little annoying.
Anyone have any ideas?

Thank you in advance.

---

### Post by tdlam on 2012-08-14
sorry for bumping this but does anyone have any thoughts on this?

Thanks!

---

### Post by OrangeCrate on 2012-08-16
I'll confirm the problem, and will provide another bump.

I just did a fresh install of Xubuntu 12.04, and I have the same problem. After the install, it worked fine prior to installating the updates, so, it's obviously something in the updates themselves that borked it.

I've looked through the update history in Synaptic, but, I don't recognize what specific update might have caused the problem.

One diference - unlike you with the red "X", I have the normal icon, but, it does not show the connection - it's just grayed out.

---

### Post by Toz on 2012-08-16
Have a look in your ~/.xsession-errors file to see if there is anything specific in there about nm-applet. It might give a clue as to what is happening.

---

### Post by OrangeCrate on 2012-08-17
Adding...

Unless I don't know what I'm looking for (quite possible), I didn't see anything in the errors file.

Just to check, I just completed a fresh install of Ubuntu 12.04 on a spare computer. The bug is there too - the behaviour is the same as Xubuntu.

Personally, I think I'll write this whole thing off, as just sloppy housekeeping by the developer/maintainer, and wait until they issue a correction...

---

### Post by OrangeCrate on 2012-08-17
> **Toz said:**
> Have a look in your ~/.xsession-errors file to see if there is anything specific in there about nm-applet. It might give a clue as to what is happening.

Sorry, I meant to post this in support of the comment I made in my last post. Here is the output of the xsession-errors file:

-----

openConnection: connect: No such file or directory
cannot connect to brltty at :0
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-fsbKzc/pkcs11: No such file or directory

(polkit-gnome-authentication-agent-1:1407): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1407): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(xfce4-settings-helper:1438): xfce4-settings-helper-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:1470): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:1470): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:1470): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

-----

---

### Post by Toz on 2012-08-20
The log file seems sparse. Can you run the following command:
```
pastebinit ~/.xsession-errors
```
...and post back the link that it generates?

---

### Post by OrangeCrate on 2012-08-20
> **Toz said:**
> The log file seems sparse. Can you run the following command:
```
pastebinit ~/.xsession-errors
```
...and **post back the link that it generates**?

[http://paste.ubuntu.com/1156998/](http://paste.ubuntu.com/1156998/)

---

### Post by Toz on 2012-08-20
Not much there.
Can you create a second account on your computer, login and see if the problem persists? This would help identify whether it is a problem with your profile or a system problem.

---

### Post by OrangeCrate on 2012-08-21
> **Toz said:**
> Not much there.
Can you create a second account on your computer, login and see if the problem persists? This would help identify whether it is a problem with your profile or a system problem.

As mentioned earier, I've already confirmed the problem with a new install of Ubuntu 12.04. The problem exists in both operating systems. Prior to applying the inital set of updates on a fresh install, the indicator works fine on both versions. It's after the changes/updates are applied, that the indicator disappears. That tells me, that one of the updates is causing the problem.

Yesterday, once, when I booted up Xubuntu, the indicator worked properly. However, when booted again, it disappeared. When I first booted the computer this morning, I had the indicator again, but when I just booted now, it is gone again.

---

### Post by tdlam on 2012-08-22
Ok so it seems that I am not the only one. Thanks for posting and sorry for the silence as I have been away for a bit . I tried to post the results of 

pastebinit ~/.xsession-errors But I get nothing in my terminal. Am I doing something wrong? And yes I agree with the poster. It happened after a recent upgrade. I serched forums, google etc. but find nothing specific about this issue except for here. 

as an aside, I also have a different Xubuntu XFCE 4.10 on another computer and LINUX MINT XFCE 4.10 on another computer. SAfter running updates on these...my desktops bonked. So it seems something is up with the updates or update that is breaking something. But that is a different issue but I only mention it as it too happened after an update

---

### Post by Foxien on 2012-08-22
Hi there guys,

I have same problem on my Xubuntu 12.04, with XFCE 4.10, after last update (2 weeks ago, I think) I have wifi indicator on my panel dark gray, like if I have very low wifi signal, but when I look into other tools, there is around 95% signal strenght.

There is my .xsession-errors - [http://paste.ubuntu.com/1161628/]("http://paste.ubuntu.com/1161628/")

Thanks for response!

---

### Post by OrangeCrate on 2012-08-22
Checking, I find that the affected version of XFCE that I am using is 4.8 not 4.10. Plus, as I mentioned in an earlier post, it is also affecting a straight up, fresh install of Ubuntu 12.04.

---

### Post by tdlam on 2012-08-23
I actually had to install the "Wavelan Plugin" on my panel just so i can see what network I am connected to now since the indicator plug in is now broken.  I find it a bit annoying as I am a bit of a perfectionist with my install...by that I mean I have small tolerance for things that don't quite work right and will spend hours chasing down solutions...but this one has me stumped.:(

---

### Post by Toz on 2012-08-23
What happens if you kill the currently running nm-applet process (this should remove the applet from the indicator plugin):
```
killall nm-applet
```
...and restart it (add it back):
```
nm-applet &
```

Does it work?
Are there any error messages displayed in the terminal window after you run it manually?

---

### Post by Toz on 2012-08-23
Also just came across this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1035590]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1035590"). Does booting the previous kernel fix the problem?

---

### Post by OrangeCrate on 2012-08-23
> **Toz said:**
> What happens if you kill the currently running nm-applet process (this should remove the applet from the indicator plugin):
```
killall nm-applet
```
...and restart it (add it back):
```
nm-applet &
```

Does it work?
Are there any error messages displayed in the terminal window after you run it manually?

This option doesn't work, and there are no error messages.

I'll try the previous kernel next...

---

### Post by tdlam on 2012-08-23
well I tried kill in terminal as you suggested and then reinstated it as you suggested and got a slew of errors here:
```
 (nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:58:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:162:12: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:163:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:164:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:194:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:293:14: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:494:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:515:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:533:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:539:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:544:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:570:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:597:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:605:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:623:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:637:21: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:637:23: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:681:23: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:693:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:693:23: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:693:25: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:704:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:704:21: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:704:23: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:704:25: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:731:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:732:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:738:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:774:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:775:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:790:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:799:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:806:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:820:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:832:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:850:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:868:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:886:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:908:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:914:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:914:15: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:915:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:972:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:978:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:979:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:979:13: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:979:15: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:979:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1011:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1012:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1017:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1018:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1018:13: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1070:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1072:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1093:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1095:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1120:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1122:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1134:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1136:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1177:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1273:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1274:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1303:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1304:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1411:14: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1411:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1439:22: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1449:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1466:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1479:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1544:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1558:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1559:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1579:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1737:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1749:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1805:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1817:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1818:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1818:13: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1818:15: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1818:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1825:18: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1825:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1825:22: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1834:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1834:20: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1834:22: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1835:11: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1871:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1871:23: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1878:19: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1878:21: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1879:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: misc.css:13:17: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: misc.css:15:16: Not using units is deprecated. Assuming 'px'.

(nm-applet:11217): Gtk-WARNING **: Theme parsing error: misc.css:16:11: Not using units is deprecated. Assuming 'px'.
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area
]
```unfortunatley I have no idea how to boot an earlier kernel...I'm not that proficient in linux as some good folks are...

---

### Post by december0123 on 2012-08-23
I too have this bug (xfce 4.8 ) and i can confirm that booting into previous kernel fixes it.

---

### Post by OrangeCrate on 2012-08-23
+1 on the confirmation.

@tdlam

Hold down the "Shift" key during boot, and the grub menu will come up. Scroll down to previous kernels (something like that), hit enter, and then choose the kernel there.

3.2.0-23-generic

-----

So, thanks Toz for the launchpad link. I suppose you could set that kernel as default, but, I'm assuming that the next kernel update will pickup the permanent fix. The indicator doesn't work, but, the connection does, and I know now why it doesn't, so, it's no big deal any more. Thx all for the insight and help.

:)

---

### Post by Toz on 2012-08-23
It might be helpful to add to the bug report to encourage the devs to have a look at it. Or at least click on the "Does this bug affect you" link to be counted.

---

### Post by OrangeCrate on 2012-08-23
> **Toz said:**
> It might be helpful to **add to the bug report** to encourage the devs to have a look at it. Or at least click on the "Does this bug affect you" link to be counted.

Done.

---

### Post by tdlam on 2012-08-23
sorry guys you all have it up on me...I see no way on that site to click  on the "does this bug affect you" link...dont see it at all. Not even  sure how to even file a bug report. I guess I'm just not as proficient  as you good folks
@ orangecrate (great name BTW lol)   Thanks for the kernel boot tip...but holding the shift key during boot up did nothing
@ Tor thanks for chiming in...
so it looks like this is going to have to wait until the devs fix it?

---

### Post by OrangeCrate on 2012-08-23
> **tdlam said:**
> sorry guys you all have it up on me...I see no way on that site to click  on the "does this bug affect you" link...dont see it at all. Not even  sure how to even file a bug report. I guess I'm just not as proficient  as you good folks

Don't worry about it, knowledge comes with time. You need to sign up for a Launchpad account to be able to see the link.

> @ orangecrate (great name BTW lol)   Thanks for the kernel boot tip...but holding the shift key during boot up did nothing

Thanks. The original orange crate was a tricked out 1975, bright orange, Dodge "surfer" van. The current incarnation, is a custom painted, dark burnt orange, Harley Fat Boy. Take a look at this link for ideas to get the shift key thingee to work:

[http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

If you opt for the gedit option, I think that you'll have to install that package in Synaptic to be able to use that command. Shift should work, if it doesn't, I don't know what to add, sorry.

> @ Tor thanks for chiming in...
so it looks like this is going to have to wait until the devs fix it?

I can't speak for Tor, but, that's what I'm going to do. I once bought an Ubuntu Dell computer. An Inspiron 530N, which came with Fiesty, if I remember correctly. It worked fine, until the next version of Ubuntu came out, and then it didn't. Frankly, I gave up a long time ago, expecting that anything built by a "committee", so to speak, will ever be able to sync together in a way, that it all works at the same time. I've never seen it with Linux/Ubuntu in the seven years I've been using it.

---

### Post by OrangeCrate on 2012-08-24
It appears that the problem will be addressed...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1035590](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1035590)

---

