---
title: "Unable to run package manager or apply updates"
date: 2006-08-20
forum: Desktop Environments
---

### Post by airjrdn on 2006-08-20
As a note, I recently got XGL working and had to add some additional repositories for that to happen.  I'd guess that it's related to these issues, but I'm not sure what to do to fix them.

If I try to run the synaptic package manager, nothing happens.  I never even get prompted for the password.

Two updates show as available; compiz and compiz-gnome.  If I try to apply the updates, I get:  "The list of changes is not available yet. Please try again later." and that's as far as it goes.  I first got this message this morning, and waited until this evening to see if it truly just needed more time for things to be updated, but at this point I suspect that's not the case.

---

### Post by Fass on 2006-08-20
Could it be [related to this?](http://www.ubuntuforums.org/showthread.php?t=239238)

---

### Post by airjrdn on 2006-08-20
I don't know.  I saw that thread, but I didn't use Quinn's info, I used someone else's.

---

### Post by xinix on 2006-08-20
What happens when you run synaptic in the terminal?  Who's packages are you using?

---

### Post by airjrdn on 2006-08-21
I don't know how to run it from the terminal.  As for the packages, what's the path/filename their stored in?

---

### Post by xtknight on 2006-08-21
> **airjrdn said:**
> I don't know how to run it from the terminal.  As for the packages, what's the path/filename their stored in?

Open the terminal and type **synaptic**.  Packages install lots of files in lots of different places.

---

### Post by airjrdn on 2006-08-21
Sorry, I meant the repository listing...isn't that in /etc/...?

As for synaptic, I get:
error while loading shared libraries:  libvte.so/4:  cannot open shared object file:  No such file or directory."

---

### Post by xinix on 2006-08-21
for now the solution is to downgrade and wait for a fixed update to come out.

This should work:
```
sudo apt-get install --reinstall libvte4/dapper libvte-common/dapper
```

---

### Post by xtknight on 2006-08-21
> **airjrdn said:**
> Sorry, I meant the repository listing...isn't that in /etc/...?

Repository list is in /etc/apt/sources.list which requires root privileges (sudo) to edit.  After you change it you must do **sudo apt-get update**.

---

### Post by airjrdn on 2006-08-22
That problem now seems fixed, but when I try to open a Terminal window from the Accessories menu, I get:

"Could not launch menu item

Details:  Failed to execute child process:  "gnome-terminal" (No such file or directory)"

---

### Post by airjrdn on 2006-08-22
anyone?

---

