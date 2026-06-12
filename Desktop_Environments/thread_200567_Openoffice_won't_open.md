---
title: "Openoffice won't open"
date: 2006-06-20
forum: Desktop Environments
---

### Post by endfx on 2006-06-20
When I try to open any openoffice application (writer, database, calc, ...)
it tries to open, you it in the task bar, but after 10 seconds it just quits, no error
or anything.

Anybody know why it would be doing this?

---

### Post by bruce89 on 2006-06-20
Run ```
ooffice -writer
``` in a terminal and paste the output here.

---

### Post by ayoli on 2006-06-20
try to run openoffice from a terminal and copy/paste errors if any.

---

### Post by endfx on 2006-06-20
I get this:

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI


I guess that means there is something wrong with my display driver...

---

### Post by hsmith on 2006-07-03
I am having the same problem. When I attempt to start any Openoffice program it simply shows the busy icon for a few seconds and then disappears. I attempted to start openoffice in terminal and got the following error message.

no suitable windowing system found, exiting.

** (process:5090): WARNING **: Unknown error forking main binary / abnormal early exit ...

I'd like to use Openoffice but..................................

Thanks for any help.

---

### Post by mrmcd on 2006-09-25
Same problem here.  Here's the error from running oowriter from the terminal:
** (process:7659): WARNING **: Unknown error forking main binary / abnormal early exit ...


This has happened in ubuntu since I installed dapper drake on the machine.  IMHO, this is a huge issue since office software is one of the most important application types on a computer.  If ubuntu is shipping with this problem happening on multiple machines, I would think this is something Cannonical would want to take care of pretty quick. Does anybody have any ideas about how to fix this?

---

### Post by fatsheep on 2006-09-25
Strange, Open Office works great for me.  Two questions for you guys:

#1: Do you use Gnome or KDE?
#2: 64-bit or 32-bit?

---

### Post by BLTicklemonster on 2006-09-25
CloseOffice.org, yes, horrible thing. I'd take the short route and remove it using synaptic, then reboot, and install it again, and see if that fixes it.

---

### Post by bfriedman on 2006-09-25
ooffice opens ok for me if the display is redirected to
an X session on another machine.

On the local machine (gnome, 32bit) it fails with the 
following api errors as in the post below:

```

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
.
.
.
.
.
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

** (process:20008): WARNING **: Unknown error forking main binary / abnormal early exit ...




```

---

### Post by nmatheis on 2006-09-26
I'm having the same problem with openoffice not opening on dapper.  It shows the openoffice splash, show the busy icon in the taskbar, and then fails to open any and all openoffice programs.  I ran synaptic, searched "openoffice", and marked everything currently installed related to openoffice for reinstallation.  This didn't help.  I'm at work and can't input any terminal data error output from running the ooffice -writer command right now but can do that later if need be.

Nikolaus

---

### Post by bfriedman on 2006-09-29
ooffice opens ok for me if the display is redirected to
an X session on another machine.

On the local machine (gnome, 32bit) it fails with the 
following api errors as in the post below:

```

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
.
.
.
.
.
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

** (process:20008): WARNING **: Unknown error forking main binary / abnormal early exit ...




```

---

### Post by T_W on 2006-09-29
I was seeing a somewhat similar behavior.  OpenOffice would silently fail to start up.  

Running 

```
ooffice -writer
``` 

from the command line  would result in the process existing with **NO output**. 

To debug I ran an strace on OpenOffice via the command 

```
strace ooffice -writer
```

I didn't capture the output, but it looked like it was having a problem opening up a shared library.  I was definitley getting the error:

```
** (process:20008): WARNING **: Unknown error forking main binary / abnormal early exit ...
```

right before termination.

I thought I remembered seeing some of the base shared libraries updated by recent updates so I figured I tried rebooting the box just to make sure the old libaries were completely unloaded.

After rebooting ooffice came up fine.  This may be a solution for some of you.

---

### Post by circuitsurfer on 2006-10-04
Help Open office will not open here is the dump from my ooffice -writer

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
--
--
--
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

I also did an strace but it is really long. Any help is appreciated. 

I am able to open ABI word, and am not having any other display issues, I am assuming that fglrx is something to do with my display driver.

Kinda new to this.

Thanks for any help.

---

### Post by blacklion on 2006-10-26
I also had this problem just after I upgraded to Edgy.  I changed my display driver to "ati" instead of "fglrx" and then I can start openoffice again.

---

### Post by nick holme on 2006-11-19
I had this problem after upgrading to an ATI card. I managed to fix it by replacing the libGl.so.1.2 in /usr/lib. Apparently ATI overwrites some GL libs. I worked OK for around 2 months and then a couple of days ago, the same thing happened again. Have a look at [http://www.minds.may.ie/~dez/serendipity/index.php?/archives/76-OpenOffice-Not-Working-on-Ubuntu-Dapper-6.06.html](http://www.minds.may.ie/~dez/serendipity/index.php?/archives/76-OpenOffice-Not-Working-on-Ubuntu-Dapper-6.06.html)

I have re-replaced libGl.so.1.2 with the one from this site and openoffice now works again. 

I must say that this sort of thing is coming close to putting me off Linux.

Nick

---

### Post by Amaroq on 2007-04-08
I may have stumbled upon the fix for this bug.

[http://ubuntuforums.org/showthread.php?p=2423551#post2423551](http://ubuntuforums.org/showthread.php?p=2423551#post2423551)

---

### Post by benner on 2007-04-10
tried it.  didn't work.  another post suggested that if i changed the theme to something other than 'crystal' that it would fix the problem.  it didn't.  i have spent countless hours screwing around trying to get openoffice to work without luck.  the best i have discovered is that when i switch vdeo drivers to the ati one, it works.  when i use fglrx, it doesn't.  unfortunately, the ati one doesn't support the 1440x900 resolution that my monitor wants.  everything turns green and horrible.  the fglrx driver works great--except that it conflicts with openoffice.  
i tried to download the new libGL and i couldn't get it.  i've been clicking on it for ages...

---

### Post by koshari on 2007-04-10
this is definately the dreaded radeon not supporting <9250 bug..

The latest ATI drivers are broken with r200 (9250) cards

```
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS 
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
```

to use the older driver download this file; right click on the link using firefox and "save as" libGL.so.1.2

```
http://www.ground-impact.com/libGL.so.1.2
```

and overwrite the newer driver

```
sudo cp /home/holto/libGL.so.1.2 /usr/lib/libGL.so.1.2
```

also the next time you upgrade the ati binary drivers the problem will return, and you will have to copy the older binary over again.

---

