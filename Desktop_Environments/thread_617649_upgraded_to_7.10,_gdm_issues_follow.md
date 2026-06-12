---
title: "upgraded to 7.10, gdm issues follow"
date: 2007-11-19
forum: Desktop Environments
---

### Post by destiney on 2007-11-19
I upgraded from 7.04 to 7.10.  The upgrade completed with no visible errors.

But now when I try to login via gdm I get this error:


> cat ~/.xsession-errors 

(process:13991): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:13995): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/bash.bashrc: 54: Syntax error: "}" unexpected (expecting "fi")


I cannot directly start gnome or kde, but if I choose "failsafe terminal" in gdm then I get a small console window and I can do `exec gnome-session` or `exec startkde` with no problems.

How can I fix my gdm (or whatever is actually broken)?

Thanks.

---

### Post by destiney on 2007-11-23
I tried this, but it was no help:

apt-get install --reinstall gdm

---

### Post by destiney on 2007-11-23
I also just tried xdm and kdm.  Gnome runs very slowly using either one of them.  Starting Gnome from a failsafe terminal that was started from gdm seems to be the only way to get my desktop going.

---

### Post by destiney on 2007-11-27
Anyone?

---

### Post by mad_goldfish on 2007-11-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/136529](https://bugs.launchpad.net/ubuntu/+bug/136529) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm afraid I don't have a solution, but I finally got round to upgrading a couple of weeks ago and I'm getting the same problem, did you find a solution?

I've also noticed that when I do a shutdown, I get a second gdm login window appearing just after the ubuntu shutdown progress bar, with a blue theme and a flower. If I go to the failsafe terminal, I can see two instances of gdm running. Have you noticed anything similar?

I suspect there's a configuration error somewhere, since the LiveCD works.

Have a log at the attached bug report I found. A few ideas to try in there.

---

### Post by destiney on 2007-12-03
No, I haven't found a fix yet.  I tried all the hints from the bug thread you posted, none of them helped.  My system already has most of the suggested changes they listed there anyway.

I just tried reinstalling everything 'gnome' or 'gtk' related:

yes | \
  for x in `dpkg -l| grep gnome \
      | sort \
      | awk 'BEGIN { FS = "[ ]*" } { print $2 }'`; do \
    echo "apt-get install --reinstall $x"; \
  done

yes | \
  for x in `dpkg -l| grep gtk \
      | sort \
      | awk 'BEGIN { FS = "[ ]*" } { print $2 }'`; do \
    echo "apt-get install --reinstall $x"; \
  done

No change, I still have to login using a failsafe terminal, then `exec gnome-session` to get my desktop going.. a total pain.

---

### Post by fvu on 2008-03-03
I got the same problem on a machine with Ubuntu 7.10.  It appeared `dash' was the default shell instead of `bash':

[INDENT][FONT="Courier New"]$> ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2008-02-28 11:28 /bin/sh -> bash[/FONT][/INDENT]

Furthermore, my `.profile' loaded `.bashrc':

[INDENT][FONT="Courier New"][ -f ~/.bashrc ] && . ~/.bashrc[/FONT][/INDENT]

.bashrc contains commands dash doesn't understand, hence the bash "syntax error" in [FONT="Courier New"].xsession-errors[/FONT].

I was able to fix things by modifying `.profile':

[INDENT][FONT="Courier New"][ $BASH ] && [ -f ~/.bashrc ] && . ~/.bashrc[/FONT][/INDENT]

Or perhaps all of .profile should be moved to .bash_profile?

Freddy Vulto
[http://fvue.nl](http://fvue.nl)

---

### Post by destiney on 2008-03-03
Thanks for the info.

Seems like the simplest solution would be to fix the (wrong) symlink.

ln -sf /bin/bash /bin/sh

That fixes things for my setup at least.

---

