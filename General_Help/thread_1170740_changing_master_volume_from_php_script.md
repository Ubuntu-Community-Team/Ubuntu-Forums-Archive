---
title: "changing master volume from php script"
date: 2009-05-26
forum: General Help
---

### Post by camupod on 2009-05-26
I am trying to write a php script that will change the volume on my Ubuntu server so I can do this from a web page, but I'm getting an error when Apache tries to run amixer.

[php]
<?php
exec("amixer sset Master playback 20%");
?>
[/php]In apache's error.log file I get this:

amixer: Mixer attach default error: No such file or directory

Of course when I run the exact same command in a terminal, it works fine. I am guessing it has something to do with Apache's permissions or something, but I don't know that much about user permissions.

---

