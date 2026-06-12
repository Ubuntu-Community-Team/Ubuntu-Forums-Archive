---
title: "[SOLVED] wesnoth-1.3.19 won't compile"
date: 2008-03-08
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-03-08
Hi! I posted this in the other thread, but since that one is already flagged as solved, I decided to make a new thread for this problem:

I'm having trouble compiling. ./configure won't run. I followed the guide. It keeps saying that I don't have libsdl-image installed, but according to synaptic i have both the normal and the -dev package. I even compiled the library from source from libsdl.org to make sure I had it, but ./configure still says I don't

Help!

---

### Post by eragon100 on 2008-03-08
Anyone any ideas?

I would like to know where wesnoth lookes for the library, so that i can compile the library again with the path to the location where wesnoth expects to see it added with the PREFIX option for ./configure.

---

### Post by Perfect Storm on 2008-03-08
Try with ./configure --prefix=/usr

---

### Post by eragon100 on 2008-03-08
In case it's useful, some info from the config.log which i geuss might be related to the problem:

configure:10890: result: /usr/bin/libtool
configure:10930: checking for IMG_Load in -lSDL_image
configure:10965:  gcc -o conftest -g -O2    conftest.c -lSDL_image   -lX11  -L/usr/lib -lSDL >&5
/usr/lib/libSDL_image.so: undefined reference to `png_destroy_read_struct@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_read_update_info@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_create_info_struct@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_valid@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_read_image@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_io_ptr@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_packing@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_strip_16@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_gray_to_rgb@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_read_info@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_tRNS@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_read_fn@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_sig_cmp@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_get_IHDR@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_set_expand@PNG12_0'
/usr/lib/libSDL_image.so: undefined reference to `png_create_read_struct@PNG12_0'
collect2: ld returned 1 exit status
configure:10971: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Battle for Wesnoth"

:confused::confused::confused::confused::confused::confused:

---

### Post by Perfect Storm on 2008-03-08
Try reinstall sdl image + dev (ubuntu version) and thereafter give the output of ./configure and eventual make of wesnoth.

---

### Post by eragon100 on 2008-03-08
@ A.I.: Thanx for the suggestion, but I'm afraid it still won't work :(

---

### Post by eragon100 on 2008-03-08
I only just noticed your second suggestion, but it still won't work

Output is exactly the same :confused:

---

### Post by eragon100 on 2008-03-08
I think I hava a better idea: the battle for wesnoth doesn't require 3d video card.

Virtualbox doesn't support "true" fullscreen, do you know of any virtual machine programs that do? :guitar:

---

### Post by Perfect Storm on 2008-03-08
Why don't you use the stable version of wesnoth instead? 1.3.19 is the unstable version which can course problems/bugs etc.

[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)

---

### Post by eragon100 on 2008-03-08
I am already using it, but they recommend the unstable version. It's probably the last release candidate, big chance next version will be final 1.4. I won't to install it when it comes out, so I can continue to play online. Plus, 1.3.19 has lots of improvements, such as better graphics. Do you know of any virtual machine tingy?

---

### Post by Perfect Storm on 2008-03-08
No sorry.

---

### Post by eragon100 on 2008-03-08
Alright, I will simply use virtualbox in a window and set the resolution of my entire desktop to 1024x768 while playing wesnoth then. Same effect as fulscreen :lolflag:

I'm going to check if it compiles in virtual machine :)

---

### Post by eragon100 on 2008-03-08
I was right about 1.4! It has just been officially released!!!

---

### Post by eragon100 on 2008-03-08
Easiest solutions are best: I had forgotten that the windows version runs absolutely perfect in wine ! :lolflag: There is no need to compile it :lolflag:

Thread solved!

---

