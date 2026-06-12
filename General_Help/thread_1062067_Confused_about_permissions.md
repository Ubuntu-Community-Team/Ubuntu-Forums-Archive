---
title: "Confused about permissions"
date: 2009-02-06
forum: General Help
---

### Post by MountainX on 2009-02-06
I do not want any other user on my computer, even other sudoers or root, to be able to read the /etc/postfix/sasl_passwd file.

How do I implement this?

Here is what I have now:

```
drwxr-xr-x  2 root         root          4096 2008-12-20 23:09 sasl
-rw-------  1 myuser       myuser          55 2009-01-24 21:19 sasl_passwd
-rw-------  1 root         root         12288 2009-01-28 11:58 sasl_passwd.db
```


But it doesn't work!
```
$ sudo cat /etc/postfix/sasl_passwd
[sudo] password for otheruser: 
[smtp.gmail.com]:587 mypersonalemail@example.com:PasswordIDontWantOthersToSee
```

What permissions should I use? Thanks

---

### Post by cariboo on 2009-02-06
Have a look access control lists (acl) here  is a [link]("http:///tlug.dnho.net/?q=node/171") to a page that explains how to use them.

Jim

---

### Post by MountainX on 2009-02-06
> **cariboo907 said:**
> Have a look access control lists (acl) here  is a [link]("http:///tlug.dnho.net/?q=node/171") to a page that explains how to use them.

Jim

Jim, thanks for the link. But I noticed this sentence:
"And that's it! now you and the www-data user can access public_html, noone else can! (except root, of course). Very useful on shared PCs."

Is that saying that even if I use ACL's, I will not be able to accomplish my goal?

---

### Post by Cinnander on 2009-02-06
If you have the need for other sudoers on your system, you could consider limiting what they can do via the /etc/sudoers file (man sudoers), but give the sudo permisions to their normal user account, or create them an admin account.

You could say, for example, user wwwadmin can run a2enmod, /etc/init.d/apache2 and tail, but that's all.
Then 'sysadmin' can shutdown and reboot the system, and run anything from /sbin, but nothing else.
Then, reserve the "master" root-who-can-run-anything permish for yourself.

IIRC you can do fairly complex stuff (I can't remember the syntax or how, but if you read the manpage you should be set), such as making groups of commands and then you can allow certain users to do certain groups of commands, and allow certain usergroups certain permish as well.

If you try and sudo a command you don't have permission to, you get a warning and afaik that gets logged. By not giving anyone permission to "sudo cat" then you would hopefully be able to prevent them from reading that file. As you have to explicitely ALLOW commands, you also end up preventing them from using sed, groff, etc. to read it too.

HTH

PS: Someone more wise and beardy - feel free to prove me wrong! I've been using this approach myself and would be keen to know how invincible it is.

---

### Post by MountainX on 2009-02-06
Hi Cinnander - that's very helpful. I had no idea about the sudoers file.

I'm reading the man page, but as usual for a man page, it is hard to understand.

Can you (or anyone) give me an example of how to do this:

I want to prevent user1 from accessing any files in /etc/postfix or subdirectories. That's all I need to do.

From the man page, I see the '!' negates. Therefore, what I need might be along these lines (I'm sure my guess is not correct):

Cmnd ::= !/etc/postfix/

I would prefer that they not be able to create a symlink or other way around this restriction.

And, of course, my whole goal is that this be effective even when user1 uses sudo!

So what is the syntax for the sudoers file to accomplish this? Thanks.

------------
UPDATE: I have 3 specific questions:

1. The man page doesn't make it clear if Cmnd is a real token or a documentation placeholder for variable.

2. What does this mean?
```
username ALL=(ALL) ALL
```

3. How would I add the restrictive command to a specific user? 

And of course a specific example as I mentioned originally is greatly appreciated.
Thanks

---

### Post by MountainX on 2009-02-06
Will adding these 2 lines to the sudoers file accomplish what I intend?

```
Cmnd_Alias  NOACESSTOPOSTFIX = !/etc/postfix/

user1 ALL = (ALL) NOACESSTOPOSTFIX
```

I've been searching on Google to help supplement the man page, but it still isn't clear. I do not want to screw up the sudoers file, so I'm asking here rather than do it by trial and error.

UPDATE: the above doesn't work

---

### Post by MountainX on 2009-02-06
Now I see that even by editing the sudoers file, I may not be able to accomplish this simple task.

"once a program is running with sudo it has full root privileges so could launch a root shell to circumvent any restrictions in the sudoers file"

Why is this so hard in Linux? All I want to do is allow someone to do some configuration on my server but not be able to read my passwords. 

Surely there is some way to do this! (And I hope there is a way that doesn't require a full day's investment of my time.)

---

