---
title: "How to run a binary file in Ubuntu GUI?"
date: 2010-12-22
forum: Desktop Environments
---

### Post by zhaotianwu on 2010-12-22
I am trying out an open source software ([http://faces.homeip.net/download.html](http://faces.homeip.net/download.html)). According to its installation instruction, "**Linux** users with an x86 compatible platform can use the  [ frozen package]("http://prdownloads.sourceforge.net/faces-project/faces-pm-0.11.7-frozen-i386.tar.gz?download") for a quick installation (Just unpack the tar file in directory an start the faces binary). "
So I just did it and unpacked it. However, when I click on the application file, which is named "faces", nothing happens. I'm new to Ubuntu so I'm not sure if there is anything that I should do before I can click and run an application like this?

---

### Post by zhaotianwu on 2010-12-22
**Another similar problem with GanttPV, [http://www.pureviolet.net/ganttpv/help/download/#Linux](http://www.pureviolet.net/ganttpv/help/download/#Linux)**


This is a Python program. I downloaded the package, and tried to mount it in my Eclipse Python pluglin, but it always failed to find a data module. I tried it using command line mode, but it always reported invalid syntax. How can I ever get things run?:(

---

### Post by 3Miro on 2010-12-22
Open terminal and then cd into the folder with the extracted files. Then you can use the command:
```
./faces
```

This will let you see errors. In my case it wants Python 2.5, which I don't have installed. You can check the Ubuntu Software Center (or better yet Synaptic Package Manager) to install Python 2.5.

The project doesn't seem to be alive anymore.

What is it that you want to achieve with this program, there may be a better program in the Software Center.

---

### Post by zhaotianwu on 2010-12-23
> **3Miro said:**
> Open terminal and then cd into the folder with the extracted files. Then you can use the command:
```
./faces
```This will let you see errors. In my case it wants Python 2.5, which I don't have installed. You can check the Ubuntu Software Center (or better yet Synaptic Package Manager) to install Python 2.5.

The project doesn't seem to be alive anymore.

What is it that you want to achieve with this program, there may be a better program in the Software Center.


Thanks. But what is "cd into the folder"? Was it a typo? And could you please explain what ./faces mean?

---

### Post by Lone_Joker on 2010-12-23
He means go into terminal and run
```
cd /path/to/folder
```

That just tells the terminal what folder to go to.

---

