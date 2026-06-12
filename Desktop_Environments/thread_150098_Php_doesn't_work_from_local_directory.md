---
title: "Php doesn't work from local directory"
date: 2006-03-25
forum: Desktop Environments
---

### Post by lrmall01 on 2006-03-25
I've installed php and made sure that it works from the /var/www directory.  Then I set up a local directory to work on it from my /home folder, doing what is suggested in the wiki.

It works for html files - I can view them with [http://localhost/lrmall01](http://localhost/lrmall01)

However, if I try to view php files this way, I get an error.  For example, [http://localhost/lrmall01/testphp.php](http://localhost/lrmall01/testphp.php) gives me:

[FONT="Courier New"]Warning: Unknown(/home/lrmall01/www/testphp.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)() [function.include]: Failed opening '/home/lrmall01/www/testphp.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/FONT]

But it works fine if I have the same file in /var/www

Any suggestions?

****
Oops, it looks like I may have done something to break the install.  Still trying to figure out what went wrong - I don't think it works from the /var/www directory anymore.
****

****
**Geez I'm a moron.  Looks like I had a copy and paste screwup that php didn't like.  Must of had an extra space or something in there that screwed up the PHP processing.  Nevermind.**
****

---

### Post by hegex on 2006-04-11
Hi buddy, i think you have similar problem than i had. And solution is simple, give a permissions to your test.php that apache/php can read it. so u should chmod it to something like 604.. or just simble right-click your php file change permissions there [http://thunar.xfce.org/wiki/media/ui/nautilus/20050209-file_properties_permissions.png]("http://thunar.xfce.org/wiki/media/ui/nautilus/20050209-file_properties_permissions.png")

---

