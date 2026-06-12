---
title: "ImageMagick and Jaunty 9.04"
date: 2009-06-14
forum: General Help
---

### Post by manekineko2 on 2009-06-14
I had a Ruby on Rails site that used ImageMagick working under 8.04.  Upgraded to Jaunty, and it stopped working, now it complains when I try to serve up a page that:
libWand.so.10: cannot open shared object file: No such file or directory - /usr/lib/ruby/gems/1.8/gems/rmagick-2.9.2/lib/RMagick2.so

I go to /usr/lib/ruby/gems/1.8/gems/rmagick-2.9.2/lib/ and do an ls -l:
-rwxr-xr-x 1 root root 388801 2009-05-21 16:17 RMagick2.so
-rw-r--r-- 1 root root  61322 2009-06-14 14:38 RMagick.rb
drwxr-xr-x 2 root root   4096 2009-06-14 14:38 rvg

There it is, right there, not being found.

I run RMagick directly using ruby RMagick.rb, and it errors out:
./RMagick2.so: libWand.so.10: cannot open shared object file: No such file or directory - ./RMagick2.so (LoadError)
	from RMagick.rb:11

Anyone have any idea what's going on?  The file is sitting right there, but for whatever reason, it can't be read by Ruby.

---

### Post by manekineko2 on 2009-06-14
Update, I've discovered that the error message actually is indicating libWand.so.10 is missing, not RMagick2.so.  Unfortunately, still can't figure out where to get libWand.so.10 from, it doesn't seem to be in any of the relevant packages.

---

### Post by manekineko2 on 2009-06-14
FYI, solved it by adding a symbolic link from libMagickWand.so.1.0.0 to libWand.so.10 using this command:
sudo ln -s libMagickWand.so.1.0.0 libWand.so.10

---

