---
title: "Flight Gear - deb of fgrun"
date: 2006-12-09
forum: Gaming &amp; Leisure
---

### Post by viciouslime on 2006-12-09
If anyone likes playing flight gear, but doesn't like having to use the command line to start it then give fgrun a try. It is a graphical launcher for flight gear, I have made a deb file for it and it would be great if people could test it for me and let me know if it works for them :D 

Both versions can be found on my site, in the downloads section:

[http://www.viciouslime.co.uk]("http://www.viciouslime.co.uk")

[COLOR="Red"]UPDATE: THIS NOW WORKS ON HARDY HERON FOR 32 AND 64 BIT USERS[/COLOR]

---

### Post by Borfo on 2007-01-08
looks like it works for me, thanks.

---

### Post by viciouslime on 2007-01-10
> **Borfo said:**
> looks like it works for me, thanks.

You're welcome! Thanks for reporting back.

---

### Post by smurfit on 2007-02-07
Been looking everywhere for this........
Not working, asking for some setup options & when filled in I cannot click next.
FGFS working fine, I wanted this to make life easier, just updated to Feisty, Kubuntu.
Any ideas?

---

### Post by Icarosaurus on 2007-02-18
Very nice job!!
I'll let you know if I'll think about some improvement: I'm just starting flying with FG.

smurfit: I'm using Ubuntu Feisty and it works nice...maybe you have to check settings.
I have installed FG from ubuntu repositories so my settings in the first page are:

Executable: /usr/games/fgfs
FG_root: /usr/share/games/FlightGear
FG_Scenery (will be filled automatically):/usr/share/games/FlightGear/Scenery

Hope this can help.

Blue Skies!!

---

### Post by viciouslime on 2007-04-22
I have now compiled the package for x64 since I have moved to 64bit ubuntu.

---

### Post by Rollinco on 2007-05-30
I get a 404 error at the links provided. Any other mirrors of FGrun for Ubuntu??

---

### Post by viciouslime on 2007-05-30
> **Rollinco said:**
> I get a 404 error at the links provided. Any other mirrors of FGrun for Ubuntu??

Will be back up soon.

---

### Post by Rollinco on 2007-05-30
OK, I'll just wait and keep checking back!! Thanks!!8-)

---

### Post by viciouslime on 2007-05-30
> **Rollinco said:**
> OK, I'll just wait and keep checking back!! Thanks!!8-)

Ok, all done, note the updated link :)

---

### Post by viciouslime on 2007-09-10
> **viciouslime said:**
> Ok, all done, note the updated link :)

I'm doing a lot of work on this site at the moment, so I have removed the direct links as it is becoming quite tiresome updating them all the time. The downloads can be found in the "debs" category on my site as linked above :)

---

### Post by orengolan on 2008-03-22
i installed it but i don't know how to run it.
(i have working version of fgfs 1,0)

when a run fgrun in command line i get:
```
fgrun: error while loading shared libraries: libsgprops.so.0: cannot open shared object file: No such file or directory
```

this guy has the same problem:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1576307](http://forum.ubuntu-fr.org/viewtopic.php?pid=1576307)
(i used google translate)

thanks, 
Oren

---

### Post by SamsLembas on 2008-04-24
Same problem here. Running Ubuntu Hardy 64 Bit.

---

### Post by orengolan on 2008-04-26
...and even on my new xubuntu hardy 32 bit (8.04) it shows the 
same error!

---

### Post by Tyche on 2008-04-29
> **orengolan said:**
> i installed it but i don't know how to run it.
(i have working version of fgfs 1,0)

when a run fgrun in command line i get:
```
fgrun: error while loading shared libraries: libsgprops.so.0: cannot open shared object file: No such file or directory
```

this guy has the same problem:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1576307](http://forum.ubuntu-fr.org/viewtopic.php?pid=1576307)
(i used google translate)

thanks, 
Oren

I solved that one by making a link to libsgprops.so.1.0.0.

HOWEVER, then it spit back out at me:  fgrun: error while loading shared libraries: libsgxml.so.0: cannot open shared object file: No such file or directory.  So there's still a problem.  And this one I haven't been able to find what to link to.  It never rains but it pours.  Oh, wait. I'm in Arizona.  It never rains.  :-D

EDIT:  I did discover (by finding a copy on the net as a .deb file and trying to install it) that a later copy exists as part of the Simulator Construction Gear -- shared libraries.  But gdebi doesn't tell me what the later copy is named.

EDIT 2:  OK, I got it to work.  There are a number of the libs that need to be linked to later versions.  As a general rule, one can link to the same name but replace the so.0 with so.1.0.0.

In addition to libsgxml.so.1.0.0, there are also:
 * libsgmisc.so.1.0.0
 * libsgstructure.so.1.0.0
 * libsgdebug.so.1.0.0

Hope this helps.

AAAAAAAAAAAAAAAAAARRRRRRRRRRRRGGGGGGGGGGGGGGGGGGGGGGHHHHHHHHHHHH!!!!!

It didn't help.  Segmentation fault.
OK, NOW what do I do?  :-(

---

### Post by Jengle on 2008-05-02
How did you make the link to the new libs?  What app are you using?  I haven't successfully got fgrun working in Hardy

---

### Post by Tyche on 2008-05-02
> **Jengle said:**
> How did you make the link to the new libs?  What app are you using?  I haven't successfully got fgrun working in Hardy

I haven't gotten it to work yet, either.  I keep getting segfaults.  However, the link command is a part of the basic Linux shell commands.  I'm not trying to put you off, but if you bring up a terminal and type "man ln" (without the quotes) you'll get a lot more information on the command and how to use it.

---

### Post by Jengle on 2008-05-02
> **Tyche said:**
> I haven't gotten it to work yet, either.  I keep getting segfaults.  However, the link command is a part of the basic Linux shell commands.  I'm not trying to put you off, but if you bring up a terminal and type "man ln" (without the quotes) you'll get a lot more information on the command and how to use it.

Thanks for the reply.  I am at the same stumbling block with segment fault.

---

### Post by bipco on 2008-05-10
Hello all - I've had the same negative experience with the debs, and I've been unable to compile it on a new machine with new Hardy install. However, I have a working 32-bit binary I compiled on my old machine with Gutsy. I've posted it up at [http://bipco.org/ubuntu-flightgear/flightgear_fgrun_binary.htm](http://bipco.org/ubuntu-flightgear/flightgear_fgrun_binary.htm)

Feel free to go and get it - only 32-bit I'm afraid and not a deb to install it, just the fgrun binary.

If you haven't got the required libraries you'll need to get them - possibly if you tried installing the viciouslime deb they may be there?

I've backtracked from a Hardy 64-bit install to 32 so I could get the one from the old machine to work - guess I'll wait till Ubuntu 8.10 to try 64 again. Previously I found fltk was the stumbling block to getting fgrun to compile - took me ages to get that to work on the old machine, haven't managed it on the new yet.

Really would save a lot of bother if these were in the Ubuntu repos.

Warren

---

### Post by viciouslime on 2008-05-11
I have tried to fix this issue, but i'm at a bit of a loss... I can no longer get the thing to compile on hardy. I'll try again when I have a bit more time.

I have tried to get this into the repo, but the process by which that is achieved is a very long drawn out one. I am still waiting on a response from over a year ago before I can move forward with it and that's to try and get it in the edgy repos which is obviously no use any more anyway...

---

### Post by jam007 on 2008-06-16
> **viciouslime said:**
> I have tried to fix this issue, but i'm at a bit of a loss... I can no longer get the thing to compile on hardy. I'll try again when I have a bit more time.

Please do! :)
> 
I have tried to get this into the repo, but the process by which that is achieved is a very long drawn out one. I am still waiting on a response from over a year ago before I can move forward with it and that's to try and get it in the edgy repos which is obviously no use any more anyway...
Strange that FGRun isn't there. It should be :(

---

### Post by Applegeek on 2008-06-21
It doesn't look like fgrun wants to work under Hardy-amd64?  I can't get the deb or the compiled version to work, either.

Anyone able to compile fgrun under Hardy64 yet?

---

### Post by bobterri on 2008-07-21
Viciouslime,

Will the fgrun deb work with FlightGear 1.0?

---

### Post by viciouslime on 2008-07-21
I'm afraid not, and I feel it's probably more effort than it's worth to get this to work on Hardy. It's something to do with Hardy sharing a resource that shouldn't be shared, instead there should be two separate copies of it... or something lol. Even having found out what causes it, it was beyond me to fix it.

I'll try and get it going in intrepid, really though, I think the flightgear team should be asked to integrate fgrun, or create something like it. Maybe we should all head over there and suggest it :)

---

### Post by viciouslime on 2008-09-02
I have finally fixed this so that it works in Hardy Heron. At the moment I have only updated the AMD64 deb, but I will build a 32 bit version asap.

---

### Post by jam007 on 2008-09-04
> **viciouslime said:**
> i have now compiled the package for x64 since i have moved to 64bit ubuntu.
thanks!

---

### Post by viciouslime on 2008-09-04
> **jam007 said:**
> thanks!

You're welcome, I've also added the 32bit build now.

---

### Post by Iwanthelp on 2009-01-28
Sorry for reviving an old thread but, I asked on the FlightGear Forums and they pointed me here, and when I click your site's link it just loads a blank page.

---

### Post by Drakkor on 2009-02-22
Yeah, I'd like   to install this,but have no clue,
I'm here: This is the link I get for the Ubuntu install
[http://www.proformatique.org/deb/](http://www.proformatique.org/deb/)
Thanks :p

---

### Post by binbash on 2009-02-23
[http://www.proformatique.org/deb/pool/main/f/flightgear/](http://www.proformatique.org/deb/pool/main/f/flightgear/)

download the deb, and install.If it complains about missing deps, download them or install them via apt-get also.

---

### Post by Drakkor on 2009-02-23
Ok,thanks for the deb file, but   unsatisfied dependency "libopenscenegraph8" , and can't find that in synaptic or
apt-get. I did find libopenscenegraph7, but that won't do it !

---

### Post by gjoellee on 2009-02-23
There might be a different DEB at [www.getdeb.net](www.getdeb.net) (you might need to choose Hardy Heron to find flightgear in the games section). This DEB might include the dependencies or have other mirrors...it might also be the same

---

### Post by konqueror7 on 2009-02-23
i believe flightgear is already in the repos...

---

### Post by binbash on 2009-02-23
> **Drakkor said:**
> Ok,thanks for the deb file, but   unsatisfied dependency "libopenscenegraph8" , and can't find that in synaptic or
apt-get. I did find libopenscenegraph7, but that won't do it !

Dude install missing debs from there : 

[http://www.proformatique.org/deb/pool/main/](http://www.proformatique.org/deb/pool/main/)

Download every deb to a folder and give sudo dpkg -i *.deb

---

### Post by aol_client on 2009-05-07
> **binbash said:**
> Dude install missing debs from there : 

[http://www.proformatique.org/deb/pool/main/](http://www.proformatique.org/deb/pool/main/)

Download every deb to a folder and give sudo dpkg -i *.deb

Thank you so much. This was really helpful.  I was searching around and found this. :popcorn:

---

### Post by Warthaug on 2009-09-19
I am trying to get FGRun to compile from source.  I am slowly working my way through all the dependencies needed to do this, and have run into a problem.  Despite having every OpenSceneGraph entry in synaptic installed (including documentation) I cannot get through the .configure script.  It always ends at this error:

> You *must* have the OpenSceneGraph support library installed on your system
to build the FGFS simulator!

Please see README.OSG for more details.


Also, there is no "readme.osg" in the FGrun directory.

Bryan

---

### Post by KIAaze on 2009-09-20
First thing to do:
```
sudo apt-get build-dep flightgear
```
It installs all necessary dependencies to build flightgear from source.
This should already make things a little bit easier. :)

edit:
Mmh, just did some quick tests and if you're trying to compile the latest source package (FlightGear-1.9.1.tar.gz), you're going to still have some problems. :/
I needed to install "libboost-dev" at first, now it asks me for "SimGear 1.9.0 or newer" which is not in the repos.
So you'll probably have to install "Open Scene Graph" from source.
Did you install "libopenscenegraph-dev" already?

Note: "apt-get build-dep" gets the dependencies that were used to build the flightgear package that is currently in the repositories.

---

### Post by Perfect Storm on 2009-09-20
Both 


Plib
Simgear
Flightgear

Needs to be compiled first.

---

### Post by Warthaug on 2009-09-20
Thanx guys.  I don't think its worth the effort given that I've got JFlightWizzard working...

Bryan

---

### Post by visionary on 2009-09-23
Visit [www.unitedfreeworld.com](www.unitedfreeworld.com) for the latest DEB files for Flightgear,FGRUN and FGCOM. It comes as acomplete package. These latest packages are not found on the official repo tho. 

Enjoy! :)

---

### Post by visionary on 2009-09-23
Visit [www.unitedfreeworld.com](www.unitedfreeworld.com) for the latest DEB files for Flightgear,FGRUN and FGCOM. It comes as complete package. These latest packages are not found on the official repo tho. [www.Unitedfreeworld.com](www.Unitedfreeworld.com) also provides some scenery, livery and SIM model packages which are not found in FLightgear offical repo as well. Seems like an interesting site 

Enjoy! :)

---

### Post by Sealbhach on 2009-09-23
I used the cvs script from here:

[http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu](http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu)

It made the process very easy and simple and it worked without a hitch.

.

---

### Post by Sealbhach on 2009-09-23
> **visionary said:**
> Visit [www.unitedfreeworld.com]("http://www.unitedfreeworld.com") for the latest DEB files for Flightgear,FGRUN and FGCOM. It comes as acomplete package. These latest packages are not found on the official repo tho. 

Enjoy! :)

Nice site buddy, this was something people needed, to get debs for the latest and greatest flightgear.

.

---

### Post by visionary on 2009-09-23
If you need the latest version of Flightgear , FGRUN, FGCOM or other flightgear add ons, just visit [www.unitedfreeworld.com](www.unitedfreeworld.com)  They provide these DEB files which are not found on the offical ubuntu repo. these files seems to work very well...you get a complete package of Flightgear,FGRUn and FGCOM from [www.unitedfreeworld.com](www.unitedfreeworld.com)

Enjoy!

---

### Post by visionary on 2009-09-23
Hope all goes well /...
Enjoy the game!

:)

---

### Post by Perfect Storm on 2009-09-24
Threads merged.

---

