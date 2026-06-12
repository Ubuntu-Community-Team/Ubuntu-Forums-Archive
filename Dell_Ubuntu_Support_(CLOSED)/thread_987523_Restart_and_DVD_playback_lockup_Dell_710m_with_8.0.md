---
title: "Restart and DVD playback lockup Dell 710m with 8.04"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by christopher1983 on 2008-11-19
I wiped the drive and installed 8.04 after using a friend's notebook that had 8.04-- wonderful.  Considering the problems I have had, I will still take Ubuntu over Microshafted.  Below is a list of issues I had with my hardware and the location of resolutions.  I post them here because it is down to two issues.

- Comcast outgoing mail does not send &#8211; resolved: outgoing mail server smtp.comcast.net:587 (port 587) 

- Wireless not working &#8211; resolved: not sure.  Tried using ndiswrapper and use the windows driver.  That did not fix it, but I was notified then of a driver update by Ubuntu.  It told me firmware was needed also and asked me to install it.  I hit yes and then it worked.

- - DVD no play/poor quality on totem &#8211; resolved: uninstall totem and install Kaffeine, make sure codecs are installed by mplayer and double check cd/dvd drive names.  (mine is scd0)


- Hibernate/standby lockup &#8211; resolved: used uswsus
[http://ubuntuforums.org/showthread.php?t=471855&highlight=restart+hibernate+standby](http://ubuntuforums.org/showthread.php?t=471855&highlight=restart+hibernate+standby)

- Restart lockup &#8211; unresolved

audio/video codecs missing &#8211; resolved: manually install codecs
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If there are any suggests on the restart lockup I am open to them.  If I find any fixes I will post.

Last note, I am new to linux.  This is my first distro.  But I am confident in my abilities and not afraid to wipe and reinstall.  Just don't want to go through the updates and fixes again.

[edited: 11/19 4:30 CST - update DVD fix]

---

