---
title: "Add root to gdm"
date: 2010-04-08
forum: Desktop Environments
---

### Post by palz2015 on 2010-04-08
I would like to add the user root to the login screen under the other usernames instead of using the "other" option. Is this possible?

I have already set up a password for root, so this is secure :guitar:

---

### Post by falconindy on 2010-04-08
GDM only lists users with a UID greater than 1000. Root is UID 0.

I question your definition of "secure" if you think logging into Gnome as root is good idea, or even necessary.

---

### Post by kellemes on 2010-04-09
> **palz2015 said:**
> I have already set up a password for root, so this is secure :guitar:

If root has no password there is no password to hack, and no functional root-account to get full control of your system.
I'm afraid you just made your system less secure.

---

### Post by lisati on 2010-04-09
Please read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by _BugsBunny_ on 2010-04-09
Having a root password does not make the system inherently less secure, I'd argue the opposite - but that's a discussion I'm not willing to get into on these boards.

I do agree that logging into Gnome as root is foolish and almost always (I can't think of any exceptions to be honest) not necessary. However it's your system, and if you break it you get to keep all the pieces.

To login as root via gdm (I assume you've already authorized root login via gdm, since it's disabled by default), and have the root user appear on the login screen you need to edit /etc/gdm/gdm.conf
In the **[greeter]** section add the following:
```
MinimalUID=0
```
This may well cause all system accounts to show up. I'm not sure since I've never tried it (as I said allowing root login to Gnome is something that I don't consider advisable). If that does happen there are also Include= and Exclude= parameters available in the **[Greeter]** section. See /usr/share/gdm/defaults.conf for more (do not edit that file).

Both the minimalid setting and the include/exclude settings should also be available via the Security and Users tabs respectively in the Login Window configuration gui.

However, let me repeat - I think this is a **really bad idea**&#8482;. There should be no reason to need to do this. Anything you need to access or run as root should be doable via short term methods (gksu/su/sudo).

---

### Post by palz2015 on 2010-04-09
Ok, I have no gdm.conf !!
This was an issue before, but now it is even worse!
I have custom.conf, but that has no greeter section.
See what I mean:

---

### Post by _BugsBunny_ on 2010-04-09
OK, so it's custom.conf. I gave you the sample file to use. I also told you that it should be accessible via the Login Window setup screen. (gksu gdmsetup). 

I do have a question for you though - **why** do you want to do this? It is a really bad idea.

---

### Post by palz2015 on 2010-04-23
For easy access to root, of course :popcorn:

---

### Post by sisco311 on 2010-04-23
We can't help you, it's against the [thread=716201]forum's policy[/thread].

---

### Post by cariboo on 2010-04-23
If you didn't read the link that lisati gave you, this is a link to the forum policy on root login:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

With that, this thread is closed.

---

### Post by Iowan on 2010-04-23
The RootSudo gives details about the root account, that's not the problem. It's the graphical login that is strongly discouraged.

---

