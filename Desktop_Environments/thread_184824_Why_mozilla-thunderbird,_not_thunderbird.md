---
title: "Why mozilla-thunderbird, not thunderbird???"
date: 2006-05-30
forum: Desktop Environments
---

### Post by johann_p on 2006-05-30
I just installed Thunderbird with synaptic (from a repository marked with the ubuntu icon). 

Strangely, the command that was installed is "mozilla-thunderbird" and what is even more strange is that the name or the profile directory is .mozilla-thunderbird, not .thunderbird.

This is not only strange but can mean trouble: people are used to start thunderbird with the command "thunderbird" from the command line, some programs might have the program name "thunderbird" preconfigured.

And most critical: if you migrate your home directory from a previous installation of a different distro (like I did), the program won't find your existing files (which are in .thunderbird) which might cause not only confusion but mentary panic :)

So -- what is the rationale behind renamind thunderbird in Ubuntu Dapper?

---

### Post by aysiu on 2006-05-30
I have no idea. It's not even consistent:

Mozilla Firefox: *firefox*, ~/.mozilla
Ubuntu Firefox: *firefox*, ~/.mozilla
Mozilla Thunderbird: *thunderbird*, ~/.thunderbird
Ubuntu Thunderbird: *mozilla-thunderbird*, ~/.mozilla-thunderbird

I think it's make more sense if Ubuntu's Firefox were called ~/.mozilla-firefox, but it's not--it's called ~/.mozilla

---

### Post by johann_p on 2006-05-30
[quote=aysiu]I have no idea. It's not even consistent:

Mozilla Firefox: *firefox*, ~/.mozilla
Ubuntu Firefox: *firefox*, ~/.mozilla
Mozilla Thunderbird: *thunderbird*, ~/.thunderbird
Ubuntu Thunderbird: *mozilla-thunderbird*, ~/.mozilla-thunderbird

I think it's make more sense if Ubuntu's Firefox were called ~/.mozilla-firefox, but it's not--it's called ~/.mozilla[/quote] 
I do not see a reason why to change the "standard" (default build) naming convention (which is still broken in itself, by the way: the ultimate plan is for all "mozilla-based" applications to share the .mozilla profile directory I think). 

What is so odd about this is that the downloadable binary installation of thunderbird from mozilla.org uses .thunderbird as the profile dir and "thunderbird" as the prgram name but Ubuntu decided for some reason to call both mozilla-thunderbird. 

So, I wander what the reason for this could be ... as far as I can see it has no useful purpose but several disadvantages.

---

### Post by johann_p on 2006-05-31
Can anyone help me with how to best submit a bug for this?

The problem is this: obviously some Ubuntu guru made a patch to Thunderbird to achieve the use of profile location .mozilla-thunderbird.

However, as I pointed out, the current default is .thunderbird and there is a bugzilla bug for changing this to be consistent with FF and become .mozilla/thunderbird (see [https://bugzilla.mozilla.org/show_bug.cgi?id=247973)](https://bugzilla.mozilla.org/show_bug.cgi?id=247973)). 

So if they patched Thunderbird, why did they not patch it correctly? This is going to break eventually and having this fixed to the final optimal situation now would prevent people to have to move/reorganize their Thunderbird profiles during the support time of Dapper.

---

### Post by johann_p on 2006-05-31
OK, for anyone interested, I submitted a bug for this: [https://launchpad.net/distros/ubuntu/+source/mozilla-thunderbird/+bug/47679](https://launchpad.net/distros/ubuntu/+source/mozilla-thunderbird/+bug/47679)

---

### Post by mannheim on 2006-05-31
It's a debian change, not specifically an ubuntu one.

Perhaps (I'm guessing) the debian packages call it mozilla-thunderbird for legacy reasons. I'm guessing that earlier versions of thunderbird were called mozilla-thunderbird, and perhaps debian retained the old name.

---

### Post by johann_p on 2006-05-31
[quote=mannheim]It's a debian change, not specifically an ubuntu one.

Perhaps (I'm guessing) the debian packages call it mozilla-thunderbird for legacy reasons. I'm guessing that earlier versions of thunderbird were called mozilla-thunderbird, and perhaps debian retained the old name.[/quote]

Well, I do not know how to file bugs against Debian nor do I know a lot about Debian, but this is so bad that Dapper should not copy it from Debian.

---

### Post by mannheim on 2006-05-31
Google threw up this: a [bug ]("http://groups.google.com/group/linux.debian.bugs.dist/search?group=linux.debian.bugs.dist&q=333509&qt_g=1&searchnow=Search+this+group")filed on the debian package, but with no follow-ups, as far as I can tell

---

### Post by aysiu on 2006-05-31
For the record, in Hoary and partway through Breezy, Firefox was called *mozilla-firefox*. The profile was still in ~/.mozilla, but the application package was called *mozilla-firefox*. Ubuntu developers have now changed it to just be *firefox*.

Even the location of the plugins has changed as of Dapper: /usr/lib/firefox instead of /usr/lib/mozilla-firefox

---

