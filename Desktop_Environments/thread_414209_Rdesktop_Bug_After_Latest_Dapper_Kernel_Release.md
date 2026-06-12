---
title: "Rdesktop Bug After Latest Dapper Kernel Release"
date: 2007-04-19
forum: Desktop Environments
---

### Post by SuperMike on 2007-04-19
I don't know whether it was the recent X Windows updates, or kernel updates, but one of the two has caused my rdesktop to fail and I can 100% reproduce the way to make it fail. Where do I post this so that the developers can see it?

1. rdesktop to an XP Pro workstation that's service packed all the way.
2. Open a message in Outlook 2000.
3. Choose Help, About Outlook.
4. The rdesktop session dies!

It also happens pulling open dialogs in MS Office, question dialogs that ask with Yes, No, Cancel, and all kinds of things.

When I run rdesktop from command line, and the session dies, it says "Segmentation fault" and no entries are put into the system log.

I'm on kernel 2.6.15-28-686. My Xorg info is:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux workstation 2.6.15-28-686 #1 SMP PREEMPT Tue Mar 13 20:55:53 UTC 2007 i686

After a reboot, I scrolled the kernel back to 2.6.15-27-686, tested, and the same problem occurred.

Anyone have a way for me to get my XOrg one version back so that I could test?

---

### Post by SuperMike on 2007-04-19
All I can say is, rdesktop is pretty critical to my workplace. Unfortunately after a lot of work, which I blogged to death about and spent 6 months working on, I was unable to live with Evolution connecting to my Exchange server and was forced to get off that buggy mess and switch to rdesktop to a windows workstation running Outlook.

---

### Post by SuperMike on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Canonical is tackling this bug here now:

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332)

---

### Post by SuperMike on 2007-04-23
Latest. Well, it's Monday and the bug update at bug # 104332 at Launchpad shows that this problem is resolved in Feisty, but not Edgy or Dapper. They're working on it, but evidently this super critical bug doesn't even have an update on when it can be patched. I'd even be willing to pay someone to show me how to rollback that Xorg patch I applied last Thursday so that I could be functional today with rdesktop.

OMG I depend on rdesktop so much in my day. Wish this weren't the case because some days I can't stand to look at Windows, but alas I have to pull a paycheck somehow in this strange place where I live.

---

### Post by SuperMike on 2007-04-23
Aha! Good news. I just got a Launchpad update one second after posting message # 4 in this thread:

[URL="https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332"]Kees Cook said 10 minutes ago:
Supermike, I'll have a Dapper .deb up for you to try shortly.
[/URL]

---

### Post by SuperMike on 2007-04-23
Mark this one as resolved. A great programmer named Kees Cook implemented a patch for Dapper in this thread:

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/104332)

I tried it and it works.

I imagine this will work into a Dapper package push coming out soon.

---

