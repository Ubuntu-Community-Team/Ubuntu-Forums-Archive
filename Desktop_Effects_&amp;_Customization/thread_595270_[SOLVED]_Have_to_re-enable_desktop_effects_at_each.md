---
title: "[SOLVED] Have to re-enable desktop effects at each login"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by sphoid on 2007-10-28
I've been running gutsy for about a week now with no problems with full compiz goodness on my geforce 6800. I had a wierd glitch last night that force me to do a hard reboot. Now every time I log in my desktop effects are turned off and I have to re-enable them. Once I turn them on, they work fine, but sure enough next time i log out and back in, they are turned off again.

I tested this on the other account on the system and same thing. I reboot and same thing. Nothing i do is making gnome remember it has to turn on those effects. I suspect a corrupted config file somewhere but I see no errors/logfiles that would indicate this.

This is very agitating.

---

### Post by Forlong on 2007-10-28
Open ```
gedit ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```
And make sure it looks like this:
```
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1193611047" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
        <entry name="default" mtime="1193524703" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
</gconf>
```

---

### Post by sphoid on 2007-10-28
Aside from the mtime, everything is identical. Any other ideas?

---

### Post by erginemr on 2007-10-28
Chances are that that the above file's permissions has been screwed somehow. Please check:
ls -l ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
to see you have read/write permissions on it.

---

### Post by sphoid on 2007-10-29
Checked my permissions, and as expected I am the owner and I have full rights over it. Still looking for a solution, uber kudos to anyone who can figure this out.

---

### Post by sphoid on 2007-10-29
I resolved this. I had an entry in my session startup stuff that was executing "compiz --replace&" at the start of my gnome session. I disabled this entry and now it seems to work. What's strange is that this hasn't been a problem until yesterday.... who knows, maybe a race condition was occuring or something. Thanks for the suggestions

---

### Post by erginemr on 2007-10-29
Glad that you have found the solution. I would suggest making the thread as SOLVED.

Happy 'bunting...

---

