---
title: "Switch off Desktop Effects at command line"
date: 2008-12-11
forum: General Help
---

### Post by za.zen on 2008-12-11
I have Kubuntu 8.10 installed, and since I have an ATI card, I can't use desktop effects and watch movies at the same time.  Since there's no solution for this problem yet, the common thing to do is disable the effects when wanting to watch a movie.  

I'm OK with that.  What I want to know is, is there any way to do this with a command line?  My idea is to create a simple little shell script and make a shortcut to it in my panel bar.  So when I want to disable the effects, I just click a panel button.  To enable them again, click the button again. 

So I guess what I want to know is this:

1.  Can such a thing be done? 

2.  How do I test, from command line, whether or not the desktop effects are enabled?

3.  How do I enable/disable those effects from command line?

4.  Would my idea of a shortcut work for this function?  

I know I could just go to the K menu, then Computer, then System Settings, then Desktop......but it seems like a lot of work just to watch a movie.  I thought a button would be easier, but can't find anything for it on the forums or on the web. 

Any help would be awesome.  :)  Maybe more people could use this little work-around until Compiz and ATI get their stuff together, eh?  :)

---

### Post by Therion on 2008-12-11
You mean like the [Compiz Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)?

---

### Post by philinux on 2008-12-11
Install the fusion-icon

sudo apt-get install fusion-icon.

Menu item appears in system tools>in gnome. When you run it it appears in the notification area. Really useful. You could start it from sessions to make it load at login.

---

### Post by HavocXphere on 2008-12-11
Yes. In fact its not about "can it be done"...it is very likely that you *will* have to do that if you run into problems.

> /home/ms/.kde/share/config/kwinrc
Note the .kde->It's a hidden directory...so it won't show with ls

> [Compositing]
Backend=OpenGL
**Enabled=true**
Thats what you need to change. Some people just delete the whole .kde directory, but I think changing it is more elegant & you don't lose settings.

There is also a widget with a ON/OFF switch. On kde-look.org I think.

---

### Post by fooman on 2008-12-11
the compiz-fusion icon puts an icon in the panel for you so that you can control turning effects on/off, enable/disable emerald themes, bring up the compizcofig settings manager and more!

install it in synaptic or from a terminal:

```
sudo apt-get install fusion-icon
```


EDIT: wow,  way too slow...phil beat me to it!

---

### Post by za.zen on 2008-12-11
> **HavocXphere said:**
> Yes. In fact its not about "can it be done"...it is very likely that you *will* have to do that if you run into problems.


Note the .kde->It's a hidden directory...so it won't show with ls


Thats what you need to change. Some people just delete the whole .kde directory, but I think changing it is more elegant & you don't lose settings.

There is also a widget with a ON/OFF switch. On kde-look.org I think.

This is what I'm looking for.  The fusion icons hangs and then crashes.  Besides, I'm kind of looking for a one-click switch.  

How would I go about editing that file, from the command line?  Like, in a shell script setting.  I'm not very familiar with file-editing capabilities of CLI.  

Thanks all for the snappy replies.  :)

---

### Post by HavocXphere on 2008-12-11
[http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299](http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299)

The easiest way would be to just create a file for each settings and then overwrite it as needed.

I wouldn't bother though. The file editing thing is mainly for when the stuff hits the fan. You'd use something like nano to edit it via cli. Just use the plasmoid linked above.

There *is* also a straight konsole style way to switch it off...I know I saw it somewhere.

btw I've got the exact same problem. Can't wait for 9.04 with DRI2.

---

### Post by za.zen on 2008-12-11
> **HavocXphere said:**
> [http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299](http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299)

The easiest way would be to just create a file for each settings and then overwrite it as needed.

I wouldn't bother though. The file editing thing is mainly for when the stuff hits the fan. You'd use something like nano to edit it via cli. Just use the plasmoid linked above.

There *is* also a straight konsole style way to switch it off...I know I saw it somewhere.

btw I've got the exact same problem. Can't wait for 9.04 with DRI2.

No doubt.  I wish DRI2 was ready to go now.  

Anyway, I'll check out the plasmoid.  I was just wondering how to do it...figured I'd make my life easier and learn something in the process.  :)

Thanks again!

---

### Post by za.zen on 2008-12-11
Here are the directions to install the plasmoid:

>     *  tar -xvf plasmoid.tar.gz
    * cd plasmoid
    * mkdir build
    * cd build
    * cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
    * make
    * sudo make install OR su -c "make install"
    * Have fun! :-) 

They don't work.  First it told me CMake wasn't installed.  So I installed it (sudo apt-get install cmake) and tried again.  Got this error:

> james@scribbler:~/Desktop/toggle-compositing-0.2.1/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..                                                
-- The C compiler identification is GNU                                         
-- The CXX compiler identification is unknown                                   
-- Check for working C compiler: /usr/bin/gcc                                   
-- Check for working C compiler: /usr/bin/gcc -- works                          
-- Detecting C compiler ABI info                                                
-- Detecting C compiler ABI info - done                                         
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND                  
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.                  
CMake Error: Internal CMake error, TryCompile configure of cmake failed         
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:





  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:1 (project)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring done


Any other options?  Suddenly modifying that file is looking better.  :P

EDIT:  I should note that I have almost no experience building things this way.  I'm a synaptic type of guy, normally.  :P  So maybe I'm doing something wrong.  IDK.  Thought I should throw that out there.  

Thanks!

---

### Post by za.zen on 2008-12-11
So I've found that the command:

```
grep -w "Enabled=false" /home/user/.kde/share/config/kwinrc
```

returns the appropriate line, and I should be able to use that output to test and see whether Enabled is true or false.  Now I've got to figure out how to edit that line via a CLI without using a text editor like nano.  Just as GREP searched the file with no text editor, I need to edit it in a similar way.  

Any ideas?  I'm looking for a command now, but don't really know what I'm looking for.  

Thanks!

---

### Post by za.zen on 2008-12-11
OK so modifying the file isn't possible as far as I can tell, so I'm back to tinkering with the plasmoid.  I read a post that said I needed to install a compiler, so i added the g++ ? compiler, and now I get this error:

> CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:72 (MESSAGE):        
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/james/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps


when I run this command:

```
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
```

Any ideas why this isn't working?  Thanks!

---

### Post by za.zen on 2008-12-11
double post...

---

