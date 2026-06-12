---
title: "Executing a command at startup"
date: 2009-02-12
forum: General Help
---

### Post by unimatrix on 2009-02-12
I'm trying to execute this command when the system boots:
```
echo -en "\xf0\x00\x20\x21\x61\x00\x00\x00\x7f\x00\xf7" > /dev/snd/midiC0D1
```

I've put it into /etc/rc.local but that didn't work. The command apparently did not get executed. It should enable my IR receiver, but it didn't. I have to run the command manually. :(

Other commands do get executed from rc.local though. Any ideas why this echo refuses to?

---

### Post by RHTopics on 2009-02-12
I am just guessing, but it could be some other process maybe coming along after rc.local is executed and resetting /dev/snd.

Look at the README file in /etc/rcS.d and consider putting in a script that is executed from /etc/rcS.d.  Have it run as one of the last scripts to ensure it is not reset or overwritten.

---

### Post by unimatrix on 2009-02-13
Yes, that did the trick. Thank you.

If someone else is also trying to figure this out, here's what I did:
I've put a new script into /etc/init.d called enable-ir-receiver (and gave it a chmod +x), then I linked it to /etc/rcS.d/99enable-ir-receiver

So lesson learned:
/etc/rc.local gets executed before all of the rcS.d scripts - WHY is that so is another question... but that's just one of the mysteries of the universe.

EDIT: Not the real solution... Look below.

---

### Post by RHTopics on 2009-02-13
unimatrix,

I am glad my suggestion worked for you.

Like you, I always thought /etc/rc.local was one of the last things to be executed in the boot process.  Yet there as been concerted efforts by the developers to reduce the bootup time and so it could be rc.local is now run parallel with other bootup processes rather than as the one of last things to run.

---

### Post by unimatrix on 2009-02-15
Ok, bad news. It seems the trick didn't work after all. (I thought it did because I only restarted the computer instead of powering it off and then on)

This time I tried executing the init.d script that contains my command manually. And what do you know, it didn't work. I tried the following:
sudo /etc/rcS.d/S99-enable-ir-receiver
sudo sh /etc/rcS.d/S99-enable-ir-receiver
sudo /bin/sh /etc/rcS.d/S99-enable-ir-receiver
sudo su
/etc/rcS.d/S99-enable-ir-receiver
sh /etc/rcS.d/S99-enable-ir-receiver
/bin/sh /etc/rcS.d/S99-enable-ir-receiver
(and all of the above directly with the /etc/init.d/enable-ir-receiver ... where the rcS.d link points to)

Nothing worked until I manually pasted the echo command in the terminal. I think the issue might be with sh refusing to execute that command.

---

### Post by unimatrix on 2009-02-15
Hmm... It turns out that when you do
```
echo -en "foo" > bar
```
with /bin/sh
the result in bar will be
> -en foo

And it works perfectly if I use /bin/bash.

******* /bin/sh... Why on earth is Ubuntu using this defective piece of **** of a shell by default?!

---

