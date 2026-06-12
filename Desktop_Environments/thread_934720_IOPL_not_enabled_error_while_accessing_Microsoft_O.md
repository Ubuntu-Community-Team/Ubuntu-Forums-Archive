---
title: "IOPL not enabled error while accessing Microsoft Office through wine"
date: 2008-09-30
forum: Desktop Environments
---

### Post by maruthi_s@infosys.com on 2008-09-30
[COLOR="Blue"]
Hi 

When I try accessing the MS Office applications through wine, I am getting the following error (IOPL not enabled), Pasted the screen shot for your reference. 

[IMG]http://farm4.static.flickr.com/3221/2902888161_17fbefc076.jpg?v=0[/IMG]

Any pointers on the same 

Thanks in Advance
[/COLOR]

---

### Post by maruthi_s@infosys.com on 2008-10-02
[COLOR="Blue"]
Hi All,

Kindly let me know is there any way to resolve this issue. 

Thanks in advance
[/COLOR]

---

### Post by RikoW on 2008-10-02
Hi,

try this:

start winecfg from the command line. Move to the Library tab and set an overwrite for gdiplus to (native, builtin).

I had the same problem when installing Visio in Wine/cxoffice. That fixed it.

Cheers,

             Riko

---

### Post by maruthi_s@infosys.com on 2008-10-02
[COLOR="Blue"]
Hi Rickow,

Thanks for the input. Still I am facing the same issue. 

I am not sure how to resolve this :(


[/COLOR]

---

### Post by fr33div3r on 2010-06-27
Hi,

Try the same as RikoW recommended, but set “Native (Windows)” for *gdiplus. *It worked for me.

Cheers,

fr33div3r

---

### Post by colo505 on 2010-10-25
I have both Crossover as also Wine installed, and while I run Office Crossover, I run uTorrent with Wine.

Can you suggest what settings I should use for both, as winecfg files are different for both apps.

Thanks

---

