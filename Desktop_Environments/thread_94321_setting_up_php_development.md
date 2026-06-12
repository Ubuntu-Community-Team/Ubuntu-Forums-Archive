---
title: "setting up php development"
date: 2005-11-23
forum: Desktop Environments
---

### Post by goneskiing on 2005-11-23
Is there a how-to on setting up php development in Breezy  - I've searched all over and not found anything.  I've installed php with it's apache dependencies.   My server only needs to be local to my machine.  thanks.

---

### Post by fimbulvetr on 2005-11-23
Ya gotta be a bit more specific, or you probably won't get an answer. I have php working on about 3 ubuntu servers and it works by default?

What steps have you taken? Have you made a php file and tested it?

---

### Post by goneskiing on 2005-11-23
I copied a select.php file in my /var/www folder.  Also in that folder is an Apache2-default folder with stuff in it.  I tried from my home directory using Firefox and going to [http://localhost/select.php](http://localhost/select.php) and I get the following:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/select.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

---

### Post by goneskiing on 2005-11-23
oh,  it looks like just a file permission error on my php file (file needs to be readable by others).

---

### Post by SuperMike on 2005-11-23
Okay, I'm like mega-stuck. I used to be on PHP4 and Apache (or was it Apache2?) with Hoary. I had the defaults. I upgrade to Breezy and then find that the web server isn't installed anymore and PHP4 won't work too.

I uninstall PHP4 from Synaptic and then reinstall it again. It says it's installed but then I couldn't run my PHP4 website like I used to. Instead, Firefox prompts me if I want to open the PHP file in gedit, which is like mega-stupid.

Okay, so I go back and try to unload PHP4 and upgrade to PHP5. That should surely work, right? Wrong. It fails. I get the same prompt again.

I just want to get to PHP4 and I need help. I've fallen and cannot get up. Please help. Anyone got that OnStar button they can push for me? I surely need it. And if I could go back to PHP4, that would be even better because many people are not yet on PHP5 yet, unfortunately. I want my source code to have the broadest appeal for now while I work on this project. Eventually, probably in late 2006 or 2007, I'll move to PHP5. I'm like REAL conservative on this issue.

Annoyed in the Desert

---

### Post by SuperMike on 2005-11-24
I figured out my problem. I needed to uninstall php5 and php4 and reinstall php4 a few times, then clear my browser cache, oddly enough, and then suddenly it worked. Don't know why.

Oh, and you can only get php4 now if you enable the universe option in /etc/apt/sources.list. And, as you know if you're really experienced with Ubuntu, keeping the universe option always uncommented is not a safe thing to do. You'll find that you'll be prompted to update your system if you keep universe enabled for very long, and when you update it, you end up in "beta land" with your PC -- quite disfunctional, perhaps. So, I only enabled the universe option temporarily, got php4 going again, did not update my system when the little red update icon appeared, and then commented out universe option. Then, I did apt-get update to ensure my system was set without the universe option for now. Now it is safe for my system to download updates because they will /not/ be coming from the universe land.

They /really/ appear to want you to upgrade to php5, but I'm not ready yet. I'm too conservative on this issue.

---

