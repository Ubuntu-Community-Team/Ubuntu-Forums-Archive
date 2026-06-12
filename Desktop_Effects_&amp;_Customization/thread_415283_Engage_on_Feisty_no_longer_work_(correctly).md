---
title: "Engage on Feisty no longer work (correctly)"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by TomG on 2007-04-20
Hi,

I'm desperately try to reinstall E17 Engage dock bar after Feisty Fawn fresh install without (complete) success.
I followed accurately steps from here :
**[http://e17blog.tuxfamily.org/e17blog-feisty_en.php/post/2007/03/10/Enlightenment-Repositories-for-Ubuntu-Feisty-Fawn](http://e17blog.tuxfamily.org/e17blog-feisty_en.php/post/2007/03/10/Enlightenment-Repositories-for-Ubuntu-Feisty-Fawn)**

So I did :
    tom@feistyfawn:~$ sudo apt-get install enlightenment
    tom@feistyfawn:~$ sudo apt-get install engage
    tom@feistyfawn:~$ sudo apt-get install emodules0-all
    tom@feistyfawn:~$ sudo apt-get install e17

Then I can get Engage starting but the settings and icons (hidden folders and files repatriated from Edgy and placed in home directory) no longer works correctly.
I get 
 - Some **"?"** characters instead of icons (likely from /usr/share/engage/icons/xapp.eap)
 - Some **"BUG: References 1 /home/tom/.e/e/applications/all/xchat.eap"** messages for all the icons when closing Engage
 - Some **"File: /usr/share/engage/icons/xapp.eap is not up to date for key "collections/0" - needs rebuilding sometime"** messages for all the icons when closing Engage
 - Some **"File: /home/tom/.e/e/applications/all/firefox.eap is not up to date for key "edje_file" - needs rebuilding sometime"** messages for all the icons when closing Engage

So it seems that EAP icons need to be rebuilt. I know that I can rebuild icons from command line with script in the** icon_example.tar.gz **package 
but I can find neither "**enlightment_eap**" executable (called by script) nor "**eap_edit**" (which should replace "e_util_eapp_edit") despite a complete e17 install !

Did anyone succeed to install and use Engage on Feisty ?

Thanks,
TomG

---

### Post by worldwithoutgurus on 2007-04-20
Engage is dead.
Eap files are no longer used.
 Just a waste of time...

---

### Post by TomG on 2007-04-23
May be old or dead. 
But it is nice and very stable. That's the best dock I've ever used.

---

### Post by des4ij on 2007-04-27
yes its the best, it works very stable in DreamLinux... After all all the other docks dont even work for the most part without beryl...

---

### Post by nlogax on 2007-04-28
> **worldwithoutgurus said:**
> Engage is dead.
Eap files are no longer used.

Is there an alternative E17 system tray?  Or do we have to use a standalone SysTray such as Trayer?

---

### Post by worldwithoutgurus on 2007-04-28
I use Itask.

First, install subversion.

Then: 
svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng

And:
cd ~/itask-module/itask_ng/itask_ng
./autogen.sh
make
sudo make install

Screenshot:
[http://perso.orange.fr/pinguSODalon/screens/itask.png](http://perso.orange.fr/pinguSODalon/screens/itask.png)

See also:
[http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2](http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2)

---

### Post by nlogax on 2007-04-28
> **worldwithoutgurus said:**
> I use Itask

Does it function as a System Tray?  I don't see any mention of that in the sparse documentation or the example video.

---

### Post by skroll on 2007-05-06
I managed to grab the latest version and compile it.  When I try to enable the module, Enlightenment tells me that it cannot find "itask/module.so" in any of the module search paths.  Yet I have .e/e/modules/itask/module.so in my home dir, and it's set as a path for modules in the my config.  I'm assuming something is going wrong during the compile, and that module.so is not working properly.

Anyone possibly have this packaged as a .deb to make it easier?  Even a checkinstall .deb would work (as itask only seems to depend on the enlightenment libs)

---

### Post by joshb86 on 2007-05-08
I have yet to find anything thats a nice and works as smooth as engage. However im having a hard time getting it to work on feisty also.... and resolution yet? I was going to try the itask but never even got it close to working. If someone could post a download link and a good walk through i would give it a shot.... so far nothing i've seen though has been as good as engage. I came back to ubuntu after being a strong dreamlinux user.... which i still am... just want to be able to help people and friends that use linux... and most of them are on ubuntu.

---

### Post by skroll on 2007-05-08
> **joshb86 said:**
> I have yet to find anything thats a nice and works as smooth as engage. However im having a hard time getting it to work on feisty also.... and resolution yet? I was going to try the itask but never even got it close to working. If someone could post a download link and a good walk through i would give it a shot.... so far nothing i've seen though has been as good as engage. I came back to ubuntu after being a strong dreamlinux user.... which i still am... just want to be able to help people and friends that use linux... and most of them are on ubuntu.

I actually got itask working, but it's a bit of a pain (especially since it requires a composite manager to do anything worthwhile, and on top of that it is having a hard time letting me click through to windows underneath) but if you want a real walkthrough, it's right here:

1) sudo apt-get install subversion
2) sudo apt-get install e17-devel
3) cd ~
4) svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng
5) cd ~/itask-module/itask_ng/itask_ng
6) ./autogen.sh
7) make
8) make install

Now you **should** have a module available in enlightenment.  If you try to start it and it complains that module.so is missing in a directory, mine was installed to a dir that was for 686, and had to be renamed for 486.  This may or may not happen to you.

Then you can create a panel and add itask to it.  There's a readme in the itask dir if you need more information.

---

### Post by joshb86 on 2007-05-08
Thanks Skroll... Now are you guys doing this under gnome? or are you running an elightenment session?

---

### Post by skroll on 2007-05-08
> **joshb86 said:**
> Thanks Skroll... Now are you guys doing this under gnome? or are you running an elightenment session?

Well iTask is an Enlightenment module, so I'm pretty sure it will only work in E, although I could be wrong.

---

### Post by izizzle on 2007-05-09
Hey skroll, your display pic creeps me out...........seriously...... :D

---

### Post by skroll on 2007-05-09
> **izizzle said:**
> Hey skroll, your display pic creeps me out...........seriously...... :D

On every forum I post on, at least one person says this exact sentence.

---

### Post by izizzle on 2007-05-11
I'm not surprised :D

---

### Post by nevin on 2007-06-14
i installed engage easily.
i run a xgl/beryl session.
so i run engage from the terminal and it shows up about an inch from the bottom of my screen with no icons and with the background around it messed up.  (ill post screenshot)
also, there are no icons and i cannot choose the configuration option.

ive used dreamlinux and think the dock is spectacular and would like to use it with my everyday ubuntu.  if anyone has any fixes or links to fixes, they would be greatly appreciated.

[IMG]http://farm2.static.flickr.com/1189/547769071_61bc3b4ac3_o.png[/IMG]

---

### Post by TomG on 2007-06-14
I've finally also been able to install Engage on another PC but I still have packages conflict (?) on my main computer. However I still not have answer to this last question too :(

---

### Post by nevin on 2007-06-19
when i try to go through the right click menu and select configuration, i get this error in the terminal:

***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.




i dont know what any of that means.  do i need to put something in the ()?

if anyone has a link to a forum that is more centered towards engage, please point me in that direction.

---

