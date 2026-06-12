---
title: "Help with user groups"
date: 2007-06-12
forum: Desktop Environments
---

### Post by Pro_D on 2007-06-12
I am still learning lots about Ubuntu (well Kubuntu 7.04 in this case - more options).  I haven't been able to find answerers to this yet (with lots of googling and site searches) and I lost my original train of thought due to my switch dying right before trying to post this.

I am trying to get a handle on user groups.  I figured they were a bit like windows user groups (winNT/2k) but it seems I might be wrong about that.  They seem to be a bit more comprehensive actually.

For example: What is the lpadmin group.  It seems to have something to do with printing but thats all I have figured out thus far.  Actually lpadmin seems to be a bad example, it seems to have to do with CUPS access rights (man lpadmin).

I am starting to think that groups might be more like services that a user has access to but that doesn't seem quite right either - where is the admin service...

If someone has some good links on this I would thank you.  I am actually interested in some good reading material I just can't seem to find it.  If I am already close to the concept some slight clarification would be appreciated too...

---

### Post by kidders on 2007-06-14
Hi there,

I *think* I see where the confusion is...

Where it's possible to do so, Linux users prefer to run things using unprivileged accounts. Since you mentioned them, take printer services as an example. By running them as root (or, for that matter, any user), your system would be vulnerable to bugs in printer management software. Additionally, anyone who wanted to interact with it might have to take on root privileges in order to do so. Now, imagine you did this...[LIST]
[*]Created a new user "testuser" and a new group "testgroup".
[*]Wrote & compiled some sort of simple application "testapp".
[*]Created an empty log file in /var/log, called "testapp.log".[/LIST]Now, suppose you ran...[LIST]
[*]**sudo chown testuser:testgroup /usr/local/bin/testapp /var/log/testapp.log**
[*]**sudo chmod 550 /usr/local/bin/testapp**
[*]**sudo chmod 640 /var/log/testapp.log**[/LIST]The result would be an application that could only be executed by members of the "testgroup" group, the only member of which is "testuser". That application would have exclusive access to somewhere to log its activity, but (assuming the rest of your system is secure) couldn't access anything else of any importance. As a result, even if "testapp" was some sort of server that contained a serious bug allowing remote users to manipulate it into deleting things, there would only be one file on your entire box that it could damage. Large, complicated services like Apache run this way. (The account Ubuntu uses to run web servers is called "www-data".)

So, when you install something like CUPS or maybe a mail server, it's pretty common practice for package managers to create dedicated users & groups, for the purpose of (a) denying unrelated things access to important files, and (b) trying to avoid introducing new security problems into a previously watertight system.

User groups have other purposes though. For instance (assuming you have a sound card), try something like **ls -l /dev | grep audio**. Then type **groups** to reveal your account's group memberships. You'll notice that sound-related system devices are owned by the "audio" group, and that your system **chmod g-rwx**-ed them, so access to your sound hardware is restricted to members of "audio". This is important, because malicious use of sound hardware can crash your system. Whether *you* have access depends on the output of **groups**. As you can imagine, the "www-data" user is not a member of "audio".

Another reason for using groups is revealed by typing **sudo grep '%admin' /etc/sudoers**. _Be careful with this command, as /etc/sudoers is an extremely security-sensitive file!_ You should see...```
$ sudo grep '%admin' /etc/sudoers
%admin ALL=(ALL) ALL
```This means that members of the "admin" group have unrestricted (because of all the 'ALL's) access to the **sudo** command. Ordinarily, **sudo** will try to limit what people can do with it ... in fact, unless it's told otherwise, it won't let anyone use it at all.

Groups have lots of other uses, but these are some of the basic ones. 
> I am starting to think that groups might be more like services that a user has access toThat's certainly one way of thinking of them, but hopefully my post helps you see how that's achieved. In the end, it all comes down to which account is running a given application, and how its group memberships intersect with your filesystem privileges.

Hopefully something in here will give you some ammunition for a few web searches. In practical terms, the main thing to take away from an exploration of user/group management is the danger of deliberately defeating the system. For instance, Linux beginners often do things like this, opening up gaping security holes in the process...[LIST]
[*]Using **sudo** without understanding what they're doing.
[*]Setting umasks that are all zeros.
[*]**chmod 777**-ing things.
[*]And so on...[/LIST]

---

### Post by Pro_D on 2007-06-14
[reads above post a couple of times]

Ok, I think I have some good concepts to search more with now (on system and on web).

Kind of a side thing (but related), it would appear that the password-less login guest account I setup can't actually destroy the system but just that account (based on some tests and reading).  Only thing I worry about is audio since apparently that can crash the system... that stuff is for later though and another thread if need be.

Thanks much.

---

### Post by kidders on 2007-06-14
> **Pro_D said:**
> [reads above post a couple of times]Heh sorry... I'm not sure I expressed myself very well! I was trying (in my own weird way) to explain how you might've gotten the *impression* that there's more to groups than just collecting users together ... but there isn't.

> **Pro_D said:**
> Only thing I worry about is audio since apparently that can crash the system.Yeah, giving people direct access to hardware is an act of trust. You should never give such privileges to anyone who won't actually be sitting in front of your PC when he uses it (ie logging in locally).

Specific to audio devices, and without wanting to get into too much detail (it's a little off topic hehe), there are some measures you can take to reduce the risk associated with allowing untrusted local users to access your sound card.

You see, it is possible to allow audio-related services to elevate their CPU scheduling priority, resulting in significantly better performance on heavily-loaded systems. People do this to stop sound skipping when their system is doing lots of things at once. Often it involves setting certain commands' SUID or SGID bits, allowing the user running them to acquire elevated privileges. (Ie the commands run with the privileges of the user that *owns* them, not the user that's executing them.) Anyhow, you would want to check that your system is _not_ configured to behave this way, thus preventing anyone from deliberately fabricating & playing maliciously crafted audio files, or hijacking your CPU ... but also preventing them from getting the best possible performance of your your computer.

It's noteworthy that it is almost never appropriate to grant remote users access to audio equipment.

Anyhow, if you run into trouble with your sound, someone here will certainly help you. :-) (In any case, most audio-related problems are outside my area of expertise.) If you're concerned about people doing damage to your system, always remember to jealously guard every single privilege & permission. Never grant anything more access than it need to function.

> it would appear that the password-less login guest account I setup can't actually destroy the system but just that accountThat sounds reasonable. For best security, all users should normally be confined to their home directories ...[LIST]
[*]If you prevent them from writing to anywhere else, your system is pretty safe from direct interference.
[*]By preventing them from *reading* certain stuff (most notably other users' homes, and some files in /etc), you help ensure users can't look inside files that might contain passwords (or other sensitive information) they could use to elevate their privileges.[/LIST]Is that any help?

---

### Post by willdex on 2007-07-27
Ok, I've messed up a bit. I'm the only person using the computer, and I needed to make a directory on my Maxtor remote hard-drive. So I went ahead and unchecked all the privileges for myself in **System -> Administration -> Users and Groups** simply because I'm quiet lazy putting sudo thing all the time. Two problems: 
**1.** I'm still unable to make directories on Maxtor:
```
will@will-desktop:/media$ umount disk
umount: /media/disk is not in the fstab (and you are not root)

``` Great, I'm not root, let's see what happens with sudo:
```
will@will-desktop:/media$ sudo umount disk
will@will-desktop:/media$ 
```As you can see, it just returns to **will@will-desktop** [I think because I've removed all the privileges, yikes!]. Maybe use Eject? No?
```
will@will-desktop:/media/disk$ eject disk
eject: tried to use `/dev/disk' as device name but it is no block device
umount: /media/disk is not in the fstab (and you are not root)
eject: unmount of `/media/disk' failed
``` Ok, that was a no. Here's what happens when I try to make a directory:
```
will@will-desktop:/media/disk$ mkdir whatever
mkdir: cannot create directory `whatever': Read-only file system
will@will-desktop:/media/disk$
```Sudo?
```
will@will-desktop:/media/disk$ sudo mkdir whatever
will@will-desktop:/media/disk$
```
**2.** When I go to **System** now to change all the privileges back to normal, I can't see **Users and Groups** anymore. Can't show a screenshot because don't know how to insert it in the Gimp from the Clipboard :( I'm a mess.

---

### Post by HermanAB on 2007-07-27
If you get tired of typing sudo, use sudo to set user to root:
$ sudo su -
Password: whatever
#

Now you should have a root # prompt.

Cheers,

Herman

---

### Post by willdex on 2007-07-27
Wow, this is awesome. I'll definitely keep that in mind. However, the two problems still persist: I can't make any directory b/c the disk is **Read-only file system** or whatever, so screw that. The real problem consists of being unable to navigate through the *System -> Administration -> Users and Groups* just to change back things to the way they were b/c now **there is no** *Users and Groups*! Rebooting didn't help, logging out didn't help either. I'm still at a total loss.

---

### Post by HermanAB on 2007-07-27
Make yourself a new user account, then log out and log in again.

---

### Post by willdex on 2007-07-27
Ok, I think I'd need that **Users and Groups** tab for that. And, if not,  in terminal I'd have to put something like **adduser bill**, and this what it gives me:
```
will@will-desktop:/home$ adduser bill
adduser: Only root may add a user or group to the system.
will@will-desktop:/home$ sudo adduser bill
will@will-desktop:/home$ ls
will

```Just goes back to *will@will-desktop:/home$*.

---

### Post by HermanAB on 2007-07-27
$ sudo groupadd joesoap
$ sudo useradd -s /bin/bash -g joesoap -d /home/joesoap joesoap
$ sudo passwd joesoap
Password: supersecret
Again: supersecret

Ctrl-alt-delete and log in as joesoap

---

### Post by willdex on 2007-07-28
```
will@will-desktop:~$ sudo groupadd bill
Password:
will@will-desktop:~$ sudo groupadd bill
will@will-desktop:~$ sudo useradd -s /bin/bash -g bill -d /home/bill
will@will-desktop:~$ sudo passwd bill
will@will-desktop:~$
```Whatever I do using sudo redirects me back to will@will-desktop. I'm afraid I'm going to have to format.

---

### Post by HermanAB on 2007-07-28
Now that you have created the new user account, you have to log out and log in again as the new user.  Press Ctrl-Alt-Backspace to restart X and log in again, or reboot the machine.

---

### Post by willdex on 2007-07-28
I'm not sure I've created a new user:
```
will@will-desktop:/home$ ls
will
will@will-desktop:/home$
```

---

### Post by HermanAB on 2007-07-28
sudo ls /home

---

### Post by willdex on 2007-07-28
```
will@will-desktop:~$ sudo ls /home
will@will-desktop:~$
``` If I **do** have to format, what's easier: through Windows [since I still have it], or through Ubuntu?
What is the command line for setting the privileges?

---

### Post by willdex on 2007-07-28
Holy crap! I got it to work after glancing at [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=458118&highlight=lost+admin+privileges"). Thanks guys. ***_This is how we do it!_***..

---

