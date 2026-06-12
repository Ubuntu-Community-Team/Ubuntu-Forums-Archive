---
title: "Before update: fix KDE menu"
date: 2005-10-13
forum: Desktop Environments
---

### Post by pepster on 2005-10-13
I would like to update to breezy, but before that I would like to fix my KDE menu, which is broken for some time.

It is impossible to make any changes to the menu. I left click, run Menu Editor, do a Save, and my menus stay the same.

Any ideas??

Thanks

---

### Post by CiberAmigo on 2005-10-13
Had the same problem some time ago. think I used the Konsole --> sudo kmeuedit

Not sure, but hope it helps. Otherwise You should be able too find some about it in the 5.04 forum.

CiberAmigo

---

### Post by Rory on 2005-10-13
I think the answer may be in erasing the kde menu hidden folder in your /home directory and then restarting.  This resets it to the default.  If you google, you may be able to find which directory it is.  Sorry, but I don't remember.

Let me know if it works.

R.

---

### Post by pepster on 2005-10-13
Nothing obvious helps. I looked at the kubuntu bagzilla and found a report of the problem. They have an ugly workaround which requires running 'sudo kbuildsycoca' to get the updated ufter any change.

I won't even start on commenting the need for su privilge to change a user preference ....

-Joseph

---

### Post by asimon on 2005-10-14
[QUOTE=Rory]I think the answer may be in erasing the kde menu hidden folder in your /home directory and then restarting.  This resets it to the default.  If you google, you may be able to find which directory it is.  Sorry, but I don't remember.
[/QUOTE]
I think that's $HOME/.local

---

### Post by devnulljp on 2006-04-20
I agree the kbuildsycoca thing is non-obvious, and the need for sudo privs is a pain, but it works.

[B]kmenuedit -> make changes->Save
sudo kbuildsycoca[/B]

---

### Post by fdoving on 2006-04-20
I have not tried, but I think running kbuildsycoca without sudo would work too.

- Frode

---

### Post by GeneralZod on 2006-04-20
[QUOTE=fdoving]I have not tried, but I think running kbuildsycoca without sudo would work too.

- Frode[/QUOTE]

Yes, it's definitely worth trying - I can't imagine for a second why sudo would be required.

---

