---
title: "Tremulous GPP"
date: 2011-06-12
forum: Gaming &amp; Leisure
---

### Post by CreativeReach on 2011-06-12
Hi, Does anyone have a PPA or something for the Tremulous Game Play Preview?

I have had nothing but trouble trying to install it. This is the one thing I need, so that I wont need Windows.

THX

---

### Post by CreativeReach on 2011-06-12
Bump

---

### Post by CreativeReach on 2011-06-13
Bump

---

### Post by Perfect Storm on 2011-06-13
I haven't seen one.
But there's an installation script on their site.

```
chmod +x tremulous-gpp1-installer.x86.run
sudo sh tremulous-gpp1-installer.x86.run
```
Then exit the installer (important).

Should do it.

---

### Post by CreativeReach on 2011-06-13
THX! I'll try that after school!

---

### Post by CreativeReach on 2011-06-13
I got this error
```
 tremulous-gpp1-installer.run: 1: Syntax error: word unexpected (expecting ")")
```

---

### Post by CreativeReach on 2011-06-13
Bump

---

### Post by Perfect Storm on 2011-06-14
Please don't bump a thread within 24 hours, it's only allowed after 24 hours.


Try this instead:
```
chmod 755 tremulous-gpp1-installer.x86.run
./tremulous-gpp1-installer.x86.run
```

install it locally.

---

### Post by CreativeReach on 2011-06-14
Thanks! Its installed! But how do I make icons in the menu? Do I use the Main menu tool?
If so what would the command look like?

---

### Post by Perfect Storm on 2011-06-14
The command would be properly something like this:

```
sh -c "<path> && ./<binary>"
```

---

### Post by CreativeReach on 2011-06-14
I have it install as /home/Creativereach/.tremulous/tremulous-gpp.x86

what would that look like?

---

### Post by Perfect Storm on 2011-06-14
```
sh -c "cd ~/.tremulous && ./tremulous-gpp.x86"
```

---

### Post by CreativeReach on 2011-06-14
Thanks A ton!

---

