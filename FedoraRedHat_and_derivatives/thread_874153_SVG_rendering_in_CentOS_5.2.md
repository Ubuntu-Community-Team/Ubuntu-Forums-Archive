---
title: "SVG rendering in CentOS 5.2"
date: 2008-07-29
forum: Fedora/RedHat and derivatives
---

### Post by cudjoe on 2008-07-29
Hi,

I posted on CentOS forums already, but wanted your opinion. I am investigating which library could be misbehaving.


I generated some SVGs using matplotlib on CentOS 5.2. 

They are rendered correctly with Inkscape (and almost well in Firefox), but are somehow cropped with Eye-of-Gnome(2.16) and display (image-magick).

I did some screenshots here (with original SVGs) : 
[http://cudjoe.org/media/centos-cairo](http://cudjoe.org/media/centos-cairo)

While I was trying to figure out where the problem could come from, I realized that :

- the small tool svg2pdf (from Carl Worth) compiles but does not work (git://people.freedesktop.org/~cworth/svg2pdf). It creates empty files. It only relies on librsvg2 and cairo...

- its svg2png works well though (git://people.freedesktop.org/~cworth/svg2png)

- the previous charts are rendered correctly with svg2png

Could it come from some underlying Cairo or librsvg libraries ? 

Thanks for your support !

---

