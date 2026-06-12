---
title: "Installing boost libraries and rose"
date: 2009-05-20
forum: General Help
---

### Post by shejohn on 2009-05-20
Hey
I downloaded boost_1_39_0.tar.gz from boost.org and followed the instructions for installation under Getting Started on Unix variants.
After the steps I have my boost headers under /usr/local/include/boost_1_39_0/boost
but I can't find the binaries under lib/.
When i did a search i found a lib/ in 4 paths:
/usr/local/boost_1_39_0/tools/build/v2/test/generators-test/
/usr/local/boost_1_39_0/tools/build/v2/test/project-test3/
/usr/local/boost_1_39_0/tools/build/v2/test/project-test4/ost li
/usr/local/boost_1_39_0/tools/build/v2/test/test-boost-build/missing_dependencies/

Which one of these path can i use to specify boost libraries for $LD_LIBRARY_PATH?
I'm trying to install rose-0.9.4a and i need to specify the bosst lib/ path for it in $LD_LIBRARY_PATH. 
I have given the above paths in $LD_LIBRARY _PATH path while installing rose-0.9.4a but it does not get accepted and it keeps prompting me to specify the correct boost libraries path. How can I get my boost lib/?
Please help!

---

