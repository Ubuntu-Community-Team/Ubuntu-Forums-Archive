---
title: "Webilder is AWSOME but since jaunty :(("
date: 2009-04-30
forum: General Help
---

### Post by Elcid247 on 2009-04-30
im using the awsome reaaaaaaaaallllyyy awsome webilder on ubuntu and just cant stop lovin it.

[http://www.webilder.org/](http://www.webilder.org/)

unfortunately with the 9.04 release, im having several bugs with it.

1. i cant open any dialog box from the window itself, all the menu commands fail.

2. i can only open preferences by right clicking the icon on the pannel.

3. i cant set the preferences since neither the ok nor the cancel button work.

4. when i try to add channels, it hangs and i have to kill it.

any1 with any workarrounds? really i just love the new release, but this bug is killin me :(

---

### Post by Elcid247 on 2009-04-30
```
webilder.installation_date = time.struct_time(tm_year=2009, tm_mon=5, tm_mday=1, tm_hour=2, tm_min=4, tm_sec=6, tm_wday=4, tm_yday=121, tm_isdst=1)
```

can any1 tell me, how does this line look in their config file? cause this is whts causing the problem, when i omit it, everything runs properly, i found this when i ran webilder from the terminal

```
Traceback (most recent call last):
  File "/usr/bin/webilder_desktop", line 2, in <module>
    from webilder.WebilderDesktop import main
  File "/var/lib/python-support/python2.6/webilder/WebilderDesktop.py", line 16, in <module>
    from config import config, set_wallpaper, reload_config
  File "/var/lib/python-support/python2.6/webilder/config.py", line 96, in <module>
    config = ConfigObject(DEFAULT_CONFIG_FILE)
  File "/var/lib/python-support/python2.6/webilder/config.py", line 9, in __init__
    self.load_config(file)
  File "/var/lib/python-support/python2.6/webilder/config.py", line 43, in load_config
    raise ValueError('Error parsing line %d of config file %s' % (lineno, file))
ValueError: Error parsing line 20 of config file /home/user/.webilder/webilder.conf
```

it seems that webilder screws up the storing of the struct :S

i just cant seem to understand y this is happening only in jaunty, and was fine in hardy :S

---

### Post by bhupsi on 2009-05-02
I just recently installed webilder under jaunty on my desktop and all is working well.  I installed webilder on my laptop and was getting the same errors as you are.  I compared line 20 of my .webilder/webilder.conf file on both my desktop and laptop and I found them to be different.  I changed line 20 on my laptop to match what it is on my desktop and now all is working.  Here is what my working configs line 20 looks like:

webilder.installation_date = (2008, 10, 26, 12, 25, 1, 6, 300, 1)

---

### Post by Elcid247 on 2009-05-05
thanks alot man, this solved it

---

### Post by beameup on 2010-01-31
I think the 0.6.5 update fixed that. No deb file to be found, I had to manually install it. Great app.

---

