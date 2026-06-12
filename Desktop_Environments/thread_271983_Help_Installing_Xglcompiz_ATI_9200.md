---
title: "Help Installing Xgl/compiz ATI 9200"
date: 2006-10-05
forum: Desktop Environments
---

### Post by klgsx on 2006-10-05
I keep on reading and hearing about this Xgl/compiz but i havent found 1 official site about "HOW-TO" install it on my laptop

My laptop video card is a ATI Radeo 9200

Any suggestion would be welcome.

ohhh btw... new to ubuntu

Thanks

---

### Post by OpticalIllusion on 2006-10-05
First of all, add these to your sources.list by typing in

```
sudo gedit /etc/apt/sources.list
```

Now, paste these into the bottom of your list somewhere and save it.
```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```

Now, follow this HOW TO on how to install XGL + Beryl (the new compiz).  This How To is the best one I have used yet, because it's the only one that I have gotten to work.

[http://ubuntuforums.org/showpost.php?p=1561758&postcount=26](http://ubuntuforums.org/showpost.php?p=1561758&postcount=26)

---

### Post by geetarista on 2006-10-08
klgsx: Did this work for you?

I've scoured the forums on how to get my 9200 (RV280) to work with XGL/Beryl, but I'm still not able to get it to work.  I tried to use the howto that OpticalIllusion linked to, but that didn't work either.  I'm close because I can switch over to Beryl and the splash screen pops up, but after I try to do anything it just crashes and exits out of X.  I've tried about 10 different configurations with my xorg.conf.  I've attached my latest one for you all to look at.

I've read through all of these links and still haven't gotten it to work:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
[http://www.ubuntuforums.org/showthread.php?t=221632](http://www.ubuntuforums.org/showthread.php?t=221632)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)
[http://ubuntuforums.org/showpost.php?p=1561758&postcount=26](http://ubuntuforums.org/showpost.php?p=1561758&postcount=26)
[http://www.ubuntuforums.org/showthread.php?t=268149](http://www.ubuntuforums.org/showthread.php?t=268149)
[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)
[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)
[http://www.ubuntuforums.org/showthread.php?t=265678](http://www.ubuntuforums.org/showthread.php?t=265678)
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)
[http://forum.beryl-project.org/topic-389-howto-compiz-gnome](http://forum.beryl-project.org/topic-389-howto-compiz-gnome)

Everything seems confusing because some people say use the driver included in Dapper, others say to use the ATI driver.  Some say to use xgl, and others say to use aiglx.  Everybody lists different startup session commands to use.

Has anyone else gotten this card to work under Dapper in Gnome?  If so, how?

---

### Post by galego on 2006-10-08
ok you have tried alot and i dont want to give you just more places to go; however looking at you file and the card that you are running it should work. first before you start run this in terminal:
```
fglrxinfo
```
it should return something like this
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700Pro
OpenGL version string: 2.0.5814 (8.25.18)
```

if it did not and it said MESA driver this is what you need to fix. you dont have the driver installed so go here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")
once you have it good to go go here and i promise this will get it working it is easy to follow and it gives some troubleshooting if you get hung up:
[https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")
i have used both of these links many times and has always worked. the above link will guide you to installing beryl as well just read it step by step.

BTW DONT FORGET TO install ```
xserver-xgl
``` when you are following the XGL how to. and also make sure your sources list has what is required, from the how to. not a bad idea to go ahead and make sure your system is upto date before you start. use synaptic.

---

### Post by geetarista on 2006-10-08
I installed the driver using method 1 before, but do I need to use method 2 like you suggested to make it work?  I used method 1 because method two says this: "The new fglrx driver supports Radeon 9500+ (older cards will not work!) and the X-series cards up to X1900."

Will it still work if I try method 2?

Ummmm...well, I tried out method 2, but all of a sudden my wireless didn't work.  I reverted back to kernel 2.6.15-27-686 and it worked, but after trying to install the ATI driver again, the same thing happened.  ](*,)  I then booted the 2.6.15-25-686 and my wifi works again, but I'm not going to try step 2 again.  I'm pretty sure the problem has to do with this part:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

I re-attached my new xorg.conf just in case anyone wanted to look at.  Before, when I tried to use method 1, fglrxinfo gave me the correct output and glxinfo said I had direct rendering, but now it doesn't after installing through method 2.  The only problem was that Beryl crashed when I tried to switch over to it.

If I had to choose b/n XGL/Beryl and my wireless, I'll go with the latter.  I wanted to just try and see if I could make this work, but I've spent waaaay too much time on this to be worth it.  Maybe I'll wait until I can afford a better card...

---

### Post by geetarista on 2006-10-12
Has anyone else had this problem or found a solution?

---

### Post by igknighted on 2006-10-12
I don't mean to be a downer, but when I first ran into compiz/XGL on SUSE earlier this year I read through the documentation they provided, and that card is one of several that are listed as incompatible (I know because that is what I had at the time).  The link to the page is: [http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl) (scroll down to the problematic hardware section).  If you do manage to get this card to work post how here because I have another computer that I would love to put that card in and still use XGL

---

### Post by blitzer on 2006-10-12
First you must get 3D acceleration going for your 9200 - This is how I got my 9200 SE using 3D. [http://www.ubuntuforums.org/showpost.php?p=1585558&postcount=55]("http://www.ubuntuforums.org/showpost.php?p=1585558&postcount=55")

[COLOR="Red"]Please do this step by step as it states ![/COLOR] 
As you can see I have the 8.25 driver working for my 9200 SE

As far as Igknighted stated for the 9200 - this is what it actually say's [URL="http://en.opensuse.org/Xgl"]> Radeon 9200
No hardware acceleration using fglrx 8.22.5 driver[/URL]
[COLOR="Blue"]Your card will be using the newer driver 8.25[/COLOR] :cool: 
Then post your 
```
Fglrxinfo
```



Please let us know if you get XGL running after you have 3D enabled8)

---

### Post by geetarista on 2006-10-12
OK, so it looks like I should have done method 1 instead of method 2.  Is there any way that I can undo everything I did in step 2 and start from scratch?

---

### Post by blitzer on 2006-10-13
Re-installing Dapper for me would be the way I would do it.  I don't know if it would be easier for you though - maybe someone else on the forums could direct you in starting over :-k 

Re-installing Dapper is painless as I remember :mrgreen:   Having done this many times.

I will be attempting to install the eyecandy soon, was hoping someone else with a 9200 SE card could let us know how it's working for them.

Good luck and report back :)

---

