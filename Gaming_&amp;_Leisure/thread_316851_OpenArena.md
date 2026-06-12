---
title: "OpenArena"
date: 2006-12-11
forum: Gaming &amp; Leisure
---

### Post by lamego on 2006-12-11
Hello,
I have packaged an OpenArena .deb for Ubuntu Dapper/Edgy (32 bits)
[http://www.getdeb.net/app.php?name=openarena](http://www.getdeb.net/app.php?name=openarena)

Please let me know if it ran successfully.

Thanks

---

### Post by Lord Illidan on 2006-12-11
Worked well. Only thing lacking is a global executable.

---

### Post by lamego on 2006-12-11
What do you mean by "global executable" ?

---

### Post by leilei on 2006-12-11
Seems to successfully install and run and uninstall :)

Though the "bouncing file" cursor is rendered over the screen however.

---

### Post by Lord Illidan on 2006-12-11
> **lamego said:**
> What do you mean by "global executable" ?
To run the game I had to navigate to /usr/share/openarena instead of running it directly from the console...

Although, I see it has been added to the KMenu..ok then.

---

### Post by biodiesel-bri on 2006-12-17
Didn't work for me :(

I installed the missing lib openal0 or something like that, but when I run it all that happens is KDM restarts.  Boo.  The error scrolls off too fast to read.

Running from console gives me "/dev/fb0" permission errors, but I don't know if that is the actual problem or has something to do with the fact that X isn't running (I suspect the latter).

I'm running in 1440x900 with the binary nvidia drivers at 24 bit color.  Opengl does work.

---

### Post by biodiesel-bri on 2006-12-17
I figured it out.  The binary Nvidia driver had a bug.  The 9631 update fixes it.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

-B

---

### Post by bagofchickens on 2006-12-21
[A little late but I just found out this game even existed :) ]

Thanks for packaging! Worked right away. Love this shooter.

---

### Post by rajeev1204 on 2006-12-21
hi

i installed this on my 64 bit dapper 
but cant get it to run cos of missing libopenal.so . i tried using a 32 bit version of this file but it appears broken. can i use any other sound version?

is there a 64 bit version u made?


regards

rajeev

---

### Post by oly on 2006-12-21
I would also be intrested in a 64bit version of the deb if there is one floating about some where.

---

### Post by patrick295767 on 2006-12-21
who wanna play ? Ubuntu game IP server ?

---

### Post by lamego on 2006-12-25
Look at /usr/share/openarena , there is a 64 bits binary, I am on holidays so I can´t check it right now...

---

### Post by motang on 2007-01-16
Installed fine on my system and I also got the link to launch the game under Games.  Thanks for the wonderful job with the .deb file.

---

### Post by tnunamak on 2007-01-16
Does anyone know how I could get this to display properly with TwinView and a dual-head setup?

The game loads on one my of monitors, but it is kind of shoved halfway off of it.

---

### Post by agorex on 2007-01-22
Works for me! :guitar:

---

### Post by old_geekster on 2007-03-02
Thanks for the great work, lamego.  I just installed OA and it works perfectly.  There is a link in the Games menu, also.

---

### Post by soapyfish on 2007-04-24
Wow worked 99.9%.  Its the first time I have seen the software and nearly the first time I have gone to install a game on ubuntu and it worked fantasically  even got a Menu item (if not an icon "deducts 0.01% "  thankyou very much  !! 

abandonment of windows is one step closer ;-)  even spans over two screens

---

### Post by nave.notnilc on 2007-04-27
Could you set up a PPC version?

---

### Post by leilei on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=404216](http://ubuntuforums.org/showthread.php?t=404216)

---

### Post by adam0509 on 2007-04-27
I just love to play openarena often, thanks for making a package :]]]

---

### Post by Binarydreams on 2007-11-26
Hello all,

I know this thread is getting old but I noticed that when I take the link to getdeb.com the only versions for download are those after Dapper.  How can I get the latest Dapper deb?  I have been extremely happy with Dapper and don't plan on upgrading until LTS ends.

Thanks for the help!

---

### Post by prateekdayal on 2008-04-08
I downloaded the 64 bit debs on my hardy beta and tried installing the openareana-data deb with the command

sudo dpkg --install openarena-data_0.7.1-1~getdeb1_all.deb

It returns an error

(Reading database ... 247184 files and directories currently installed.)
Unpacking openarena-data (from openarena-data_0.7.1-1~getdeb1_all.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing openarena-data_0.7.1-1~getdeb1_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/games/openarena/baseoa/pak2-players-mature.pk3')
Errors were encountered while processing:
 openarena-data_0.7.1-1~getdeb1_all.deb


I tried using ar x openarena-data and it said malformed deb file

I downloaded it again and it still gives the same error. Any ideas ?

I would love to try this game but it is just not co-operating :)

---

### Post by AprilHare on 2008-11-26
Tried installing OpenArena 0.8.1 from here.
It runs - but there are no maps installed, so game didn't work. Not sure why.

---

### Post by bladerunnerfast on 2009-08-26
sorry am not fully used to linux
how do you install as root user?

---

### Post by Zanthir on 2010-10-21
Open Arena 0.8.5 is available for Ubuntu 10.10 Maverick Meerkat with apt-get after you update your universe file to say Maverick instead of Lucid (from 10.04).
 
But some features require additional downloading from another site. I'm not sure if this could be included in the apt-get package or not.

---

### Post by Perfect Storm on 2010-10-22
3 times necromacing. Going to close the thread this time.

---

