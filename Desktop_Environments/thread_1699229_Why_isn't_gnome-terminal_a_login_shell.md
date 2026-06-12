---
title: "Why isn't gnome-terminal a login shell"
date: 2011-03-03
forum: Desktop Environments
---

### Post by n8_sl8er on 2011-03-03
I've seen lots of posts all over the Internet that advise users to check the "Run command as a login shell" checkbox in GNOME Terminal under Edit->Profile Preferences->Title and Command.

This makes gnome-terminal run bash/csh/tcsh/ksh as a login shell, which it does not do by default. In turn, running gnome-terminal as a login shell sources the system and user login scripts. This sets up things like colored ls etc.

It seems like gnome-terminal should be a login shell by default. Why isn't it? I've never seen a good explanation of why gnome-terminal isn't a login shell. The "Run command as a login shell" checkbox must be unchecked by default for some good reason, right?

---

### Post by vashfish on 2011-05-04
I'm going to second this... There is no indication in .profile that it will only be run by making this setting change. Took me an annoying while to figure out why $HOME/bin wasn't in my path.

---

### Post by riderplus on 2012-03-21
Yet nobody provided that good reason :guitar: I still don't get it why I have to check that box...it should be set as login shell by default.

---

### Post by mcduck on 2012-03-21
> **riderplus said:**
> Yet nobody provided that good reason :guitar: I still don't get it why I have to check that box...it should be set as login shell by default.

I don't really get why it should be set as a login shell. You are not actually logging in to it,a re you? ;)

Just place your startup scripts in ~/.bashrc (or the equivalent config file for whatever shell you are using) and they will sourced.

The colours are applied in bashrc, unlike what the posts above suggested, and path should be correctly set from the moment you log in, not from the moment you open a terminal emulator, which is why it's done in .profile instead of the shell config file.

In other words, use ~/.profile for everything you want to happen when you log in, regardless if you are logging into your desktop or a TTY. And then use the shell-specific confg fiels to configure the options for each shell you want to use, and to be run each time that shell is executed.

---

### Post by robotslave on 2012-06-16
> **mcduck said:**
> I don't really get why it should be set as a login shell. You are not actually logging in to it,a re you? ;)

Just place your startup scripts in ~/.bashrc (or the equivalent config file for whatever shell you are using) and they will sourced.

There are very good reasons that bash and other shells have both config files that are loaded on login (.bash_profile and friends), as well as config files that are loaded for each new shell instance or subshell (.bashrc & Co).  Most of these reasons boil down to "recursion", but there are others.

In particular, you will want to add to the $PATH environment variable (export PATH=~/foo:/usr/local/bar:...:$PATH) only once, in the top-level shell, rather than have it explode on you when doing things that invoke multiple subshells.

This is why the Ubuntu terminal should invoke "login" (i.e, top-level) shells by default; you are already logged in to your ubuntu account via Unity, true, but Unity does not source .profile, .bash_profile, .bash_login, etc.  As far as bash (or your preferred shell) is concerned, you are not logged in until the first instance of bash is started.

I think there may be some confusion between logging in to an account and a "login" shell; they are not the same thing, and nobody, including Canonical, should assume one from the other.

---

