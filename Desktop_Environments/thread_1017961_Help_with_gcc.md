---
title: "Help with gcc"
date: 2008-12-21
forum: Desktop Environments
---

### Post by ST1999 on 2008-12-21
I've been using gcc with Ubuntu without any problems for the last year.
This weekend I decided to install some of the libraries from boost and sgi. 
Long story short, I managed to thoroughly mangle the contents of /usr/include directory. In the process of trying to unmangle the directory, 
I managed to delete the stdio.h file. So now, nothing compiles and every little thing generates a gazillion errors.

I tried to get rid of gcc altogether and then do a reinstall. That didn't help as - I think - I didn't do a clean delete and therefore the corrupted state of my directories never got fixed during the reinstall. 

Not sure if any of the above is enough information for anyone willing to help. Can I download the stdio.h from somewhere? Or - and this would be my preference - how can I do a complete , clean, absolute resinstall of gcc and all the libraries? 

Any help will be much, much appreciated. 

- ST

---

### Post by snova on 2008-12-21
The GCC package only contains just that- GCC. No headers. That's part of libc. So try reinstalling the correct package:

```
sudo aptitude reinstall libc6-dev
```

This'll probably generate some errors/warnings if you moved files, since it won't be able to find them while uninstalling.

Don't mess with system files in the future. There's surely a better way... what were you trying to accomplish?

---

### Post by ST1999 on 2008-12-21
I was trying to install the files from Boost and SGI into my /usr/include directory. I made the mistake of de-compressing all the SGI files into /usr/include and found that a lot of the names - vector, list, etc. - are common to the defaults included by gcc. This started causing some problems with several existing c++ programs not compiling. So, I decided to remove al the SGI files, and while doing that ended up removing stdio.h. So obviously, I need to be careful where to place the Boost and SGI files.

This was all very frustrating and thanks to your help, things are all back to normal. Cheers

- ST

---

