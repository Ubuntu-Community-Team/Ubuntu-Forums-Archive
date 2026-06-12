---
title: "No Greeting Widget???"
date: 2009-06-22
forum: General Help
---

### Post by dharvell on 2009-06-22
Went to turn my computer on, this morning, and rather than the typical username/password dialogue that I am usually greeted by, I was given an error stating that there are no greeting widgets specified with an "OK" button on the bottom.  When OK is clicked, I am sent back to a text screen that shows the status of all of the services that booted [OK] or [FAILED].  Nothing there looks out of the ordinary, by the way.

Any ideas as to how I can fix this, using nothing but shell commands?

All help would be very much appreciated!

---

### Post by celticbhoy on 2009-06-22
Can you say what the last line says?

---

### Post by dharvell on 2009-06-22
The entire error reads:

> No greeter widget plugin loaded.  Check the configuration.

OK

But, it doesn't say WHICH configuration.  Sometimes these error messages are about as helpful as Windows error messages... ](*,)

---

### Post by celticbhoy on 2009-06-22
are you able to type commands?

If so can you login?

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> are you able to type commands?

If so can you login?

Yes... I was able to boot to the Grub bootloader, so I selected recovery mode [the only way I can get on the computer].  I am able to type commands as Root.

---

### Post by celticbhoy on 2009-06-22
A couple of things. First what version of Ubuntu are you using.
second what happens if type 'startx' and then enter?

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> A couple of things. First what version of Ubuntu are you using.
second what happens if type 'startx' and then enter?

I'm using the latest/greatest version [not sure what it's called] with all updates installed.  If I type startx, the graphical interface attempts to boot, but when it does, I get a largely black screen with various random blue and white lines at the top.  On the bottom, I have the usual launcher, program switcher, and clock, but the icons are really spread out [not configured the way I had it, before].  In other words, I guess I would say that it attempts to start, but it does not do so properly.

---

### Post by celticbhoy on 2009-06-22
Can you reboot into recovery again, and move down the list to the xfix option & try that.

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> Can you reboot into recovery again, and move down the list to the xfix option & try that.

Just ran xfix.  Xfix appeared to complete without error.  Attempted to boot normally.  Problem persists:
> 
No greeter widget plugin loaded.  Check the configuration.

OK

---

### Post by celticbhoy on 2009-06-22
Try this :-

[http://albertech.net/2009/04/kde-how-to-fix-no-greeter-widget-plugin-loaded-error/](http://albertech.net/2009/04/kde-how-to-fix-no-greeter-widget-plugin-loaded-error/)

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> Try this :-

[http://albertech.net/2009/04/kde-how-to-fix-no-greeter-widget-plugin-loaded-error/](http://albertech.net/2009/04/kde-how-to-fix-no-greeter-widget-plugin-loaded-error/)

Apparently, dropping to root with networking doesn't work, either.  I can't seem to use apt-get, as is.

---

### Post by celticbhoy on 2009-06-22
When you start up and drop to your error message, can you type on screen? If so, press enter a couple of times and then type login followed by enter again, and see if it will let you in.

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> When you start up and drop to your error message, can you type on screen? If so, press enter a couple of times and then type login followed by enter again, and see if it will let you in.

When pressing <ENTER>, it sends me to a black screen.  I am able to type, but all it does is echo whatever I type.  It doesn't actually execute the commands.

---

### Post by celticbhoy on 2009-06-22
what happens if you type Ctrl-C or Ctrl-Break, Do you get a command prompt?

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> what happens if you type Ctrl-C or Ctrl-Break, Do you get a command prompt?

<ctrl>-c echoes ^C
<ctrl><break> echoes ^[[P

---

### Post by celticbhoy on 2009-06-22
Are you trying to connect to the internet wireless, can you connect with a ethernet cable?

---

### Post by dharvell on 2009-06-22
> **celticbhoy said:**
> Are you trying to connect to the internet wireless, can you connect with a ethernet cable?
I am attempting to connect via wireless.  I'll need to relocate to the basement for a wired connection.  I'll be up in about 5 minutes...

---

### Post by celticbhoy on 2009-06-22
With the wired connection you should be able to login as root from the recovery console with networking. then try the link.

---

### Post by dharvell on 2009-06-22
Alright!  Thanks for pointing that site out to me.  I was able to connect via wired connection, so ran the apt-get install kdebase-workspace and it seemed to do the trick.

That's the last time I try to upgrade my Amarok to the latest version... heh heh heh

Thanks, again, for hanging in there!

---

### Post by celticbhoy on 2009-06-22
Its a pleasure to help anyone in need.

---

