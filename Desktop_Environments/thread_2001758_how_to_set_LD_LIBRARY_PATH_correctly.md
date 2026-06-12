---
title: "how to set LD_LIBRARY_PATH correctly"
date: 2012-06-11
forum: Desktop Environments
---

### Post by aroky on 2012-06-11
Hi, all 

 By reading this post, [http://askubuntu.com/questions/121073/why-bash-profile-is-not-getting-sourced-when-opening-a-terminal](http://askubuntu.com/questions/121073/why-bash-profile-is-not-getting-sourced-when-opening-a-terminal)

  i set all my lib and path info in ~/.profile file, and delete ~/.bash_profile. 

  but after i logout, i can get my 'path' value, but i can not get my 'ld_library_path' value. why ? should i do extra work here?
  my sample .profile file : 

  export xxpath = /**/yy/zz

  export path = ${xxpath}/bin:${path}
 
  export LD_LIBRARY_PATH=${xxpath}/lib:${LD_LIBRARY_PATH}

  also, if i set my ld_library_path in my ~/.bashrc, i can get value if i do echo ${ld_library_path}. but when i do the compilation in c++ eclipse, it still can not find the lib. How can i set the lib path for c++ eclipse environment ? 

 thanks

---

### Post by steeldriver on 2012-06-11
what exactly are you trying to do?

if you are getting build-time linker errors, that's more likely related to static libraries I think - afaik LD_LIBRARY_PATH only affects shared libraries (.so files)

also these things are case sensitive so you won't be able to echo $ld_library_path if what you've set is LD_LIBRARY_PATH - your example .profile is a mess of upper and lower cases

in general, defining LD_LIBRARY_PATH in a login or shell profile is a bad idea anyway - if you absolutely need to run specific executables with specific non-standard library dependencies then write a launcher script for the executable that sets LD_LIBRARY_PATH *only* within that environment

---

### Post by sisco311 on 2012-06-11
[http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

---

