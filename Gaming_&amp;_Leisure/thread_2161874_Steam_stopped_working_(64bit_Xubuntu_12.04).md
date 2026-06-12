---
title: "Steam stopped working (64bit Xubuntu 12.04)"
date: 2013-07-12
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-07-12
I haven't booted up in Steam in forever (but it did work previously) and today when I booted it up to see what linux games steam had on sale it wouldn't start. First a message popped up that said, "You are missing the following 32-bit libraries, and Steam may not run: libGL.so.1". I click ok to that error and then this pops up
[IMG]https://lh3.googleusercontent.com/-vtccoE1laoc/Ud_j_3ZMnBI/AAAAAAAAB50/q8-4T5TBFSI/s403/Screenshot%2520-%252007122013%2520-%252006%253A09%253A39%2520AM.png[/IMG]
So I went to synaptic to search for it and I found "libgl1-mesa-swx11" and in it's notes it mentions the following, "On Linux, this library is also known as libGL or libGL.so.1." When I clicked it for installation a box with a ton of stuff to remove showed up. I have attached a picture of what it's going to remove and I cancelled as I don't want to remove that stuff.
[IMG]https://lh3.googleusercontent.com/-TQh7a42CP0o/Ud_jHubZ9rI/AAAAAAAAB5Y/oyBWKn_DMTY/s720/Screenshot%2520-%252007122013%2520-%252006%253A01%253A13%2520AM.png[/IMG]

It turns out when I removed nvidia-current-updates driver and installed the nvidia binary from their website 319.32, something gets messed up BUT the solution that worked was to do the following
```
sudo nano /etc/ld.so.conf.d/steam.conf
```
within the file add these 2 lines
```
/usr/lib32
/usr/lib/i386-linux-gnu/mesa
```
then hit ctrl-x and then "Y" to save your changes to that file. THen issue
```
sudo ldconfig
```
and then start steam and you should be all fixed.

---

### Post by oldrocker99 on 2013-07-12
I haven't had this problem, but I'll bet somebody else does, or will, and you hvae provided the solution. Kudos!

---

