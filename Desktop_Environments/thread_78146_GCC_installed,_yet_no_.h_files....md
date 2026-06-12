---
title: "GCC installed, yet no .h files..."
date: 2005-10-17
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-17
Any idea?

I can't find any .h files on my PC so I can't even compile with GCC.

---

### Post by Stormy Eyes on 2005-10-17
Try **sudo apt-get install libc6-dev** for the GNU C Library's headers, or **sudo apt-get install libc6-dev-amd64** if you're using amd64. 

You may want to do **sudo apt-get install anjuta** for a C/C++ IDE that fits with GNOME.

---

### Post by az on 2005-10-17
You need to install the -dev packages you need.  Like xlibs-dev to compile stuff that require the x libraries, for example.

---

### Post by SeanCallan on 2005-10-17
Awesome thanks guys! I'm new to all this.

I get a 404 error when I try to get the libs so I'll try later I guess.

---

