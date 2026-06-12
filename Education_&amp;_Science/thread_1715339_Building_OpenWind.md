---
title: "Building OpenWind"
date: 2011-03-26
forum: Education &amp; Science
---

### Post by Goyo on 2011-03-26
[OpenWind]("http://www.awsopenwind.org/") is a free wind farm design program. I had kinda hard time building it from source (mostly due to being new to the Ultimate++ environment) so I'm writing this for my own reference and to help others. Please note that I still don't understand Ultimate++ well so there may be better ways, this is just what I did and worked. Please comment if you know how to improve this. I used Ubuntu 10.10 (Maverick) and openWind_00.09.00.0837_280211 source code.

First you have to grab the sources from [http://www.awsopenwind.org/downloads/source-code-archive](http://www.awsopenwind.org/downloads/source-code-archive). It requires you to create a user account. Download openWind_00.09.00.0837_280211.zip, unzip it and rename the resulting folder to OpenWind.

You'll need to download the geotiff plugin for Ultimate++ too. From the same page download geotiff.zip by clicking in the additional plugins link and unzip it.

Now install Ultimate++. Jan Dolinár mantains a repository for Ubuntu at [https://launchpad.net/~dolik-rce/+archive/upp](https://launchpad.net/~dolik-rce/+archive/upp). Typing these commands in a terminal will install all the required libraries and the development environment TheIDE.
```
$ sudo add-apt-repository ppa:dolik-rce/upp
$ sudo apt-get update
$ sudo apt-get install upp
```
In the GNOME menu select Applications > Programming > TheIDE. A dialog lets you to create user copies of Ultimate++ source code, examples and tutorials. I don't know how necessary or convenient is this, but since in the OpenWind site it's said that you need to add the geotiff plugin in the uppsrc directory I guess making a user copy of it is a good idea.
[IMG]http://www.23hq.com/goyo/photo/6594795/original[/IMG]
In the "Select main package" dialog press Cancel.
[[IMG]http://www.23hq.com/6355826/6594797_27a78ab9cce81ffb2799434a4560acc5_standard.jpg[/IMG]]("http://www.23hq.com/goyo/photo/6594797/original")
Go to the directory where you copied the Ultimate++ sources, in my case /home/goyo/upp. Create a directory called MyApps and copy the OpenWind directory into it. This will make OpenWind to be shown in the "Select main package" dialog. Then go to the plugin directory of the Ultimate++ source code, in my case /home/goyo/upp/uppsrc/plugin. Copy the geotiff directory into it.
Open TheIDE again. The "Select main package" dialog will be displayed. In the Assembly list select MyApps. Then select the OpenWind package and press OK.
[[IMG]http://www.23hq.com/6355830/6594798_e7bd8ad503f881943e2c7870120c6fa1_standard.jpg[/IMG]]("http://www.23hq.com/goyo/photo/6594798/original")
When the main window of TheIDE shows up, look at the toolbar where it reads "GCC Debug". The debug option will create a huge executable file with debug symbols. If you don't want this, click on the right arrow and select Optimal (or Speed or Size if you prefer).
[[IMG]http://www.23hq.com/6355822/6594802_05b97ed1c7c4bf2900a54b29f90f70d7_standard.jpg[/IMG]]("http://www.23hq.com/goyo/photo/6594802/original")
Now, in order to avoid an annoying error message about gdk-pixbuf/gdk-pixbuf.h not being found you have to tell its location to TheIDE. Select Setup > Build methods, then the INCLUDE directories tab. Right click on the list of directories, select Append row and add /usr/include/gdk-pixbuf-2.0 to the list.
[[IMG]http://www.23hq.com/23666/6604609_c6ee15612538f294da639872612c9098_standard.jpg[/IMG]]("http://www.23hq.com/goyo/photo/6604609/original")
You're now ready to build OpenWind. In the menu bar select Build > Build (or press F7). In order to find the executable select Build > Open output directory. Just double click on OpenWind and enjoy designing your wind farm.

---

### Post by dolik.rce on 2011-03-27
Hi Goyo!
No idea how can someone say theide is hard to work with for beginners, you got it perfect on your first try ;)

> **Goyo said:**
> Now, when I tried to build OpenWind for the first time I got an error message about gdk-pixbuf/gdk-pixbuf.h not being found. For sure the proper way to fix this problem is telling TheIDE about include directories. But since I didn't know how to do that I used the old and dirty trick of symlinking and it worked:
```
$ cd /usr/include
$ sudo ln -s gdk-pixbuf-2.0/gdk-pixbuf gdk-pixbuf
```
Open TheIDE again.
The "proper" way is to add the path into Setup > Build methods > GCC (in the list on the left) > "INCLUDE paths" tab. In newer versions (e.g. those in nightly builds PPA) this path is present by default. Anyway, the symlink solution is just as good.

> **Goyo said:**
> You're now ready to build OpenWind. In the menu bar select Build > Build (or press F7). In order to find the executable select Build > Open output directory. Just double click on OpenWind and enjoy designing your wind farm.
You can also do all this in single step, using Debug > Run (or Ctrl+F5), which compiles the application and executes it.

Best regards,
Honza (aka Jan Dolinar)

---

### Post by Goyo on 2011-03-29
Hi Honza, thanks for your feedbak and your advice.

> **dolik.rce said:**
> 
No idea how can someone say theide is hard to work with for beginners, you got it perfect on your first try ;)

Not really so hard but just a bunch of new things to put together in my brain and then in my box.

> The "proper" way is to add the path into Setup > Build methods > GCC (in the list on the left) > "INCLUDE paths" tab. In newer versions (e.g. those in nightly builds PPA) this path is present by default. Anyway, the symlink solution is just as good.

I found adding the path to the INCLUDES list far more convenient so I updated the post.

Goyo

---

### Post by agav on 2011-08-29
Hi Goyo, i need you help for installing openwind. When i click the Myapps icon, open wind does not appear right side. what can be a problem. Thanks...

---

### Post by Goyo on 2011-09-05
Please run this command and paste the output here:
```
ls ~/upp/MyApps
```

---

### Post by akamad on 2011-09-19
Hi Goyo,
I am having the same issue as Agav.

> **Goyo said:**
> Please run this command and paste the output here:
```
ls ~/upp/MyApps
```

The output is:
wiki@wiki-test:~$ ls ~/upp/MyApps/
OpenWind_00.09.00.0916_220811

Thanks!

---

### Post by Goyo on 2011-09-20
> **akamad said:**
> 
```
wiki@wiki-test:~$ ls ~/upp/MyApps/
OpenWind_00.09.00.0916_220811
```


Rename OpenWind_00.09.00.0916_220811 to just OpenWind, otherwise the project won't appear in the dialog. I guess the directory name has to be the same as the project name as written in some project configuration file.

---

### Post by akamad on 2011-09-20
> **Goyo said:**
> Rename OpenWind_00.09.00.0916_220811 to just OpenWind, otherwise the project won't appear in the dialog. I guess the directory name has to be the same as the project name as written in some project configuration file.

Perfect, that did the trick! Thanks.

---

