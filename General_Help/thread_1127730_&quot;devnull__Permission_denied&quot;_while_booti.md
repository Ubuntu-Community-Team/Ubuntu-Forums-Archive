---
title: "&quot;/dev/null/ : Permission denied&quot; while booting"
date: 2009-04-16
forum: General Help
---

### Post by Greenbean209 on 2009-04-16
I installed intrepid ibex through wubi successfuly. I boot into ubuntu and this is what happens exactly:
The loading bar shows up with the ubuntu logo. The bar fills after a while. Blank black screen. A white flashing cursor shaped like an _ underscore shows up. Then some text runs through. (I'm not able to read this and neither is it possible for me to find out what it says). Then a line shows up that says 
```
bash- : /dev/null : permission denied
```
this line repeats for a undetermined amount of times. It finally stops on its own and the shows me a command prompt like this "ubuntu@ubuntu~$". And that is the problem. I don't know what this command prompt is for or who the user is supposed to be. Normaly on my other machine when I run a terminal it gives me "john@johndesktop~$". So I have no idea what ubuntu@ubuntu could be. 

I have tried researching this problem and I have found similar problems but all of those cases occur after the computer asks for a login & password. For me on the other hand, it just happens right after I try booting. Also in the cases I mention, people respond by telling them some strange command
```
chmod 666 /dev/null
```
that will remove the permission on the file "/dev/null". I have heard that this works but I have also heard that this should not be done because it will allow any body to access the null device.

Help is greatly appreciated!

---

### Post by Greenbean209 on 2009-04-16
so can anybody help?

---

### Post by Greenbean209 on 2009-04-17
any body

---

### Post by jackhe22 on 2009-04-17
I would use that command, and afterwards type reboot, then it should boot up normally!

---

### Post by Greenbean209 on 2009-04-17
ok I'll try...
If anyone objects say nay.

---

### Post by Greenbean209 on 2009-04-17
oh yeah and before I do that... can anyone tell me how to find out the current permissions incase I want to chmod it back to its original settings?

---

### Post by trlkly on 2009-04-17
Yeah, don't worry about anyone being able to use /dev/null. That's the way it's supposed to be. It's not really a device, anyways, just a blac khole to funnel out information you don't want to see.

For example, wine by default outputs a lot of error messages, even though these errors often don't cause any real problems, So one could use the following command if they don't want to see those error messages.

```
wine program.exe > /dev/null 2>&1
```

This pipes all standard messages and error messages to /dev/null, where it just disappears.

So, in other words, jackhe22 is right.

ETA: Not that you'll need it, but the command that will let you see the current permissions is 

```
stat --format=%a /dev/null
```

---

### Post by Peasantoid on 2009-04-17
Allowing anybody to use /dev/null is a non-issue. It's basically a bottomless pit for data.

---

### Post by Greenbean209 on 2009-04-17
ok I get what you're saying. I know that this is the device for trashing data for the monitor. Just so we're clear though... changing the permission in the /dev/null, This won't allow me to accidently write something to it, right? Also is it normal for the permissions to be set to 666, or is that just a way of getting around the permission problem?

---

### Post by trlkly on 2009-04-17
Well, it's set to 666 on my system by default. So I think that's what it's supposed to be.

---

### Post by Greenbean209 on 2009-04-17
ok thanks I'll try it now then

---

### Post by Greenbean209 on 2009-04-17
here is what happened...
Input:
```
chmod 666 /dev/null
```
Output:
```
chmod: changing permissions of '/dev/null' : operation not permitted
```
Input:
```
sudo chmod 666 /dev/null
```
Output
```
[  199.566395] aufs au_xino_do_write:280:sudo[6226]: I/O Error write failed (-5)
[  199.566394] aufs au_xino_write:280:sudo[6226]: I/O Error write failed (-2)
```

then I typed sudo reboot and I rebooted. no change happend in the permissions. Any ideas?

---

### Post by trlkly on 2009-04-18
Sorry, I don't know what those errors mean. My only suggestion is to try doing it in Recovery Mode. 

It should be on the menu when you first boot your computer (after the BIOS screen that tells you what computer you have). If not, press escape at that time to force it to open.

This will take you to a command-line only version of Ubuntu. Login as normal (your password won't show, but it will work), and it'll be just like a Terminal.

Try the sudo command there.

(Sorry if I'm telling stuff you already know.)

---

### Post by Greenbean209 on 2009-05-04
how do you log in through command line. What do you type to log into your user?

---

### Post by Stephen Howard on 2010-01-06
Its a permissions problem (sometimes happens after an upgrade goes a bit screwy).

Easy to fix though - all you need to do is become root user and recreate the device (/dev/null is a virtual file, not a real one, so its okay to have linux deal delete it and create it).

Use these commands to first delete it and then recreate it:

rm /dev/null
mknod -m 0666 /dev/null c 1 3

---

### Post by lotharmat on 2010-01-06
> **Stephen Howard said:**
> Its a permissions problem (sometimes happens after an upgrade goes a bit screwy).

Easy to fix though - all you need to do is become root user and recreate the device (/dev/null is a virtual file, not a real one, so its okay to have linux deal delete it and create it).

Use these commands to first delete it and then recreate it:

rm /dev/null
mknod -m 0666 /dev/null c 1 3

Quick question - I have looked at the man page for mknod but cannot see what c 1 3 mean.

I am a curious bugger who needs to know! :grin:

---

