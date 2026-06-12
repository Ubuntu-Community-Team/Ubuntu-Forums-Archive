---
title: "~&lt;dir&gt; system wide shortcuts"
date: 2009-04-21
forum: General Help
---

### Post by sloggerkhan on 2009-04-21
I know you can type the tilde ~<dirname> for a list of shortcut dirs
```

~avahi/         ~haldaemon/     ~man/           ~saned
~avahi-autoipd/ ~hplip          ~messagebus/

```
like so.

My question is how to I create/add a directory to this group?

---

### Post by ajmorris on 2009-04-22
hi there,
they are home directories. For example, if i type ```
~ajmorris
``` that is the same as typing ```
cd ~/
``` It is the same as ```
~dhcp
``` is the same as typing ```
cd /var/lib/dhcp
```
To create more of these shortcuts, you would have to create more user ids. As well as pressing ~<tab> to list them all, you can ```
cat /etc/passwd
``` to give a list of the users, and their home directories.

EDIT: oh, you could also add an alias. I.e if you're using bash, add an alias for ~<dir> to act as cd /<dir> to ~/.bashrc also, a simple bash script could probably be made to make <dir> a variable, and have any directory specified as <dir> work for ~<dir> if you so desired :)

AJ

---

### Post by sdennie on 2009-04-22
If I understand what you are trying to accomplish, you can also use $CDPATH.  For example:

```

export CDPATH=${HOME}/src

```

Now, if for example, you have a directory named ~/src/foo, no matter where you are, you can type:

```

cd foo

```

And it will change you to ~/src/foo.  Tab completion also works for the foo directory no matter where you are.

---

### Post by sloggerkhan on 2009-04-22
thanks for the responses, I think based on them I will be able to figure out what I needed.
thanks.

---

