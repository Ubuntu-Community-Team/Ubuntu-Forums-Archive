---
title: "ruby: undefined symbol: usb_init"
date: 2009-06-24
forum: General Help
---

### Post by slawmac on 2009-06-24
Hi
I did some usb thermometer and I want connecting it with computer. So I followed the instruction on:  [http://www.a-k-r.org/ruby-usb/ ]("http://www.a-k-r.org/ruby-usb/")
I probably installed everything successfully. Unfortunately when I trying run my ruby script, console display such error:
[FONT=Courier New]$ ./temp_probe.rb
ruby: symbol lookup error: /usr/local/lib/site_ruby/1.8/x86_64-linux/usb.so: undefined symbol: usb_init :(

[/FONT]

---

### Post by Yellow Pasque on 2009-06-24
Did you use the software in the repository or did you install libusb and ruby from source?

My suggestion would be to use the versions provided by Ubuntu, e.g.:
```
sudo apt-get install libusb-dev ruby-dev
```

---

### Post by slawmac on 2009-06-24
Thanks, I did what You wrote - but error is still present.

---

### Post by Yellow Pasque on 2009-06-24
Try removing the stuff you installed in /usr/local
usb_init is defined in the libusb that comes with Ubuntu:
```
/lib$ strings libusb-0.1.so.4 | grep init
usb_init
...
```

---

### Post by Leslie Viljoen on 2009-06-24
Hi

Can you undo your installations? So if you tried to compile ruby-usb from source with "make install", try to remove it with "make uninstall".

The better way to install this would be to use apt and gems. Do:
1. sudo apt-get install libusb-dev
2. sudo gem install ruby-usb -r

Now, in your Ruby program you can:
1. require 'rubygems'
2. require 'usb'

..and you should be set.

You need to have installed rubygems already for all this to work. If you haven't done that, install it first by following instructions here: [http://rubygems.org/read/chapter/3](http://rubygems.org/read/chapter/3)

---

