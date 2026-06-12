---
title: "What steps are required to program GUI in Ubuntu"
date: 2010-06-23
forum: Desktop Environments
---

### Post by wiseguy12851 on 2010-06-23
For many years I have programmed in all areas of Windows GUI with both the Windows API and MFC but I'm wanting to switch to ubuntu and have never programmed anything in linux before. Where would I find information for programming GUI for linux and what compilers should I use coming from a C++ background.

---

### Post by nikhilbhardwaj on 2010-06-24
qt is great if you already know c++

---

### Post by fepple on 2010-06-24
GCC/G++ is pretty much the standard compiler
For an IDE, check out Eclipse (CDT is the C/C++ versions name) - not sure how if its best for GUI programming though

---

### Post by wkulecz on 2010-06-24
I agree that QT is the way to go if you like C++, I'd also say its by far the best documented of the lot.  Take a look a QT Creator and its youTube tutorials.

I prefer C and thus have been suckered into GTK+/Glade/Gnome, but its not really C, its C++ re-invented poorly in C, and not documented worth a hoot.

---

### Post by KdotJ on 2010-06-24
There are so many GUI toolkits out there, especially for C++.
Like people have suggested, Qt Creator is great and also allows you for "drag and drop" creation of GUI if you want to get started straight away (though not the best way to learn in my opinion).


By the way, this thread may be moved to Programming Talk

---

### Post by wiseguy12851 on 2010-06-24
I'll look for these toolkits but I'm quite a bit more interested in the raw API that powers linux's graphical side, what includes and functions would I need to make a simple program using nothing but API calls or what references are out there that might explain this.

---

### Post by VH-BIL on 2010-06-24
I program C# using mono which is great for cross platform development.

If you want to just create a simple application you can bash script it and use zenity. For example my wireless modem is crappy and crashes and I have to reload the modem manager. I wanted a confirmation dialog in case of a accidental icon click and stop a download. Here is how I did it.
```
#!/bin/bash
zenity --question --title "modem-manager reloader." --text "Are you sure you want to reload the modem manager?"
if [ $? = 0 ]
then
  gksudo killall modem-manager
fi
```

---

### Post by wiseguy12851 on 2010-06-24
I'm not interested in making a simple application but an immensely complicated application with several thousand lines of code. I said simple application because you always start simple with a new API before you dive in. there's bound to be some reference to the Ubuntu API for GUI development else how do these toolkit wrappers know what API calls to make.

---

### Post by VH-BIL on 2010-06-24
Just look at the libraries supplied in Ubuntu. There is no Ubuntu API but many libraries that make up Ubuntu. What are you trying to program so I can help you get on the right track?

---

