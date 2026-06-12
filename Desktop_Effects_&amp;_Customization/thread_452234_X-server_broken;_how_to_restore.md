---
title: "X-server broken; how to restore?"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by boon on 2007-05-23
ok i wanted to muck around with beryl - my mistake.

Now all I want to do is get my xserver back up and working.

I downloaded and installed the fglrx driver and then reconfigured xserver to run it.

Now its broken and i dont know what to do.

How do I get back to a standard xorg xserver set up?

---

### Post by Ub1476 on 2007-05-23
```
sudo dpkg-reconfigure xserver-xorg
```

Will resotre your X. Applying all default should work, so no need to worry about the questions, but if you know them, answer them correctly of course..:)

---

### Post by boon on 2007-05-23
thanks ub, that command is handy.

Also in the process before it created a backup version of xorg.conf file. So all i had to do was delete the new file and rename the backup file xorg.conf

Problem solved!

I think I'll let beryl rest for a little bit. And also stop entering commands into the terminal when i dont know what im doing :)

---

