---
title: "Create your own server question?"
date: 2008-04-02
forum: Full Circle Magazine
---

### Post by r0ut3r on 2008-04-02
I have been following the "Create your own server" "How To" and decided to attempt this myself.

I followed the instructions from Part 1 with no problems.  However, now I tried part 2 from issue 10 and it won't allow me to run any of the sudo commands.  It says my username isn't in the sudoers.  Looking back to Part 1 when I loaded the server version and created my username it says it doesn't have administrative rights.

How can I elevate my username to appropriate status or get my username into the admin group?

---

### Post by ronniet on 2008-04-05
> **r0ut3r said:**
> I have been following the "Create your own server" "How To" and decided to attempt this myself.

I followed the instructions from Part 1 with no problems.  However, now I tried part 2 from issue 10 and it won't allow me to run any of the sudo commands.  It says my username isn't in the sudoers.  Looking back to Part 1 when I loaded the server version and created my username it says it doesn't have administrative rights.

How can I elevate my username to appropriate status or get my username into the admin group?

From Daniel, writer of *Create Your Own Server*:

```

Press esc to access the grub boot menu.

Choose Recovery mode (should be the second option) and hit enter.

It will start up and you will have a command line which should show: root@ubuntu#

Type in: adduser "username" admin

```

**Hopefully that should sort your problem.**

---

