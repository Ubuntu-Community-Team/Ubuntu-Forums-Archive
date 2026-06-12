---
title: "The NetworkManager Applet keyring problem again"
date: 2009-05-17
forum: General Help
---

### Post by Benboom on 2009-05-17
I'll bet that somewhere there's a FAQ with the answer to this but I haven't been able to find it; I've Googled this and see there are tons of people who have a problem like mine or something similar, and I also see that most of them don't seem to be able to fix it.

Ever since I got my wireless working every time it starts up I get the window that says "The application &#8220;NetworkManager Applet&#8221; (usr/bin/nm-applet) wants access to the default keyring, but it is locked." So I have to give it my password, and it goes away.

I have autologin enabled (apparently this is related) but none of the fixes I have seen mentioned seems to work, and in fact most of them seem to involve prefs or pref managers that aren't even on my machine, as near as I can tell.

I'd really like the machine to just start up without any prompts that require user interaction; it's just a testing machine with nothing of any value at all on it so security is just not an issue.

I'm pretty new to linux, so apologies if this is something obvious.

Can no one rid me of this troublesome prompt? :)

Thanks.

PowerMac G4 Sawtooth, Ubuntu 9.04

---

### Post by kpkeerthi on 2009-05-17
[http://ubuntuforums.org/showpost.php?p=7190594&postcount=123]("http://ubuntuforums.org/showpost.php?p=7190594&postcount=123")

This worked for me.

---

### Post by hobo14 on 2009-05-17
Check this thread: [http://ubuntuforums.org/showthread.php?t=1153326]("http://ubuntuforums.org/showthread.php?t=1153326")

I put a solution in post #8, and there is an even better one in #10.

---

### Post by lovinglinux on 2009-05-17
Solution in the quote below:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by Benboom on 2009-05-17
> **kpkeerthi said:**
> [http://ubuntuforums.org/showpost.php?p=7190594&postcount=123]("http://ubuntuforums.org/showpost.php?p=7190594&postcount=123")

This worked for me.

Wow, me too! That's so simple...thanks a ton!

Thanks to everybody for the responses; I've copied them all into my scrapbook because I think the info applies to some other things as well.

---

### Post by lovinglinux on 2009-05-17
> **kpkeerthi said:**
> [http://ubuntuforums.org/showpost.php?p=7190594&postcount=123]("http://ubuntuforums.org/showpost.php?p=7190594&postcount=123")

This worked for me.

I think this option is only available on Jaunty or for wired connections. I don't have this option on Intrepid wireless connection. Anyway, the solution I have posted above works too.

---

