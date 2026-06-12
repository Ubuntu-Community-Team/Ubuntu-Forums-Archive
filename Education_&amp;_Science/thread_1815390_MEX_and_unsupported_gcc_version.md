---
title: "MEX and unsupported gcc version"
date: 2011-07-31
forum: Education &amp; Science
---

### Post by evenrelation on 2011-07-31
Hello

When I run "mexall" in Matlab 7.10.0 I get 

```
>> mexall

Warning: You are using gcc version "4.5.2-8ubuntu4)".  The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         http://www.mathworks.com/support/compilers/current_release/

/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl.so.7)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl.so.7)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libgmpxx.so.4)

    mex: compile of ' "baw.c"' failed.

??? Error using ==> mex at 222
Unable to complete successfully.

Error in ==> mexall at 26
  mex(files(i).name)
```When I googled, all I could find was [http://ubuntuforums.org/showthread.php?t=1413330](http://ubuntuforums.org/showthread.php?t=1413330)
where the problem seemed to concern permissions. 

Would it be enough for me to install gcc 4.2.3? If so, how? I could not find it in the package manager.

In any case, for some reason, I could not find the file 'baw.c' in my Matlab subdirectory.

Sorry, I'm not a Linux superuser, just an average bloke.

---

### Post by tommpogg on 2011-08-01
The message about the gcc version is just a warning: usually the compilation is performed correctly (at least in my case). So I wouldn't worry about that.

The problem seems to be that the compiler cannot find he file "baw.c". Couldn't it be caused by some missing library in your c code?
Maybe there is a correlation with the messages:
```

/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl_c.so.2)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/libppl.so.7)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libppl.so.7)
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/cc1: /home/username/matlab/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libgmpxx.so.4) 

```In this case you can take a look [here]("http://ubuntuforums.org/showthread.php?t=1809300") and [here]("http://ubuntuforums.org/showthread.php?t=808045").

---

