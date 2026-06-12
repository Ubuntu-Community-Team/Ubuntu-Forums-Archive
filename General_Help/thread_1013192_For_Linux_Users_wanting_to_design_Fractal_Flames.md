---
title: "For Linux Users wanting to design Fractal Flames"
date: 2008-12-16
forum: General Help
---

### Post by djbushido on 2008-12-16
Okay, first things first, this is tested on Intrepid, but should work with Hardy, etc.

You should have a very basic knowledge of terminal commands. I will tell you exactly what you need to do, but this will help.

Now, make sure build-essential is installed. This is required.```
sudo apt-get install build-essential
```

Okay, so there are multiple ways to do this: Apophysis with WINE and Linux flam3(my recommendation), [Apophysis-J]("http://membres.lycos.fr/jfbouzereau/apophysis.html"), or Qosmic. (Fyre removed because these are not fractal flames - Fyre is like the Chaoscope of Linux)

To do any ways, you need these packages:
libjpeg-dev, libpng-dev, libxml2-dev, and zlib-dev

Which can be installed with synaptic, or
```
sudo apt-get install libjpeg-dev libpng-dev libxml2-dev zlib1g-dev
```

This will get you what you need to build flam3. Now, the fun stuff.
Make a temporary directory, like /home/your_name/flam3. To get the source code, do: ```
wget http://flam3.com/flam3-2.7.17.tar.gz
```
Then, we need to compile it, so do:```
./configure
make
sudo make install
```
This will install flam3-render to your /usr/bin directory to use.

Now that flam3 is out of the way, you have 3 options. You can either get Qosmic, get Apophysis-J, or use Apophysis via WINE (my preference)

To get qosmic, some extra work has to be done. In case the ultimate edition gets hosting worked out, this is a very easy way of getting it done, however is not currently working. Might work later.
Add the ultimate edition repo's to sources.list with this:```
sudo echo “deb http://repoubuntusoftware.info/ edgy all”>>/etc/apt/sources.list
sudo apt-get update
```

This will add the ultimate edition repo's so you can install qosmic easily. If you really feel like building it, the source code is [here]("http://code.google.com/p/qosmic/"). Note, you will need qt4-tools from synaptic.

Since the above method is currently not working, some extra stuff has to be done to avoid compiling it yourself, which is a pain.
Download an rpm from [this site]("http://rpmfind.net/linux/rpm2html/search.php?query=qosmic&submit=Search+...") dependent on your architecture. Then we need to install the alien package, with ```
sudo apt-get install alien
```
This will allow us to convert the .rpm to .deb. Also needed is liblua5.1. This can be installed AS A DEBIAN PACKAGE (i.e. built on debian NOT ubuntu - I am not responsible) [here]("http://packages.debian.org/unstable/lua5.1"). You can also compile it yourself, shouldn't be too hard. The source is [here]("http://www.lua.org/ftp/").

First install Lua whichever way you decide. It just needs to happen first.
Next, convert the qosmic rpm to a debian. In the folder where the .deb was placed, execute this command:```
sudo alien -d <name_of_qosmic_rpm>
```
This will generate a debian file which you can install. This should work, not tested thoroughly.

To use Apophysis-J, download it [here]("http://membres.lycos.fr/jfbouzereau/apophysis.html"). As far as I know, it uses an internal rendering engine, so you should just be able to execute the *.jar and you should be good to go. There is some help available on the site, and try and ask other people before me (i program c++ not java)

If you decide to use apophysis (which I recommend), you need to get WINE from the repo's with ```
sudo apt-get install wine
```

Now, get the Apophysis program from [here]("http://www.apophysis.org/downloads.html"). You can either get the sourceforge betas or the stable, i recommend the betas. Move the downloaded files to somewhere like /usr/share/Apophysis or /home/your_name/Apophysis, just somewhere easy to remember.

Okay, so now you get to play with the program, and when you have some *.flame files you like, then we get to render them.

To get a renderable flame, first make sure that Apophysis is linked to hqi.exe in the menu options-paths. hqi.exe should be in the same folder as apophysis.

Next, we open the file menu, then click export flame, or just Ctrl-X. Select the size, quality, etc parameters if you want to change them. 
NOTE:unless you _know_ what you're doing, don't mess with the slices, bits, etc. numbers, as this could screw things up. haven't tested myself.
Next, set the export directory, again, somewhere easy to remember.

VERY IMPORTANT!!!:unclick the "Render" box, otherwise your system will slow down a lot for no apparent reason (hqi.exe is running but not producing a visual result).

Finally, go to the directory in which this .flame is and do this:

Now, issue this command:```
env in=your_flame.flame out=your_flame.png flam3-render
```
This will render the flame to your_flame.png (you can also do jpeg, and change the name-also, if you don't use a name for "out", then flam3 will use the title of the flame file). Note that we compiled flam3 to save a lot of time over using the apophysis internal rendering engine.

Qosmic automatically uses flam3 as the renderer, so a standard render is all that is needed there.

Because apophysis-j is limited by memory in a java-vm, you should also use the export function.

I think that that is it, I will try to keep this updated, so I hope that this helps some people. Post any problems you have, and I will try and fix them.

---

### Post by acm321 on 2009-01-07
Thanks for that, it really helped, but I have a reccomendation:
Instead of using Apophysis with WINE, which can be a lot slower, I would reccomend using Apophysis-j, which is a java port of Apophyis and can be found [here.]("http://membres.lycos.fr/jfbouzereau/apophysis.html")
Once again, thanks!

---

### Post by djbushido on 2009-01-07
OK, thanks for the link
Just to let you know, i didn't include it by default, because i find it to be a pain. But adding in now.

---

### Post by argie on 2009-01-07
I played with Fyre a long while ago, and found it quite nice. Maybe not as big and complex as these, but I think mentioning it is relevant.

---

### Post by Demise on 2009-01-23
[http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) is parked on godaddy and not useable, got a walkaround besides compiling myself? I've run into way too many problems doing it that way.

---

### Post by djbushido on 2009-01-23
I hear you, I had a lot of problems.
The only thing i could recommend is to use alien and convert an rpm. I'll add a section on doing that. Sorry about ultimate edition, send a note to the dev and make sure he knows godaddy took over hosting.

EDIT: re-updated qosmic stuff, should work. Also, thanks for your first post on my thread!

---

