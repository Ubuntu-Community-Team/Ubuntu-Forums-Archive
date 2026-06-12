---
title: "Wanting to make a frontend"
date: 2008-04-04
forum: Gaming &amp; Leisure
---

### Post by GSZX1337 on 2008-04-04
for Osmose. Yes, I do know of wxOsmose, but it's only in RPM (tried using Alien, but it won't start up). How should I go about this? Someone linked me to [wxWidgets]("http://www.wxwidgets.org/"). Seems pretty good, but I'm not sure if it is the best route. 

Thanks in advance,
     GSZX1337

---

### Post by Vadi on 2008-04-04
Tried compiling the source? I think that would be easier...

(I couldn't find it, but then again, I have no idea what Osmose is)

Edit: French ubuntu chaps got a guide here: [http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/osmose&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3DwxOsmose%26start%3D10%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DMsw%26sa%3DN](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/osmose&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3DwxOsmose%26start%3D10%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DMsw%26sa%3DN)

---

### Post by GSZX1337 on 2008-04-04
I solved my problem, the error was pointing to an earlier (not working) installation. wxOsmOse works great! Thanks for finding the source, maybe I'll just compile that.

---

### Post by zagieman on 2008-04-04
I made a quick front end for osmose in gtk that consists of choosing a file and running it, plus a few options. It is just a tool for me to learn gtk but I would be interested in starting something if there is interest.

---

### Post by GSZX1337 on 2008-04-05
> **zagieman said:**
> I made a quick front end for osmose in gtk that consists of choosing a file and running it, plus a few options. It is just a tool for me to learn gtk but I would be interested in starting something if there is interest.
If you do it, I'll use it. :)

---

### Post by zagieman on 2008-04-06
What options should a frontend have for osmose have? Should I just use all of them or are some of them redundant?

---

### Post by GSZX1337 on 2008-04-06
Here's a list of option in Osmose the bolded ones are the ones I find most useful.
```
Options: 
    -paddle           emulates one axis paddle (mapped on mouse).
   **-joy              use joystick as input device, instead of keyboard.**
    -acceleration x.x paddle acceleration (0.1 to 5 default 0.5)
    **-fs               run in fullscreen   (default: windowed).**
    -nosound          do not play sounds. (default: sound on).
    -dp               use dark palette for screen emulation (default: off).
    -inifile          xxx use xxx as configuration file. 
    -fps              display fps in title bar.
    -monochrom        emulates B&W tv (default: off).
    **-scale2x          scale2x video filter implementation (default: off).**
    -bilinear         bilinear video filter (default: off).
    -tv               emulates TV scanline video filter (default: off).
    -scale2xscanline  Scale2x + 75% scanline video filter (default: off).
    -nn2x             nearest neighbour video filter (default: off).
   ** -cm               use codemaster games mem. mapper (default: off). **
  **  -km               use korean games mem. mapper (default: off). **
**    -irqhack          Enable irq hack (specific rom option. default off)**.
[B]    -pal              emulates PAL/SECAM video timing (default: NTSC).
    -jap              run as japanese sms (default: export).
    -exp              run as exported sms (default).[/B]

```
I'm not even sure what -paddle is.

---

### Post by zagieman on 2008-04-07
I'm guessing paddle emulates a paddle controller but I didn't even know there were games for SMS that used paddles.

No sound and FPS are very useful also.

---

### Post by GSZX1337 on 2008-04-07
> **zagieman said:**
> I'm guessing paddle emulates a paddle controller but I didn't even know there were games for SMS that used paddles.

No sound and FPS are very useful also.

For no sound, you can just turn down the system volume (that's what I do). I never really thought that FPS was useful since Sega Master System games aren't taxing on the hardware. I was considering the minimum options to run SMS games fullscreen (enough for an Alpha/Beta I suppose).

---

### Post by zagieman on 2008-04-07
Heres a quick mock up with a few vital options. If anyone could give it a test that would be cool.

Currently you have to select the osmose path. I'll cange that soon.

---

### Post by GSZX1337 on 2008-04-08
> **zagieman said:**
> Heres a quick mock up with a few vital options. If anyone could give it a test that would be cool.

Currently you have to select the osmose path. I'll cange that soon.

I'll try that as soon as I get back to my Ubuntu 'puter. :)

---

### Post by zagieman on 2008-04-08
Made a small adjustment. Now just extract the files so they are in the same directory as osmose. Then run "GOsmose".

---

### Post by GSZX1337 on 2008-04-10
Front end's great! FPS doesn't work, but it doesn't work in wxOsmose, so I guess it's a problem with the emu itself.

---

### Post by zagieman on 2008-04-10
I think it worked for me, it displays the FPS in the title of the window not in the window itself.

---

### Post by jorgerosa on 2008-04-10
> **zagieman said:**
> (...) I would be interested in starting something if there is interest.
My reason to change to Linux is because it makes me so happy to see there are guys out there, allways trying to help others! :)
**zagieman**, can you post a tutorial, or so, refering the tools you used to do that front-end for gnome for that piece of software? (if you have time, of course).
Maybe i could develop front-ends for [iteam]("http://ubuntuforums.org/showthread.php?t=427011") and [isoccer]("http://ubuntuforums.org/showthread.php?t=747426") (maybe i could develop "one click button installers", or so...).
Since some people, me included, gets in panic when we see that long command lines. **Thanks.**

---

### Post by zagieman on 2008-04-10
It will all depend on what your lanuage of choice is. I found Gtk quite easy to learn although I am rather amatuer and still suck quite a bit. There are quite a few good resources online that I could direct you to, all depending on what language you like.

---

### Post by jorgerosa on 2008-04-10
Thanks for your reply. :) Any language will be fine.

---

### Post by zagieman on 2008-04-10
Well I personally use C++ and gtkmm at [http://www.gtkmm.org/](http://www.gtkmm.org/) 

You can get all the info you need from the documentation on their site. A good place to start is here:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html)
and here:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-helloworld.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-helloworld.html)

Then you can build on your simple code by adding different widgets, most of which are listed in the documentation [http://www.gtkmm.org/documentation.shtml](http://www.gtkmm.org/documentation.shtml). Give those a read then PM if you would like some specific help.

---

### Post by jorgerosa on 2008-04-11
 Thankyou!

---

