---
title: "Override sudo for my www dir?"
date: 2009-01-05
forum: General Help
---

### Post by boozker on 2009-01-05
I've always been working on Mac OS X with MAMP for working locally and it works great. Now I want to work on my Linux box but...

I installed PHP5, Apache, PHPMyAdmin, and a bunch of other server stuff and it's running fine in my /www directory, my problem however is it's way too annoying and counter productive to have to do sudo gedit etc every time I want to edit a file. I don't want to login as root either for obvious reasons.

Is there a way to point apache in linux to a different directory or just change the permissions to the www directory?

---

### Post by reality1011 on 2009-01-05
sudo chown -R <username> /var/www

---

### Post by boozker on 2009-01-05
duh, :oops: thanks!

I tried doing it with FileZilla and right clicking totally forgot that i could force the change with Terminal...

---

