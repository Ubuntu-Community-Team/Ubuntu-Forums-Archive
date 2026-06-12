---
title: "samba guest user unused"
date: 2009-01-01
forum: General Help
---

### Post by bartvh on 2009-01-01
I have made the following guest share on my home server:
```

[share]
	guest account = guest
	writeable = yes
	create mode = 775
	public = yes
	path = /home/share
	directory mode = 775

```

However, when I open this share on my windows PC, it still uses the user "nobody" instead of "guest", therefore requiring me to chmod /home/share to 777 to make it writable (which I don't want to do).
I have of course already restarted the daemon.

/home/share is owned by "root:people" and the user "guest" is in the group "people", along with the user accounts for real people in my family.

What is wrong?

---

