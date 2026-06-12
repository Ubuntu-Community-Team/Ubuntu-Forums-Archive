---
title: "/var/www and /svnrepos permissions"
date: 2009-01-31
forum: General Help
---

### Post by kerryhall on 2009-01-31
Hey, so I am trying to figure out the proper way to admin a system.

What should the permissions of /var/www be? Who should the owner be? What group should it be a part of? Right now the user owner and the group are both www-data. Is this a good idea?

At the same time, if I am setting up an svn repository in /svnrepos, what should the permissions be? Who should own it? What group should it be a part of? Right now I can't do a commit without sudo (grrr!) I feel like the permissions should be similar to /var/www, but I can't remember what I did.

Obviously I don't want any big security holes, and I want certain users to be able to modify the contents of /var/www, and to be able to do svn commits.

I have done extensive searching of these forums, but I have found a wide variety of answers ranging anywhere from "Only use sudo to modify the contents of /var/www" to "add your users to the www-data group"

Thanks!

---

### Post by kidders on 2009-02-02
Hi there,

> **kerryhall said:**
> I have found a wide variety of answers ranging anywhere from "Only use sudo to modify the contents of /var/www" to "add your users to the www-data group"Imo, both of those recommendations are terrible ideas. Forcing the use of sudo to alter /var/www means routinely running text editors, copy commands, etc. as root for no reason. A bug in an X app or a typo in a command you type would result in who knows what executing on your system without a safety net. Security in Linux relies heavily on the assumption that root privileges only get used for operations that really need them.

Making the user your web server runs as the owner of /var/www means that (in theory) anyone in the world can modify/erase the entire directory. You'd be surprised how easily well-known security issues can creep into a website. For the sake of a simple example, a PHP script passing part of a querystring to a shell unescaped would allow a malicious user to launch a phishing attack from your server.

What to do depends on how many people work on your websites, and how. For example, if it's just you, running **sudo chown -R kerryhall: /var/www** seems the best idea. The owner of temporary directories & other locations your scripts need to write to should be set to www-data on a case-by-case basis, and kept outside your sites' document roots where possible. Another approach might be to set up a "web editors" group. Alternatively, if a lot of editing or updates happen over SSH, creating an unprivileged "web editors" *user* for everyone to share greatly simplifies permissions management.

I hope that helps.

---

### Post by kerryhall on 2009-02-03
Damn, I was going to give you a "thanks" but they are gone. When they come back I will thank you.

My current setup is this: I have a web server, running one web site, and I am the only user who updates it. However, in the future it is possible I might need to add more users.

I will definitely try what you suggested! It was very helpful.

Two more quick questions:

1. How do I make an underprivileged user account?
 
2. How do I secure my subversion repos? (I don't want them to be viewable from the outside world without a password)

Oh man, I was adding myself to a group, and I couldn't modify files, I thought I was going crazy. The two things that tripped me up were having to log out before I was a member of the group, and setting permissions recursively.

Thanks!

---

### Post by kidders on 2009-02-03
> **kerryhall said:**
> Damn, I was going to give you a "thanks" but they are gone.Hehe... Seems the feature was causing database issues.

If I were you, I would take ownership of /var/www myself. You can change that in the future if you need to.

> **kerryhall said:**
> 1. How do I make an underprivileged user account?An account is unprivileged if you don't do anything to explicitly change that (eg give it access to **sudo**, membership of root or system groups like audio).

> **kerryhall said:**
> 2. How do I secure my subversion repos?You could use an SSH tunnel (Often called svn+ssh).

The two issues you ran into with groups are by design, so you needn't worry. Group membership determines too much about a user's operating environment to allow changes to take effect in running shells. Logging out & back in again is the simplest way to be sure you're up to date. Also, as you've noticed, Unix permissions don't propagate downwards or get inherited unless you explicitly tell them to (eg **chmod g+s /var/www** or **chmod -R +X /var/www**).

Anyhow, glad I could help.

---

### Post by josheby on 2009-02-22
Hello all, I have a quick question...  I have been looking into the same thing and as kerryhall noticed, there are 15 different answers out there...   I wanted to run what i did by you to make sure there are not any problems with the way I did it...

I simply assign the group with my user name to the /var/www group and chmod 775...

ls -l returns this following:
drxwrxwr-x 4 root josheby 4096 2009-02-22 16:51 www

Any reason that setting it up that way is a bad idea?

Also... I checked and apache is running as www-data... is there any instance where www-data will need access to /var/www?  If so, how does it get it?   The main reason I ask is that I though in past versions of ubuntu that I had messed with I thought that after installing apache www-data was the owner of /var/www, but now I see it as root:root after installation...

Thanks for your help!!!

---

