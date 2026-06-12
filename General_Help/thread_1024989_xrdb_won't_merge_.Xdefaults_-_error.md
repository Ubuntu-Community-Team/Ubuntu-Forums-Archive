---
title: "xrdb won't merge .Xdefaults - error"
date: 2008-12-29
forum: General Help
---

### Post by Bubnoff on 2008-12-29
*****Updated - Resolved *************
# I am a horrendous idiot. .Xdefaults was invalid due to my commenting with '#'.
# You can't comment this file the way you may have grown to expect with bash ...apparently.
# Word to the wise - don't comment this file, unless, of course, you've
# discovered the secret commenting rules.
#
# Thanks to all who participated in the original post below.

I am having the same problem as the fellow in the following post:

[http://ubuntuforums.org/showthread.php?t=702664](http://ubuntuforums.org/showthread.php?t=702664)

Whereas the original poster appears to have gained satisfaction and
xterm bliss, I get the following error:
[HTML]
automation@Sherman:~$ xrdb -merge .Xdefaults 
<stdin>:1:3: error: invalid preprocessing directive #File
[/HTML]

Any advice would be appreciated. Running 8.04.

thanks -

bubnoff

---

### Post by kiwibird on 2011-12-22
It's X commenting rules, use ! to start a comment instead of #

---

### Post by Bubnoff on 2011-12-22
Thanks! Good to know. I'll give that a shot.

Bubnoff

---

