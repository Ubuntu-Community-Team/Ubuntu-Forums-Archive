---
title: "REVIEW: CentOS 4.x"
date: 2005-06-14
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2005-06-14
Due to my summer USFIRST robotics projects, I need to host a Subversion repository, along with a few other small public services, on my primary desktop. First, I looked into having VMWare do it, but I wasn't satisfied with the performance impact on my desktop.

Next, I looked at the RedHat OS'es, which had SELinux and Exec-Shield on the security front, not to mention their super-prompt responses to security holes. I didn't like FC3 because of its speed (or lack thereof), and FC4's too new and binary-only module vendors haven't caught up with it.

Next, I thought of the RHEL clones I've read about. After a bit of research, the strongest RHEL clone that could handle both server and desktop tasks was CentOS. So, last weekend, I grabbed a CentOS 4.0 DVD ISO and installed it on my desktop.

INSTALLATION

	After grabbing the ISO's I knew about one problem I'd have to face: Two of my six hard drives are on an unsupported IDE controller (Promise FastTrak 378), which had a patch upstream that still hasn't been merged into a kernel. I filed a request with RedHat, Ubuntu, and Gentoo for the inclusion. All three now include it, but RedHat has only included it in FC4 and other 2.6.11 based releases. Until the driver gets a bit more testing, RHEL won't have it.

So, I decided to get a bit creative: Install on a spare partition, then move the whole install onto the RAID after patching the kernel :)

	The install procedure felt exactly like a Fedora Core install, minus the RedHat logos. I chose a GNOME desktop for now; I'll try KDE later. I know that RedHat's strongest in their GNOME offerings :)


FIRST FEEL:

The install was flawless, and in about 20 minutes, I had a GDM login screen. I logged in, and was greeted by a CentOS logo. Success! I started up2date, and pulled the 10 or so updates. Not bad.

The desktop looks almost exactly like a Fedora desktop, except a different background and logo.  Bluecurve has its presence, folks!

ON THE DESKTOP FRONT:

Well, all I've said from my previous Fedora Core review apply here. Well polished, nicely designed, crisp-looking desktop, with very descriptive and clear icons. Applications are fairly recent. Firefox is at 1.0.4, GAIM is at 1.2.1, Openoffice is at a redhat-patched 1.1.2. Evolution is at 2.0.x, and GNOME is at 2.8.x. KDE is at 3.3.1, BTW. I can live with these.

ON THE SERVER FRONT:
Apache, MySQL, and PHP are all new enough that I'd have no problem with it. I set up an Apache server with mod_dav_svn. It worked quite well. I stress-tested it by committing 20,000 tiny text files, and it crunched the request as fast as Debian or BSD would've.

ON THE SECURITY FRONT:

RedHat offers security updates very promptly, both for desktop and for server packages. A quick look into CentOS history, it seems like the slowest Redhat-to-CentOS response was 6 hours :). I can live with that!

SELinux and Exec-shield are very helpful, too. As quick proof-of-concept tests, I used a Python CGI script that basically behaved like a BASH prompt. As far as the script can see, /home and most of /dev (and many other places) are invisible! Dmesg is filled with a bunch of SELinux denied messages, too. Desktop usage is unaffected by SELinux (targeted policies)

I also did a quick buffer overflow test with Exec-shield, and it promptly terminated the offending application. Success :)


UPDATE PACKS:

As I was testing, CentOS 4.1 came out. It basically is RedHat Enterprise Linux's Update 1. The update mainly comprised of updated packages (including GAIM, Apache, Firefox, MySQL, and others) and a kernel with more drivers. I can quickly see that, with these periodic update packs, RHEL/CentOS will never get as out-of-date as Debian does through its release cycle. Smart idea, RedHat. These update packs are a great way of introducing bugfixes and minor new features during the life cycle of the product.




Overall, I'm impressed with the stability and usability of CentOS, not to mention its security. I highly recommend this distro to those who are:
1)Setting up servers
2)Setting up enterprise-level workstations
3)Setting up Linux systems that are designed to last for years without configuration changes.

---

### Post by poofyhairguy on 2005-06-14
What I have always wanted to know:

CentOS vs. Fedora

If CentOS is so great, waht is advantage of Fedora? Newer stuff?

---

### Post by Xian on 2005-06-14
[QUOTE=poofyhairguy]What I have always wanted to know:

CentOS vs. Fedora

If CentOS is so great, waht is advantage of Fedora? Newer stuff?[/QUOTE]

_ALOT_ newer stuff. :)

---

### Post by mrtaber on 2005-06-14
Definitely newer stuff.  I run RHEL 4 WS, but I've run CentOS 4, and I was very impressed with it.  (Work pays for the RHEL, so there you have it).  Another bonus--programs like VMWare only officially support certain distros...and RHEL 3 and 4 are among those.  So, no nasty surprises for us VMWare users after, say, a kernel upgrade.  We know that VMWare and the distro vendor will be working on it.

In fact, I've run VMWare on CentOS 4 (and, now, RHEL 4), and I'm running XP Pro, Ubuntu Hoary, FC 3, and FC4 on it...solid as a rock.

Good review, JDong :)

Mark

---

### Post by jdong on 2005-06-14
Thanks.

As far as the differences between Fedora and CentOS/RHEL:

Fedora sits on the bleeding edge, with the absolutely newest software and technologies. When they are deemed stable, that turns into RHEL/CentOS.

It's still possible that Fedora has bugs. Look at FC4: 24 hours after the release, there's already 20+ bugfix updates!

For RHEL to have major breakage after release is unacceptable. If you want a dependable system that is ready to be used whenever you need it, go RHEL/CentOS. If you'd like to try out the latest Linux has to offer, go Fedora.

Me? I have FC4 inside VMWare to play with.

---

