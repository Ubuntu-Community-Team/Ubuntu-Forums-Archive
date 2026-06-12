---
title: "OSSIM(Open Source Software Image Map) install"
date: 2008-02-21
forum: Education &amp; Science
---

### Post by mitch_77 on 2008-02-21
Hi everyone,

is there anybody who can tell me how to install this Remote Sensing sw [HTML]http://www.ossim.org/OSSIM/OSSIMHome.html[/HTML] ?
Any link with some tutorial..stuff like that. I think I can't install it from the Add/Remove sw, can I?
Thanks for your help.

Cheers,
mitch.

---

### Post by thisismalhotra on 2008-02-21
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Download the source through subversion, and use the tar.bz tutorial in the link above.. that should do it post bck if u face issues

---

### Post by mitch_77 on 2008-02-22
Thanks man, I appreciated that but it's still not so clear.:(

I downloaded the sw and the dependencies.
I decompressed them on my desktop and then I started doing what the tutorial was saying but I got this:

mitch@mitch-desktop:~$ cd /home/mitch/Desktop/ossim
mitch@mitch-desktop:~/Desktop/ossim$ ./configure
bash: ./configure: No such file or directory
mitch@mitch-desktop:~/Desktop/ossim$ make
make: *** No targets specified and no makefile found.  Stop.
mitch@mitch-desktop:~/Desktop/ossim$ 

 I've been trying all the possible variations but without success.

What did I wrong?

cheers,
mitch

---

### Post by FiReSTaRT on 2008-10-11
It looks like the configure file isn't executable. I'm a relative newb, especially when it comes to compiling and using the shell, but I'll see if I can figure it out and give it a go. I'm actually looking for an alternative to ER Mapper that will run on Linux.

---

### Post by FiReSTaRT on 2008-10-11
Progress report..
For starters, you'll need to make the configure file executable by using the command > sudo chmod +x configure
I also had to satisfy the following dependencies before I could successfuly configure it.
tiff
geotiff
openthreads

Edit: While I did get it to install, I'm not sure what to do next.. Ended up removing it until I can get a better idea of how to install the GUI and the additional libraries. This is a complex package and would involve a lot of documentation for it to be removed later on down the line. That's why I uninstalled it for now.

---

### Post by maphew on 2008-10-12
> **FiReSTaRT said:**
> ... I'm actually looking for an alternative to ER Mapper that will run on Linux.

Depending on what ermapper-type functionality you are looking to use, SAGA GIS might work for you: [http://saga-gis.wiki.sourceforge.net/](http://saga-gis.wiki.sourceforge.net/)
Of the open source GIS/RS software I've looked it it probably has the most well developed raster processing toolkit. Expect to spend some time learning to use it as it has it's own unique approach and the documentation is spotty (again, that depends what you want to do).

There are some recent .deb packages talked about here:
[http://sourceforge.net/forum/forum.php?thread_id=2223819&forum_id=790705](http://sourceforge.net/forum/forum.php?thread_id=2223819&forum_id=790705)

Note: I've not used saga for awhile and never on linux (I don't do much raster processing outside of format conversion and gdal works just fine for that). It's just a project I like to keep an eye on.

cheers,

---

### Post by FiReSTaRT on 2008-10-13
Thanks for the link. I already installed it and will play with it tomorrow. I hope it can handle vector overlays as well, such as a map layer. 
OSSIM didn't work well for me. I booted into Vi**a and installed the W*n binary to give it a shot. It took forever to install and ran very slowly. Considering that I'm running on a dv9000 that's only a couple of months old, that should not have been an issue. That's why I'll hold off on installing it on Linux.

---

### Post by TATEVARI on 2009-05-02
Hi,

I'm trying to install OSSIM (Open Source Software Image Map) in Ubuntu 9.04 but I think it's above my skills (for now :twisted:) so I was wondering if you could help me. 
In previous posts [thisismalhotra]("http://ubuntuforums.org/member.php?u=388944") gave what seemed to be a useful link but it's not working anymore and as far as I know there are no how to's or tutorial's whatsoever.

Pleeeeeeeeeeeease help me [-o<. I've been struggling with this for weeks and at this point I'm about to quit ](*,). It's just that I want to check this software so badly... plus I need it for research.
By the way, I've tried this link already [http://trac.osgeo.org/ossim/wiki/Ubuntu-8.10Build](http://trac.osgeo.org/ossim/wiki/Ubuntu-8.10Build)
won't work...

Thank you.

---

### Post by arma0012 on 2010-03-01
I too would like to know how to get ossim working. I'm on 9.10 and would like to know if anyone has been able to get it running. I checked out SAGA, but it doesn't do photogrammetry, which is what I really need.

Cheers,
Sam

---

### Post by johanvdw on 2010-05-18
In case somebody is still looking for ossim:
[https://launchpad.net/~ubuntugis](https://launchpad.net/~ubuntugis)
provides a ppa which contains ossim

---

