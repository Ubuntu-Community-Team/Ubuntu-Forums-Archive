---
title: "netcdf_c++ or libstdc++ issue"
date: 2005-12-20
forum: General Help
---

### Post by ccrab on 2005-12-20
I hope this is the correct place to ask this question.  If not please advise.  

I recently installed ubuntu and am trying to get my codes running.  I use netcdf_c++ for data storage, and am getting undefined references:

```
g++ -Wall  -O3  -o singleDCM singleDCM.o  DCMSim.o Equilibrium.o MPDistribution.o MarkerParticle.o GridQuantity.o T01.o Mag.o tsyg01.o geopack.o C05Density.o Density.o NameList.o GlobalDefs.o  -lnetcdf_c++ -lnetcdf -lgsl -lgslcblas -lg2c -lm
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/libnetcdf_c++.so: undefined reference to `std::basic_streambuf<char, std::char_traits<char> >::_M_out_cur_move(long)'
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/libnetcdf_c++.so: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_create(unsigned int, std::allocator<char> const&)'
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/libnetcdf_c++.so: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_S_empty_rep_storage'
collect2: ld returned 1 exit status
make: *** [singleDCM] Error 1

```

I'm using:

g++ (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
netcdfg3 3.5.0-7.1
netcdfg-dev 3.5.0-7.1 
libstdc++6 4.0.1-4ubuntu9
libstdc++6-4.0-dev 4.0.1-4ubuntu9

Am I missing a particular package that will fulfill the undefined references?  I thought these would be in libstdc++?  Is it a version mismatch?  Thanks for any help.

---

### Post by ccrab on 2005-12-20
I resolved the issue (somewhat), by reinstalling netcdf from source which must have fixed the libstdc++ mismatch issue.  For the record I

1) sudo passwd root (to set the passwd)
2) su (you need to be root, sudo will not work for the following)
3) apt-get update; apt-get build-dep netcdfg
4) apt-get --build source netcdfg
5) dpkg -i netcdf*.db

and then everything works.  But I have another question...

Now that I've built from source and installed, my software update icon says there is software to update.  If I choose to update my software, the binary packages are downloaded and installed and the system is broken again, forcing me to run the dpkg command over again.  The question is, why does the update manager think there are new packages to install?  Can't it tell that the package versions are the same?

---

