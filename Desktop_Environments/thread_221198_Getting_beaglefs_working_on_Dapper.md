---
title: "Getting beaglefs working on Dapper"
date: 2006-07-22
forum: Desktop Environments
---

### Post by gpierce on 2006-07-22
Hello, 

I have read about beaglefs, a new FUSE application that can create folders containing links to searches. I am having a great deal of trouble getting this to work. I have downloaded the source and during compilation I get a number of errors with the end result being failure to compile. 

The most glaring error appears to be failure to find libbeagle, even though I have beagle up and running and working well. This is the first error I get when I try to compile:

Package libbeagle-0.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libbeagle-0.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libbeagle-0.0' found
Package libbeagle-0.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libbeagle-0.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libbeagle-0.0' found

I have no idea where the PKG_CONFIG_PATH variable is so I could add libbeagle's directory. Any assistance would be appreciated.

Thanks,
Greg

---

### Post by mattman on 2006-07-22
Make sure that you have beagle-dev installed. That will provide /usr/lib/pkgconfig/libbeagle-0.0.pc :)

---

### Post by gpierce on 2006-07-23
It's definitely installed, but still the same error message.

---

