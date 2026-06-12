---
title: "problem installing ruby-freedb; &quot;$ ruby extconf.rb&quot; fails"
date: 2006-02-13
forum: Desktop Environments
---

### Post by VCSkier on 2006-02-13
i'm very new to linux, and i'm wanting to install [this]("http://www.hydrogenaudio.org/forums/index.php?showtopic=38418") application, and it, according to the that thread, requires "ruby-freedb, ruby-libglade2, cdparanoia and cdda2wav installed as a minimum."  so i went to synaptic package manager, and found "libglade2-ruby," so i installed it and all of its dependencies.  i'm assuming that that is the same as "ruby-libglade2."  iirc, cdparanoia, and cdda2wav were already installed, if not, i installed them as well. 

so i googled for ruby-freedb, and found [this]("http://ruby-freedb.rubyforge.org/") site.  they offer a deb package, and a tar package.  the deb package said it was for i386 archetecture, but i'm running a 686 kernel, so i'm assuming that wasn't for me.  so i downloaded the tar package.  this is what i did: (as you can tell, the tar was in my home folder)```
reed@ubuntu:~$ ls
Desktop                     ruby-freedb-0.5.tar.gz
reed@ubuntu:~$ tar xfz ruby-freedb-0.5.tar.gz
reed@ubuntu:~$ cd ruby-freedb-0.5
reed@ubuntu:~/ruby-freedb-0.5$ ruby extconf.rb
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
       from extconf.rb:1
reed@ubuntu:~/ruby-freedb-0.5$
```let me know if any of you have any advice.

---

### Post by VCSkier on 2006-02-15
i dont mean to be rude, but i wanted to bump this.

---

### Post by pjstadig on 2006-02-16
I don't know if you've figured this out yet, but I have had the same problem while trying to install PostgreSQL and Oracle drivers. I finally gave up on the PostgreSQL driver and just installed the libpgsql-ruby package (which is much, much easier), but sometimes you want to install a ruby extension for which there is no Ubuntu package.

Anyway, here is the solution...

To get the 'mkmf' module you need to install the ruby1.8-dev package (or whatever version of ruby you are using). That should solve your problem. It solved mine, and now I have the Oracle driver installed on Ubuntu!!!

Paul

---

### Post by VCSkier on 2006-02-24
thanks for the advice.  i installed ruby1.8-dev, and it helped, but i'm still not out of the water.  the "$ ruby extconf.rb" step worked,  but now the "$ make" step isn't working.```
reed@ubuntu:~/ruby-freedb-0.5$ ruby extconf.rb
checking for OS... linux
creating Makefile
reed@ubuntu:~/ruby-freedb-0.5$ make
bash: make: command not found
reed@ubuntu:~/ruby-freedb-0.5$

```i dont know what to do now.

---

### Post by pjstadig on 2006-02-24
For that I believe you need the build-essential package:

```
sudo apt-get build-essential
```

HTH
Paul

---

### Post by VCSkier on 2006-02-26
it worked great.  thanks

---

### Post by marsanpin on 2006-04-17
Thank you for this post and respective solution.
Also had problems to "make" ruby-freedb and get goin' rubyripper working.
Let's see what happens next...

VCSkier,

If you could tell me how is it rubyripper ripping for you, I'll appreciate.

Have fun

---

