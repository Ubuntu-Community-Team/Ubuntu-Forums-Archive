---
title: "$XDG_CACHE_HOME relocation of it to another directory"
date: 2010-11-17
forum: Desktop Environments
---

### Post by metallica1973 on 2010-11-17
I am working on a project to where I need to relocate the standard cache directory locations within Xubuntu. I read this article and It doesn't seem work for me

[http://blog.electronsmith.com/?p=191](http://blog.electronsmith.com/?p=191)

I add this entry to my /home/test/.pam_environment file without success.

[PHP]#!/bin/bash
$XDG_CACHE_HOME=/tmp/.cache[/PHP]

and I have also added this to my /etc/environment file as well without success.

[PHP]$XDG_CACHE_HOME=/tmp/.cache[/PHP]

and without quotes

[php]XDG_CACHE_HOME="/tmp/.cache"[/php]

no success!!

---

### Post by Brandon Williams on 2010-11-17
I haven't used .pam_environment and I don't recommend making changes to /etc/environment. Instead, for an individual user, you can set and export the value in ~/.xprofile. This file is sourced by /etc/gdm/Xsession when you log in. Here is what the file should look like to make sure the setting you want impacts all applications:
```
export XDG_CACHE_HOME=/tmp/.cache
```

---

### Post by metallica1973 on 2010-11-17
Oddly once I fireup Chromium it worked and stores it cached under 

[php]/tmp/various/.cache[/php]

but the minute I close it, it resorts back to the old directory.

[php]~/.cache/chromium[/php]

?????????????

I will try your suggestions. I will get back to you thanks

---

