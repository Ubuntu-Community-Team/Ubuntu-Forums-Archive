---
title: "Time change mechanism"
date: 2008-03-09
forum: Desktop Environments
---

### Post by FLPCGuy on 2008-03-09
I've been unable to find a post that discusses the mechanism for changing the system time for daylight time.  Since my Edgy system did not change to US daylight time today in spite of an update a few days ago, I'd like to know how this is controlled and why my system didn't change.  

I'm assuming my specific problem has to do with blocked ports. I get no error or change when I sync with a time server, but I'd welcome a discussion of the basic mechanism for tracking when daylight time applies.

Here's what I've found so far.  The package tzdata applies time zone and DST rules.  To check your version use the command dpkg --status tzdata

On Edgy the output looks like this:
root@Dell4100:/etc# dpkg --status tzdata
Package: tzdata
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 5764
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Architecture: all
Version: 2007k-0ubuntu0.6.10.1
Replaces: libc0.1, libc0.3, libc6, libc6.1, locales
Description: Time Zone and Daylight Saving Time Data
 This package contains data that represent the history of local time for many
 representative locations around the globe. It is updated periodically to
 reflect changes made by political bodies to time zone boundaries, UTC offsets,
 and daylight-saving rules
Xsbc-Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
root@Dell4100:/etc#

---

### Post by FLPCGuy on 2008-03-09
oxBulbizarre has posted valuable info on this issue. (thank you!)
[http://ubuntuforums.org/showthread.php?t=150472&page=2](http://ubuntuforums.org/showthread.php?t=150472&page=2)

Apparently the script /etc/init.d/hwclock.sh reads parameters from /etc/default/rcS then adjusts the hw clock according to those settings. One key parameter in rcS is whether the system clock is set to localtime or UTC.  Many have observed that if UTC is no, no time change is applied to the hwclock according to the DST rules stored in the binary tzdata library.

(If you are dual booting with Winders you may not want Ubuntu to make DST adjustments.) 

I'm still looking for a good authoritative summary of the entire process.

---

