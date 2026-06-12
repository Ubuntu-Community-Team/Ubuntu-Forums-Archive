---
title: "APT frustration"
date: 2005-10-02
forum: Desktop Environments
---

### Post by dc2447 on 2005-10-02
I'm havindg osme serious frustration with apt.

Example one azureus - just plain broken.  I understand why (Sun's licencing but still)

> davidcam@vader:~/bin$ sudo apt-get install azureus
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  azureus: Depends: sun-j2sdk1.5 but it is not installable or
                    java2-runtime but it is not installable
E: Broken packages


Example2 wine
From the bwine website:
> September 30, 2005: Wine 20050930 Released

but:

> davidcam@vader:~/bin$ apt-cache show wine | grep -i version
Version: 0.0.20050310-1.1


Not *that* old but old enough to be significantly broken.

I could go on but I think you get my drift.

I know package maintainers have a lot to do but surely an OS that natively supports APT* should be doing better.

* Unlike Fedora

---

### Post by mlomker on 2005-10-02
> Not *that* old but old enough to be significantly broken.

Ubuntu is mostly a volunteer effort (with the exception of a handful few people paid out of grant money).  If you know how to package software then they'll [happily accept]("https://wiki.ubuntu.com/MOTU") .deb files from you to put into the repositories.

There are a number of posts about how to manually install [Sun's JRE]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=sun+jre+.bin") and Azureus (which basically just requires uncompressing into a directory...easy).

---

### Post by tseliot on 2005-10-02
Java RE isn't available in the repos any more, I don't know if it will be again (in Breezy?)

You have to use a guide for that

---

### Post by az on 2005-10-02
[QUOTE=tseliot]Java RE isn't available in the repos any more, I don't know if it will be again (in Breezy?)
You have to use a guide for that[/QUOTE]


Sun has licenced java insuch a way that if you chose to distribute their version of java, you are prohibited from distributing any other version.  So no, it won't be in breezy, in favour of all the different free implementations of java.

---

### Post by dc2447 on 2005-10-02
[QUOTE=mlomker]Ubuntu is mostly a volunteer effort (with the exception of a handful few people paid out of grant money).  If you know how to package software then they'll [happily accept]("https://wiki.ubuntu.com/MOTU") .deb files from you to put into the repositories.
[/QUOTE]

Sure, I understand this.  I do know how to package and do alot of work on RedHat.  I realise the limitations of volunteers maintaining repositories but I'm just getting to the point where APT is becoming less and less usful every day,  Packages are either out of date (wine), missing (KDETV) broken (Azeurus) or were compiled wrong (Kaffine).

I can install all these packages manually but then why bother using Kubuntu at all?  The easier solution is Gentoo or Slack.

I don't want it to sound like I'm bashing Kubuntu and I realsise I could be maintaining some of the packages.

---

### Post by mlomker on 2005-10-02
> The easier solution is Gentoo or Slack.
I don't want it to sound like I'm bashing Kubuntu and I realsise I could be maintaining some of the packages.

If everyone picked a couple of their favorite packages and maintained them then there would be a lot less to compile.  You have to compile everything on Gentoo...compiling something here and there requires a lot less time.

I compile the SVN of amaroK every few days to make sure I have the latest.  It isn't an inconvenience for me because I love the app.

---

### Post by dc2447 on 2005-10-02
> If everyone picked a couple of their favorite packages and maintained them then there would be a lot less to compile. You have to compile everything on Gentoo...compiling something here and there requires a lot less time.

Actually on Gentoo you only actually install what you need much like BSD ports - in reality you send very little time compiling new versions especially on high spec machines.

I take your point about maintaining packages - I'm not sure how different deb files are but with Redhat all we need is a Spec file and the latest source.  This means that  the building of RPM's becomes pretty much an automated process.  Can't debian/ubuntu updates be automated in some way?

---

### Post by localzuk on 2005-10-02
[QUOTE=dc2447]Sure, I understand this.  I do know how to package and do alot of work on RedHat.  I realise the limitations of volunteers maintaining repositories but I'm just getting to the point where APT is becoming less and less usful every day,  Packages are either out of date (wine), missing (KDETV) broken (Azeurus) or were compiled wrong (Kaffine).
I can install all these packages manually but then why bother using Kubuntu at all?  The easier solution is Gentoo or Slack.
I don't want it to sound like I'm bashing Kubuntu and I realsise I could be maintaining some of the packages.[/QUOTE]

I don't understand your complaint?

Either you don't like apt (which you mention 'APT is becoming less and less useful')?
or you think that packages should be better maintained.

Which one is it? Apt works like a charm. Sure there are a few ideosyncracies/bugs to work on but it provides 99% functionality - which I would hedge bets that yum doesn't.

If you have gripes about package maintenance, this has been covered adequately by prior posters - and you have failed to comment usefully on this (ie Java licensing/azeurus).

---

### Post by mlomker on 2005-10-02
> Actually on Gentoo you only actually install what you need much like BSD ports 


That's an option with Ubuntu as well.  Do a **server** install at installation and add packages one at a time.  The large ubuntu-desktop metapackage is for linux users that don't want or (in the case of newbies) don't know how to determine what they need.


> I'm not sure how different deb files are but with Redhat all we need is a Spec file and the latest source. 

Not much different.  You can apt-get the dh-make and debhelper packages.  Here's a [how-to]("http://www.ubuntuforums.org/showthread.php?t=49216") for a simple application.

---

### Post by dc2447 on 2005-10-02
>  don't understand your complaint?

Either you don't like apt (which you mention 'APT is becoming less and less useful')?
or you think that packages should be better maintained.

Which one is it?  The repositories for sure.  I use APT on Fedora.

---

