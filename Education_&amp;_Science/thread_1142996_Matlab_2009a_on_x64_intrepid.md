---
title: "Matlab 2009a on x64 intrepid"
date: 2009-04-29
forum: Education &amp; Science
---

### Post by amiq on 2009-04-29
I have been using the latest version of matlab(2009a) on x64 ubuntu 8.10 for a couple of weeks now.
Every thing works fine but I can't make the matlab compile my C files into Matlab mex(using mex function). Intrepid is shipped with gcc 4.3.2 while the latest version that matlab supports is still [gcc 4.2.3  ]("http://www.mathworks.com/support/compilers/current_release/linux.html") so I think this should be the source of the problem.
When I mex a script, matlab warns me about the wrong version of the GCC and then the mex-ed file does not work properly. I get odd errors like "out of memory" or the mex ed function returns an incorrect value. The script works fine when I mex it on another computer with an older version of Linux(opensuse 10.3) which has a compatible GCC.

I tried to install an older version of GCC on intrepid but I either did it wrong or it didn't solve my problem.

I would appreciate if anyone have any idea/experience about solving this problem.

amiq

---

