---
title: "Need Help On How to install XFCE"
date: 2006-10-09
forum: Desktop Environments
---

### Post by mimoh_mi on 2006-10-09
[I][COLOR="Red"][SIZE="4"]Please can anybody help me out
on the installation of XFCE destop on ubuntu. Downloaded,
i think all the packages and the gui builder. On running
it i getting these errors.

Xfce GTK+ engine and themes
Running configure... done
Running make all... done
Running make install... done
Cleaning up... done
Xfce Icon Theme
Running configure... done
Running make all... done
Running make install... done
Cleaning up... done
Xfce Utility Library
Running configure... done
Running make all... done
Running make install... done
Cleaning up... done
Xfce MCS Library
Running configure... failed

when i click the error button, i get this message

from the error page 
checking for X... no
configure: error: X Window system libraries and header files are required
!! Failed to configure libxfce4mcs, see the errors above
!! for details on the problem.

Thanks for your anticipated reply

](*,) [/SIZE][/COLOR][/I]

---

### Post by josys36 on 2006-10-09
There is a tread here already that outlines what dependcies you need to compile XFCE using their gui builder.

Just do a search for XFCE and you should find the how to.

Jason

---

### Post by aysiu on 2006-10-09
Any reason in particular you're compiling it instead of using the package manager to install it?

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) has package manager installation of XFCE instructions.

---

### Post by orev on 2006-10-14
You can open a terminal and type: 

```
sudo apt-get install xubuntu-desktop
```

This would be the easiest, IMHO.

---

### Post by aysiu on 2006-10-14
> **orev said:**
> You can open a terminal and type: 

```
sudo apt-get install xubuntu-desktop
```

This would be the easiest, IMHO.
Except you would use *aptitude* instead to make XFCE easier to remove should the OP wish to do so later: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by TiredBird on 2006-10-15
I have XFCE running but I installed it from the live CD. I have noticed however that a site I visit regularly has instructions on installing XFCE which I presume is a beta and looks similar to what you are doing. Take a look at these two links: [http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE]("http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE")
and [http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE_4.4_preview_versions_.284.3.90.1.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE_4.4_preview_versions_.284.3.90.1.29").
The first installs the current binary, I believe, but the second has compile instructions so I would guess it's something more recent.
The site is an unofficial one but I've used them as guidance for an awful lot of things and never been disappointed. A cut and paste of their instructions always seems to work. Try it. It might solve your problem.

---

