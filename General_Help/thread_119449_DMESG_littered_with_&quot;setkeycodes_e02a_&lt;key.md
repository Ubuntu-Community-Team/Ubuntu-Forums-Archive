---
title: "DMESG littered with &quot;setkeycodes e02a &lt;keycode&gt;&quot;..."
date: 2006-01-19
forum: General Help
---

### Post by j-a-p on 2006-01-19
My dmesg output is being corrupted by this annoying error:

```
[4335062.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335063.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.607000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335063.607000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335073.996000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335073.996000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335074.114000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335074.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

Who's got the solution?

---

### Post by dcstar on 2006-01-19
[QUOTE=j-a-p]My dmesg output is being corrupted by this annoying error:

```
[4335062.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335063.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.607000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335063.607000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335073.996000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335073.996000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335074.114000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335074.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

Who's got the solution?[/QUOTE]
This is what I did, create a /etc/init.d/keys-fix.sh (perms 755) file containing the following:

```
#! /bin/sh
#
# Try and cleanup messages in /var/log/messages file:
#
/usr/bin/setkeycodes 0xaa 129
/usr/bin/setkeycodes e02a 129
```
Then: sudo ln -s /etc/init.d/keys-fix.sh /etc/rc2.d/S99keys

This then runs late in the boot-up process, and fixes the issue (which also fills up a log file if left as it is).

I think that I'll submit this as a "HOWTO" in the "Customization Tips & Tricks" section.......

---

### Post by dcstar on 2006-01-19
[QUOTE=dcstar]This is what I did, create a /etc/init.d/keys-fix.sh (perms 755) file containing the following:

```
#! /bin/sh
#
# Try and cleanup messages in /var/log/messages file:
#
/usr/bin/setkeycodes 0xaa 129
/usr/bin/setkeycodes e02a 129
```
Then: sudo ln -s /etc/init.d/keys-fix.sh /etc/rc2.d/S99keys

This then runs late in the boot-up process, and fixes the issue (which also fills up a log file if left as it is).

I think that I'll submit this as a "HOWTO" in the "Customization Tips & Tricks" section.......[/QUOTE]
And having done some further research, I found a better solution:

[https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29](https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29)

---

### Post by j-a-p on 2006-01-19
Thanks for the input, I'll give it a whack.

EDIT:  The second option worked a treat.  You're a gent.

---

### Post by john131971 on 2006-02-08
This page does not exist yet.

is what i get from the url listed....

playing around with the modconf program

...in the mean time I shall return to pounding my head against thy keyboard in hopes of discovery the mystery of the great Xserver....

---

### Post by dcstar on 2006-02-08
[QUOTE=john131971]This page does not exist yet.

is what i get from the url listed....

playing around with the modconf program

...in the mean time I shall return to pounding my head against thy keyboard in hopes of discovery the mystery of the great Xserver....[/QUOTE]
It got renamed:

[https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29]("https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29")

I've changed it in the previous post.

---

### Post by newOldUser on 2006-02-14
dcstar...

The advice at the link you gave worked great. 
Thank you.

Does the fact that I was getting those messages over and over, without touching the keyboard, mean that one or my keys on the keyboard is sticking?

I really don't remember seeing this message in the dmesg list until recently.

Thanks again.

---

### Post by jazzgossen on 2006-02-15
I also started getting these messages pretty recently. dcstar's tip worked for getting rid of the e02a messages, but I still get similar messages regarding e059 and e001. I found these keycodes in /usr/share/hotkey-setup/hp.hk and commented the corresponding lines, but I still get loads of dmesg entries with setkeycodes e001 and e059. Any ideas why?

---

### Post by chugru on 2006-03-19
[QUOTE=dcstar]It got renamed:

[https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29]("https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=%28e02a%29")

I've changed it in the previous post.[/QUOTE]
I, too, want to fix this problem, but the link doesn't work... :( 

Could someone please supply the missing solution?

Thanks...

---

### Post by Scanner on 2006-03-20
This is a bump, the wiki link provided for this solution does not exist, does anyone have the correction?

---

### Post by dcstar on 2006-03-21
I am really pissed-off that some moron has removed this (obviously) useful information from the Wiki, luckily this still exists:

[http://ubuntuforums.org/showthread.php?t=119499](http://ubuntuforums.org/showthread.php?t=119499)

---

### Post by chugru on 2006-03-21
[QUOTE=dcstar]I am really pissed-off that some moron has removed this (obviously) useful information from the Wiki, luckily this still exists:

[http://ubuntuforums.org/showthread.php?t=119499](http://ubuntuforums.org/showthread.php?t=119499)[/QUOTE]
Thanks, David, for sticking with this thread! Your link is definitely the answer!  :)

---

### Post by xoon on 2006-03-27
[http://ubuntuforums.org/showthread.php?t=119499](http://ubuntuforums.org/showthread.php?t=119499)

runs very well. Thanks!

---

### Post by dcstar on 2006-03-28
[QUOTE=chugru]Thanks, David, for sticking with this thread! Your link is definitely the answer!  :)[/QUOTE]
You're most welcome, I am still flabbergasted the someone would remove an obviously useful solution from the Wiki - oh well, I suppose that is the risk in any environment where there is no control on being able to change or delete stuff.

It makes it tough to build up the motivation to actually put things in that Wiki (as you are asked to do) if you find out that they disappear afterwards.....    ](*,)

---

### Post by dentament on 2006-06-15
Maybe this can help..
[http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c](http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c)

---

### Post by dmizer on 2006-06-16
after having traveled to this same thread for the umpteenth time to fix this exact same problem on many many machines (particularly laptops) it occured to me ... should this be filed as a bug?  or perhaps it already has?

found it: [https://launchpad.net/malone/bugtrackers/ubuntu-bugzilla/17569](https://launchpad.net/malone/bugtrackers/ubuntu-bugzilla/17569)
note ... this bug has been marked as fixed.  does this problem still occur in dapper?

---

### Post by teejcee on 2006-06-22
[QUOTE=dmizer]  does this problem still occur in dapper?[/QUOTE]

As far as I'm concerned it does. 

I've commented out the codes from what I believe is the correct file - atkbd.hk - and restarted "sudo /etc/init.d/hotkey-setup restart" without success. 

I've tried "sudo /etc/init.d/hotkey-setup stop".... no luck.

If only we could turn    ](*,)    ,   into   =D>  .....................

---

### Post by socrates32 on 2007-06-13
I'm having the same problem on a generic PC running Dapper. I'm only seeing e001/0x81 and e059/0xd9 in dmesg.

```
[18171404.148000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[18171404.148000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[18171418.608000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[18171418.608000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
```

This doesn't seem to be the same issue that is addressed by fixing hotkeys mapping, which I have tried to no avail.

---

### Post by jazzgossen on 2007-06-15
For what it's worth, I have a Microsoft Natural Wireless keyboard, and I also get the e001 and e059 scancodes in my dmesg. What kind of keyboard do you have?

---

### Post by socrates32 on 2007-06-17
Hmm,,, That's interesting. I too have a Microsoft Wireless Natural (Multimedia) keyboard. Any ideas on how to stop the dmesg messages? They don't seem to be related to keypresses.

---

### Post by LeDechaine on 2008-02-09
Wow, resurrecting an old thread, but anyway.

I'm using a **Microsoft Wireless Comfort Keyboard 1.0A**. One, or maybe two years ago, i've read in a forum that this keyboard sends these weird "scancodes" to tell the computer it's still *there*. (In windows, there is programs that tells the battery life of the keyboard.)

Mines are **e059** and **e002**. Just saw **e03e** too, but only 3 times, so i don't know if it's related to the wireless.

A **not-recommended** harsh way to get rid of this is to add "**dmesg -n 1**" on startup, a command telling dmesg to **ignore** almost all the messages instead of printing them in the log. I've already done this on another box, but well, I obviously really don't recommend doing this, see why:

[QUOTE="man dmesg"][B]-n  1 prevents all messages, expect panic
              messages, from appearing on the console.[/B]  All levels of messages
              are still written to /proc/kmsg, so syslogd(8) can still be used
              to control exactly where kernel messages appear.[/QUOTE]
By reading this i'd say I may have missed a lot of important messages since then! ;)


Back to the subject.. looks like Microsoft Keyboards are "telling" the computer, every 5 to 10 seconds (at least, according to my dmesg), that the keyboard is still *there*, and that the battery is still okay. Since sending this "fake key press" is like pressing a key every 5 to 10 seconds, this is really stupid, 'cause this is actually wasting battery life, and more: this never worked for me. I knew when the batteries were getting low when I had to re-type some letters because the signal wasn't strong enough to get to the pod.

Agreed, this is not really wasting a lot of battery since i've already typed what the keyboard "types" in an hour, but well, 360 to 720 "fake key pressed" in an hour, 8640 to 17280 characters in a day.. Leave your keyboard alone and your computer open one night and it spends battery life as if you wrote an essay while sleeping! (PS: I don't know if it still sends these "fake key presses" even when the computer is off.)

Anyway, if anyone has a way to prevent *only* the "setkeycodes" lines to appear in the logs, and even more "safer", the "setkeycodes" lines only for the M$ wireless "scancodes", this would be greatly appreciated! :)

---

### Post by MaxVK on 2008-03-24
Ill bump this thread by replying since I also have an MS wireless keyboard, and I'm getting the same erroneous keycodes in my logs. (I was in fact researching this issue when I found this thread).

If, as suggested, these codes are coming from the keyboard because it keeps announcing its presence, then I doubt that a fix will be found until Ubuntu is updated enough to see them and throw them out, but its always worth a bump, just in case!

Regards

Max

---

### Post by wfriesen on 2008-05-26
I get the same messages, using a Microsoft wireless keyboard. Mine seem to be mainly e059 and e001.

---

### Post by Skretch on 2008-07-08
Try this solution: [http://ph.ubuntuforums.com/showthread.php?p=5342606#post5342606](http://ph.ubuntuforums.com/showthread.php?p=5342606#post5342606)

---

