---
title: "How to show opened ports on my desktop (widgets)"
date: 2009-09-18
forum: Desktop Environments
---

### Post by sowhat123456789a on 2009-09-18
I look for kde-look.org but I could not find anythink about it. I want to see on my KDE (4.x) desktop the ports which are opened. If there is no a widget I can do it with conky or screenlets ?
There is any widget like "active ports" software on windows? Can you help me?

Thank you!

---

### Post by krazyd on 2009-09-18
do you mean network ports? some display like this command?
```
lsof -i
```

I don't know of any widgets that can do this specifically, but the STDIN plasma widget can display the output of any terminal command. So it can show the output of the above command. See here:
[http://www.kde-look.org/content/show.php/STDIN%20Plasmoid?content=92309](http://www.kde-look.org/content/show.php/STDIN%20Plasmoid?content=92309)

---

### Post by sowhat123456789a on 2009-09-19
netstat -tapn and sudo lsof -i  is nice idea but they stop after 10 seconds from terminal. I want to see them always updated.

---

### Post by krazyd on 2009-09-19
> **sowhat123456789a said:**
> netstat -tapn and sudo lsof -i  is nice idea but they stop after 10 seconds from terminal. I want to see them always updated.

Have you actually tried that plasma widget I suggested?

you can set it to update as often as you want. I set the timer for 10 seconds and use this command:
```
kdesudo -i question -c "lsof -i"
```

---

### Post by sowhat123456789a on 2009-09-19
I had not saw your meesage sorry...

I try to install STDIN plasma widget but I could not :( First i gave these commands :
mkdir build
cd build
and than :
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
but this give me an error :
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/user/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:1 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!



Also when I write your second commnand on terminal, it gives me the results after 10 seconds and than stops (as always).

---

### Post by krazyd on 2009-09-19
you need to install a compiler ```
sudo apt-get install build-essential
```
i think there are also kde-specific dev packages required. cmake will notify you of this if you try running it again after installing build-essential. I've attached a deb package I built from svn a few months ago, which you could use instead of compiling your own. It's a 32-bit checkinstall build, so won't work if you're running 64-bit.

---

### Post by sowhat123456789a on 2009-09-20
I install both of them but till the same problem.

---

### Post by krazyd on 2009-09-20
what's the error message?

---

### Post by sowhat123456789a on 2009-09-20
The same problem

---

