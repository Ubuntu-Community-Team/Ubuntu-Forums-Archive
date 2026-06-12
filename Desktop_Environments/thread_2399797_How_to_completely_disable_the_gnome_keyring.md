---
title: "How to completely disable the gnome keyring?"
date: 2018-08-29
forum: Desktop Environments
---

### Post by jrpstonecarver on 2018-08-29
Hi All,

I'm using an older machine running 18.04.1 as upgraded from 16.04. It seems to be fine, but there is an annoying issue.

I have a set of custom scripts that use gpg to encrypt and decrypt a local file for a couple of uses. Back in 16.04 I found a way to completely disable the keyring so that it would not pop up and ask me for the password every time I ran these scripts. Instead I'd just enter the password right into the terminal window/shell. I need to figure that out for 18.04 now, and I am having no luck. All of the posts I have found on this are old, and most are specific to getting Chrome to stop prompting for the keyring.

That's not enough. I want to go one step farther: I want the keyring to stop entirely. Forever. For all applications. I'll type the passwords when I need them, thank you, and I don't want that software getting in my way. There are some very specific cases where they keyring causes me to have to retype passwords multiple times, and that is pointless. That will go away if I can turn off the keyring, or it used to in 16.04. Assuming that behaviour is unchanged, getting rid of this thing will get me back to where I need to be.

The best advice I've found so far was to remove execute permission from /usr/bin/gnome-keyring-3 and gnome-keyring-daemon, which I tried, but it did nothing. No luck. The silly thing keeps working, though I honestly don't know how the daemon restarts after I've turned off write permission to it. That makes no sense at all. I haven't rebooted yet, but maybe I need to do that.

Any suggestions would be most appreciated. Thank you. This software is very intrusive and really needs a simple way to be removed or disabled.

---

### Post by jrpstonecarver on 2018-08-29
OK. An update on this.

A reboot didn't change anything, but... I had to log back in to google afterwards, which I suspect means Chrome was using the gnome keyring and now it can't do so. That's just fine with me. Oh, and now the keyring daemon is not running and doesn't seem to restart, so that's good.

But the silly UI for passphrase entry still pops up when my scripts invoke pgp, and that is the problem.

But now I recall something from when I did the update to 18.04 and first ran these scripts. I got a message from them saying that --no-use-agent is no longer a supported option from gpg. I removed the option without thinking about it much - since things were working properly except for the silly prompt - but now I have reviewed the manpage for gpg and it says:

       --no-use-agent
              This is dummy option. gpg always requires the agent.

That fills me with foreboding. I am guessing that gpg has been updated, and that my problem really isn't with the keyring, but rather with gpg based keyring management. And the man page for gpp is not longer than War and Peace.

I'll have to poke at that, I suspect. I've changed the subject accordingly.

---

### Post by jrpstonecarver on 2018-08-29
Oh Joy!  I solved this!

Add the option --pinentry-mode=loopback to the gpg command and the entire prompt is suppressed.

Good. Problem solved.

---

### Post by VMC on 2018-12-27
I know this topic is solved and old, but read this explanation:
[https://ubuntuforums.org/showthread.php?t=1655397&p=10301640#post10301640](https://ubuntuforums.org/showthread.php?t=1655397&p=10301640#post10301640)

---

