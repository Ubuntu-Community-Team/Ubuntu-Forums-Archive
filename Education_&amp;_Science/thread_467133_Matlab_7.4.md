---
title: "Matlab 7.4"
date: 2007-06-07
forum: Education &amp; Science
---

### Post by trinitry on 2007-06-07
hello all, after many tries i managed to install it:p, but (there is always a but) when i run simulink it crashes and i got a Segmentation fault (core dumped) output to the terminal.:(
Any ideas?????
Thanks

---

### Post by daschmidty on 2007-06-07
i think there are google posts about this..i got it working once. I'll try to find it, but it has to do with simulink using java JRE and it links to the wrong directory for java6 in ubuntu, you have to edit the launch script, but i have since reinstalled and i don't remember the details.

---

### Post by MaximusTG on 2007-06-07
You need to edit the matlab file, in the bin directory, and add the following lines:

export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/ 

(You need to have java 6 installed ( sudo apt-get install sun-java6-jre))

The first line (AWT_TOOLKIT etc.) is only needed if you run compiz or beryl, without it, the interfaces appears completely grey.

Good luck!

---

### Post by trinitry on 2007-06-08
Maximus u r the man!! thanks, it works !!!
chao:p

---

### Post by TasKiNG on 2007-07-09
Thanks Maximus, Fix worked a treat for my matlab 2007a :)

---

### Post by tikey on 2007-07-15
I had the same problem than trinitry so I checked if java is installed on my machine and added the line with the java in the matlab start-script (I added it below all the other export-lines.

Now when I try to start matlab from konsole I get the following error-message "Failed to start the Desktop: Failure loading desktop class"
Does anyone have an idea how I could fix this?

Thanks!

Edit: Some more information.

If I start matlab with the -nodesktop option I get the message 
"Couldn't load Look and Feel: java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: undefined symbol: sunHints_INTVAL_STROKE_PURE"
I then can type commands in the shell where I started matlab. Unfortunately this is not helpfull for me as I have to use simulink and I need the GUI.

---

### Post by nszabolcs on 2007-07-18
> **tikey said:**
> 
If I start matlab with the -nodesktop option I get the message 
"Couldn't load Look and Feel: java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: undefined symbol: sunHints_INTVAL_STROKE_PURE"
I then can type commands in the shell where I started matlab. Unfortunately this is not helpfull for me as I have to use simulink and I need the GUI.

if you want an absolute javaless matlab environment then use
matlab -nodisplay

(unfortunately matlab has poor readline support so it's unusable)

try ubuntu's sun-java
try the MTOOLKIT and MATLAB_JAVA environment variable fix posted above
if it does not help then you have a broken install i guess

---

### Post by tikey on 2007-07-18
The problem is that I really need simulink and there is no way to use that without a gui.

I already tried sun-java with the fix posted above. Before I did that I always got a segmentation fault (core dumped) when I tried to start matlab. So there must be something else. If anyone has some more ideas I would really appreciate it!

---

### Post by tikey on 2007-07-24
Does no one have an idea? It would be very helpful for me!
thanks

---

### Post by jmgc on 2007-07-25
Hi tikey,

Are you using Beryl? I had the same problem in Ubuntu 7.04. One possible workaround is the following:

1- Start Matlab from the terminal as usual (without having exported nor the AWT_TOOLKIT either the  MATLAB_JAVA variable).

2- Turn off the Beryl manager and use the standard one (like Metacity). At this moment the toolbar will reapear.

3- Switch again to Beryl if you want. The toolbar will be still visible. But I do not recommend it because you may still have redrawing problems. For example, if you want to maximize a window containing an image, the image will probably keep the same size as for the previous window size. Using other managers it may not happen.

Hope it works

---

### Post by tikey on 2007-07-26
I don't think that I'm using Beryl. At least I didn't install s/th like this if it is not standard in Kubuntu. (I actually don't even know exactly what Beryl is.) I will check if there is s/th called Beryl installed on my system as soon as I get home.

---

### Post by tikey on 2007-07-27
So I checked in the adapt_manager. I'm not using Beryl. It is not installed. When I type "window manager" in the search field I only get 3 installed packages:
- kwin
- libmetacity0
- metacity-common

Do I have to install some other window manager in order to get Matlab to run?

thanks

---

### Post by 1Slater1 on 2007-07-28
> **tikey said:**
> I had the same problem than trinitry so I checked if java is installed on my machine and added the line with the java in the matlab start-script (I added it below all the other export-lines.

Now when I try to start matlab from konsole I get the following error-message "Failed to start the Desktop: Failure loading desktop class"
Does anyone have an idea how I could fix this?

Thanks!

Edit: Some more information.

If I start matlab with the -nodesktop option I get the message 
"Couldn't load Look and Feel: java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so: undefined symbol: sunHints_INTVAL_STROKE_PURE"
I then can type commands in the shell where I started matlab. Unfortunately this is not helpfull for me as I have to use simulink and I need the GUI.

Mate the solution presented by MaximusTG works, you simply have to add those lines first before the 
beginning of the code (right after the blue text which is remarks). Don't mean to offend you if you already tried that but, sometimes we all miss the most basic stuff! Hope that helps Tikey.

---

### Post by tikey on 2007-07-28
Thank you so much! How stupid from me. 

I hadn't tried different places for the lines before. Even if I would have, I would never feel offended if someone wants to help me. Always remember:
- My screen is black, it doesn't work anymore.
- Did you turn it on?
- OF COURSE!
- Can you turn it off?
- Now it works...

Again: Thank you so much. Now I can sleep again.

---

### Post by Icarosaurus on 2007-07-29
Works with Matlab 7.2 (R2006a) too.
Thank you.

---

### Post by bjornTFN on 2007-08-09
Just a note back to the Simulink crash because of java - I had the same problem and followed the steps here (exporting stuff), and it wasn't helping - I found out that I needed to move the export lines to the top of the Matlab file, just after all the usage stuff (the matlab file is in the matlab/bin folder for those who can't find it). Its now working. I also separately installed the sun-java6-fonts package.
(apologies, I'm a bit of a noob here and this is aimed at helping others like me :-) )

---

### Post by spectatorion on 2007-10-08
> **MaximusTG said:**
> You need to edit the matlab file, in the bin directory, and add the following lines:

export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/ 

(You need to have java 6 installed ( sudo apt-get install sun-java6-jre))

The first line (AWT_TOOLKIT etc.) is only needed if you run compiz or beryl, without it, the interfaces appears completely grey.

Good luck!

this is amazing! i'm so happy it works now.  I was using compiz and getting the grey toolbars and windows you were talking about, searching everywhere for a fix.

i have a couple refinements, however:
1. on my system, there is a symlink to /usr/lib/jvm/java-6-sun-1.6.0.00 which is located at /usr/lib/jvm/java-6-sun
my guess is that if i ever upgrade to a new version of java6, this symlink will be updated so that it is better to use the symlink in the script so i don't have to update often.  i.e., it might be better to make the second line:
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ 
```
if your system has the symlink like mine.

2. completely commenting out the second line works just fine and in fact causes some font warnings to go away (when starting matlab from the terminal).  you may have alluded to this in your post, but any clue why this might be?  i guess i don't really care as long as it works, but if things get screwey again with a java upgrade or some such, i'd like to know how to fix it on my own.

THANKS AGAIN!!

---

### Post by cherry316316 on 2007-10-30
> **MaximusTG said:**
> You need to edit the matlab file, in the bin directory, and add the following lines:

export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/ 

(You need to have java 6 installed ( sudo apt-get install sun-java6-jre))

The first line (AWT_TOOLKIT etc.) is only needed if you run compiz or beryl, without it, the interfaces appears completely grey.

Good luck!

thanks Maxumus, you solved my unsolvable problem so easily.
:)

---

### Post by cherry316316 on 2007-10-30
i got this error when i run from command prompt 
```

Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct


```

then i commented the 1st line of maximus part, as suggested above and it worked fine.


now only problem is I m not able to run Matlab from desktop, it tries to launch , but then crashes :(
any one knows why ?

I was having a similar problem in windows and my univ admin group suggested this part 


```
 IMPORTANT INSTALLATION NOTE:

There is a known installation error which is currently under investigation. The installation will complete successfuly, however Matlab will NOT start. The current workaround is to set an environment variable that will bypass the error. Please try the following to start MATLAB:

   1. Go to the Start menu to Control Panel.
   2. Double click on "System" and go to the Advanced tab (for Vista go to "System and Maintenance" to "System" to "Advanced System Settings".
   3. Click the Environment Variables button.
   4. Click "New" under either option (System or User variables) to create a new variable. The variable name will be MATLAB_RESERVE_LO. The variable value will be the number 0 (zero). Press OK to save the changes.

EXPLANATION:

Setting MATLAB_RESERVE_LO=0 tells MATLAB to bypass the functionality introduced in R2007b (for Windows only) that tries to reserve the largest available contiguous space for MATLAB arrays. This process guarantees that at least 256MB is left available for use by Java for the Heap and PermGen spaces. It appears that Windows is either loading a DLL or doing a malloc somewhere in this 256MB space, so that when Java tries to reserve the Heap and PermGen address space, it fails, since both the Heap and PermGen spaces must be contiguous. If MATLAB_RESERVE_LO is set to 0, the reserve is for a fixed amount of space, not the largest available space.

Once this variable is set, try starting MATLAB again. 
```

any idea , what to do in linux , i am new to linux

---

### Post by syxbit on 2007-12-04
spec!
great improvement. I noticed the same thing, as i had java 1.6.0.3
just in case anyone else has the same problems
i installed 2007b (7.5) x64, and i had to just add the line
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
and not that first line, else it wouldn't boot.

you don't know how happy i am!
it's a little ironic that the only time i ever booted into windows was to program......
now i'm windows free (except gaming :) )

---

### Post by Blutack on 2007-12-05
Linux free...?
Does anybody else have a problem with a hideous simulink library?
It doesn't respond to double clicks, meaning I have to manually select each block category and then press enter to view.  As you can imagine this is getting a little annoying.  Is this normal?  The rest of Matlab is fine, I've got compiz with the java6 fix.
Could someone at least confirm whether this is normal or not?  It's making the program VERY difficult to use.
EDIT: Disabling compiz allows double click on the simulink library.  It also speeds it up massively.  However, it is still malformed compared to the windows version, although I think this may be intentional.
Screenshot attached.

---

### Post by cherry316316 on 2007-12-05
> **Blutack said:**
> Linux free...?
Does anybody else have a problem with a hideous simulink library?
It doesn't respond to double clicks, meaning I have to manually select each block category and then press enter to view.  As you can imagine this is getting a little annoying.  Is this normal?  The rest of Matlab is fine, I've got compiz with the java6 fix.
Could someone at least confirm whether this is normal or not?  It's making the program VERY difficult to use.
EDIT: Disabling compiz allows double click on the simulink library.  It also speeds it up massively.  However, it is still malformed compared to the windows version, although I think this may be intentional.
Screenshot attached.

I have a similar problem , not in simulink , but in matlab, when i want to open a directory or navigate to a file or when i use command "uigetfile" or "uigetdirectory" etc, then i have to click so many times before it open a directory and then i have to struggle with the sub-directory till the time I reach to the target directory or file, most of the time it tries to rename the directory.
so the best way i use is to put the address directory in the box , rather then navigating to the target.
 :(

---

### Post by syxbit on 2007-12-05
sorry, meant windows free :)
fixed it

---

### Post by Blutack on 2007-12-05
I know you did... :D
So is this crappy tcl/whatever the default Simulink interface?  For the love of god, I'd prefer native swing!  Why isn't it like the rest of Matlab...still, got the model done in the end.  Thanks guys!
(Apologies to any offense caused by the screenshot but I couldn't be bothered to gimp it out and I guess we are mostly adults here).

---

### Post by syxbit on 2007-12-05
just an FYI, matlab is single-threaded unless you tell it otherwise in Preferences-General-Multithreaded

---

### Post by syxbit on 2007-12-07
anyone else noticed a problem printing.
it seems that everything BUT printing works (AFAICT)
removing compiz, and the java line removes the error, but no printers are found.

---

### Post by ozziem on 2007-12-08
> **syxbit said:**
> anyone else noticed a problem printing.

Same problem here with printing. ditto on everything else working fine ...

Anyone have ideas on how to fix printing?

---

### Post by Vovan_01 on 2007-12-26
Can you tell exact place where to add "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/" line in matlab file (matlab74/bin/matlab). I tried to add it at the end but nothing changed,  if i add in the beginning i get an warning:
Warning: Cannot locate Java Runtime Environment (JRE) . . .

---

### Post by cherry316316 on 2007-12-26
> **Vovan_01 said:**
> Can you tell exact place where to add "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/" line in matlab file (matlab74/bin/matlab). I tried to add it at the end but nothing changed,  if i add in the beginning i get an warning:
Warning: Cannot locate Java Runtime Environment (JRE) . . .

use this command in /usr/bin/matlab
at the beginning 
```
 export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/  
```

this is because , if you update your java, then your java is no longer java1.0.0.xx it will be some new number , and every time you update your java , you will have to come to matlab file and change the line,
by using this line, you will avoid the conflict of java update
also goto folder 
"/usr/lib/jvm/" and see  which all types of java you have , just to have a rough idea for yourself.
good luck

---

### Post by spectatorion on 2008-01-02
> **Vovan_01 said:**
> Can you tell exact place where to add "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/" line in matlab file (matlab74/bin/matlab). I tried to add it at the end but nothing changed,  if i add in the beginning i get an warning:
Warning: Cannot locate Java Runtime Environment (JRE) . . .

you should put it at the very beginning (or equivalently, after the header, which is the initial section where each line begins with a #).  it sounds like you might not have java6 installed.  try
```
sudo apt-get install sun-java6-jre
```
then re-run matlab (with the extra line at the top).

---

### Post by ocarinahuff on 2008-01-08
Thanks MaximusTG
That "export AWT_TOOLKIT=MToolkit" thing worked.  Didn't need the java line  though.

I'm running Ubuntu Gutsy 7.10 on a Dell Vostro 1500, with uber-cool Compiz on

Rock on Linux!

---

### Post by darrenleeweber on 2008-01-11
I use

matlab -nojvm -nosplash

to avoid java on command line prompts and within emacs (configure matlab-shell command).  I guess this would kill simulink and other matlab stuff that relies on the GUI.

---

### Post by AeroGT3 on 2008-04-27
> **cherry316316 said:**
> use this command in /usr/bin/matlab
at the beginning 
```
 export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/  
```

this is because , if you update your java, then your java is no longer java1.0.0.xx it will be some new number , and every time you update your java , you will have to come to matlab file and change the line,
by using this line, you will avoid the conflict of java update
also goto folder 
"/usr/lib/jvm/" and see  which all types of java you have , just to have a rough idea for yourself.
good luck

This worked perfect for me! :guitar:

---

### Post by kakila on 2008-05-20
Hi Guy,
Thank you very much for all the solutions.
Apparently everything was working until i try to use the publish() command.
Then Matlab crashes.

I still have this warnings when I start matlab
```
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct

```

Here is the file dumped
```

------------------------------------------------------------------------
       Segmentation violation detected at Tue May 20 14:50:37 2008
------------------------------------------------------------------------

Configuration:
  MATLAB Version:   7.0.0.19901 (R14)
  Operating System: Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
  Window System:    The X.Org Foundation (10300000), display :0.0
  Current Visual:   0x21 (class 4, depth 24)
  Processor ID:     x86 Family 6 Model 15 Stepping 11, GenuineIntel
  Virtual Machine:  Java 1.6.0_03 with Sun Microsystems Inc. Java HotSpot(TM) Client VM
    (mixed mode, sharing)
  Default Charset:  UTF-8

Register State:
  eax = 00000001   ebx = b7bf7a00
  ecx = 68664d38   edx = b7c895f5
  esi = bfb80944   edi = bfb82190
  ebp = bfb82168   esp = bfb82120
  eip = b7a27d3b   flg = 00210296

Stack Trace:
  [0] libmwm_interpreter.so:Mfun_call_context::~Mfun_call_context()(0xbfb82190, 
0, 0x08815f50, 0xb7a266a4) + 919 bytes
  [1] libmwm_interpreter.so:inWordsj(2, 0xbfb82b70, 1, 0xbfb82c00) + 683 bytes
  [2] libmwm_interpreter.so:Mfh_mp::dispatch_file(_mdUnknown_workspace*, int, mx
Array_tag**, int, mxArray_tag**)(0x08815f50, 0, 2, 0xbfb82b70) + 398 bytes
  [3] libmwm_interpreter.so:Mfh_mp::dispatch_file(int, mxArray_tag**, int, mxArr
ay_tag**)(0x08815f50, 2, 0xbfb82b70, 1) + 32 bytes
  [4] libmwm_dispatcher.so:Mfh_file::dispatch_fh(int, mxArray_tag**, int, mxArra
y_tag**)(0x08815f50, 2, 0xbfb82b70, 1) + 270 bytes
  [5] libmwm_interpreter.so:ResolverFunctionDesc::CallFunction(int, mxArray_tag*
*, int, mxArray_tag**)(0xbfb82f24, 2, 0xbfb82b70, 1) + 267 bytes
  [6] libmwm_interpreter.so:Resolver::CallMFunction(int, int, _m_operand*, m_ope
rand_storage*, int, _m_operand*, m_operand_storage*, int*)(0xbfb82d00, 2, 2, 0xb
52b6a30) + 1010 bytes
  [7] libmwm_interpreter.so:inResolveMFunctionCall(_m_function_desc*, int, int, 
_m_operand*, m_operand_storage*, int, _m_operand*, m_operand_storage*, int*, inM
arshalType*, unsigned, int, unsigned*, int)(0x085ef9c0, 2, 2, 0xb52b6a30) + 241 
bytes
  [8] libmwm_interpreter.so:accelMFunctionCall(_accelOp*, _accelOp**, _accelByte
code*, int*, inMarshalType*)(0x08801be0, 0xbfb8358c, 0x0824fdb0, 0xbfb8352c) + 9
0 bytes
  [9] libmwm_interpreter.so:.L1370(0x0824fdb0, 0xbfb8378c, 0xbfb837e8, 0xb7a021f
1) + 95 bytes
  [10] libmwm_interpreter.so:inExecuteHotSegment(0xbfb83860, 0xbfb83844, 0xbfb83
848 ", 0) + 1167 bytes
  [11] libmwm_interpreter.so:inExecuteMFunctionOrScript(Mfh_mp*, bool)(0x088158e
0, 0, 0x088158e0, 1) + 463 bytes
  [12] libmwm_interpreter.so:inWordsj(2, 0xbfb842c0, 1, 0xbfb84350) + 338 bytes
  [13] libmwm_interpreter.so:Mfh_mp::dispatch_file(_mdUnknown_workspace*, int, m
xArray_tag**, int, mxArray_tag**)(0x088158e0, 0, 2, 0xbfb842c0) + 398 bytes
  [14] libmwm_interpreter.so:Mfh_mp::dispatch_file(int, mxArray_tag**, int, mxAr
ray_tag**)(0x088158e0, 2, 0xbfb842c0, 1) + 32 bytes
  [15] libmwm_dispatcher.so:Mfh_file::dispatch_fh(int, mxArray_tag**, int, mxArr
ay_tag**)(0x088158e0, 2, 0xbfb842c0, 1) + 270 bytes
  [16] libmwm_interpreter.so:ResolverFunctionDesc::CallFunction(int, mxArray_tag
**, int, mxArray_tag**)(0xbfb84674, 2, 0xbfb842c0, 1) + 267 bytes
  [17] libmwm_interpreter.so:Resolver::CallMFunction(int, int, _m_operand*, m_op
erand_storage*, int, _m_operand*, m_operand_storage*, int*)(0xbfb84450, 2, 2, 0x
b52b66b0) + 1010 bytes
  [18] libmwm_interpreter.so:inResolveMFunctionCall(_m_function_desc*, int, int,
 _m_operand*, m_operand_storage*, int, _m_operand*, m_operand_storage*, int*, inMarshalType*, unsigned, int, unsigned*, int)(0x085edf80, 2, 2, 0xb52b66b0) + 241
 bytes
  [19] libmwm_interpreter.so:accelMFunctionCall(_accelOp*, _accelOp**, _accelByt
ecode*, int*, inMarshalType*)(0x08818fb0, 0xbfb84cdc, 0x0824fda0, 0xbfb84c7c) + 
90 bytes
  [20] libmwm_interpreter.so:.L1370(0x0824fda0, 0xbfb84edc, 0xbfb84f38, 0xb7a021
f1) + 95 bytes
  [21] libmwm_interpreter.so:inExecuteHotSegment(0xbfb85050, 0xbfb850bc, 0xbfb85
03c, 0xb7b93960) + 1167 bytes
  [22] libmwm_interpreter.so:.L611(1, 779, 27, 0) + 221 bytes
  [23] libmwm_interpreter.so:inInterPcodeSJ(inDebugCheck, int, int, opcodes, inP
codeNest_tag*)(1, 779, 22, 0) + 300 bytes
  [24] libmwm_interpreter.so:inExecuteMFunctionOrScript(Mfh_mp*, bool)(0x087f5b6
0, 0, 0x087f5b60, 2) + 604 bytes
  [25] libmwm_interpreter.so:inWordsj(2, 0xbfb85d40, 1, 0xbfb85dd0) + 338 bytes
  [26] libmwm_interpreter.so:Mfh_mp::dispatch_file(_mdUnknown_workspace*, int, m
xArray_tag**, int, mxArray_tag**)(0x087f5b60, 0, 2, 0xbfb85d40) + 398 bytes
  [27] libmwm_interpreter.so:Mfh_mp::dispatch_file(int, mxArray_tag**, int, mxAr
ray_tag**)(0x087f5b60, 2, 0xbfb85d40, 1) + 32 bytes
  [28] libmwm_dispatcher.so:Mfh_file::dispatch_fh(int, mxArray_tag**, int, mxArr
ay_tag**)(0x087f5b60, 2, 0xbfb85d40, 1) + 270 bytes
  [29] libmwm_interpreter.so:ResolverFunctionDesc::CallFunction(int, mxArray_tag
**, int, mxArray_tag**)(0xbfb860f4, 2, 0xbfb85d40, 1) + 267 bytes
  [30] libmwm_interpreter.so:Resolver::CallMFunction(int, int, _m_operand*, m_op
erand_storage*, int, _m_operand*, m_operand_storage*, int*)(0xbfb85ed0, 2, 2, 0x
b52b6bf0) + 1010 bytes
  [31] libmwm_interpreter.so:inResolveMFunctionCall(_m_function_desc*, int, int,
 _m_operand*, m_operand_storage*, int, _m_operand*, m_operand_storage*, int*, in
MarshalType*, unsigned, int, unsigned*, int)(0x085f06e0, 2, 2, 0xb52b6bf0) + 241
 bytes
  [32] libmwm_interpreter.so:accelMFunctionCall(_accelOp*, _accelOp**, _accelByt
ecode*, int*, inMarshalType*)(0x08812d40, 0xbfb8675c, 0x0824fd00, 0xbfb866fc) + 
90 bytes
  [33] libmwm_interpreter.so:.L1370(0x0824fd00, 0xbfb8695c, 0xbfb869b8, 0xb7a021
f1) + 95 bytes
  [34] libmwm_interpreter.so:inExecuteHotSegment(0xbfb86ad0, 0xbfb86b3c, 0xbfb86
abc, 0xb7b93960) + 1167 bytes
  [35] libmwm_interpreter.so:.L611(1, 1162, 110, 0) + 221 bytes
  [36] libmwm_interpreter.so:inInterPcodeSJ(inDebugCheck, int, int, opcodes, inP
codeNest_tag*)(1, 1162, 55, 0) + 300 bytes
  [37] libmwm_interpreter.so:inExecuteMFunctionOrScript(Mfh_mp*, bool)(0x08796b8
0, 0, 0x08796b80, 1) + 604 bytes
  [38] libmwm_interpreter.so:inWordsj(0, 0x08797094, 1, 0x08797074) + 338 bytes
  [39] libmwm_interpreter.so:Mfh_mp::dispatch_file(_mdUnknown_workspace*, int, m
xArray_tag**, int, mxArray_tag**)(0x08796b80, 0, 0, 0x08797094) + 398 bytes
  [40] libmwm_interpreter.so:Mfh_mp::dispatch_file(int, mxArray_tag**, int, mxAr
ray_tag**)(0x08796b80, 0, 0x08797094, 1) + 32 bytes
  [41] libmwm_dispatcher.so:Mfh_file::dispatch_fh(int, mxArray_tag**, int, mxArr
ay_tag**)(0x08796b80, 0, 0x08797094, 1) + 270 bytes
  [42] libmwm_interpreter.so:inCallFcnWithTrap(0, 0x08797094, 1, 0x08797074) + 259 bytes
  [43] libmwjmi_mi.so:FEvalIqmPreFcn(0x08797010 " 7&#1399; 7&#1399;", 0x08797010 " 7&#1399; 7&#1399;", 0
xbfb87178, 0xb7ce47d5) + 343 bytes
  [44] libmwbridge.so:mnIqmDequeue(int)(0xffffffff, 0x087970c0, 4096, 0x0808b1cc
) + 1458 bytes
  [45] libmwbridge.so:unixIoReadLine(int, _IO_FILE*, char*, char*, int, bool*)(2
55, 0xb7876440, 0x08508020, 0x08508020) + 442 bytes
  [46] libmwbridge.so:mnGetFullLine(char**, unsigned*, unsigned*, int)(0xbfb872a
4, 0xbfb872a8, 0xbfb872ac, 255) + 83 bytes
  [47] libmwbridge.so:mnGetCommandLineBuffer(255, 0xb7d4eb08, 0xbfb8b468, 0xb7ce
ad5f) + 148 bytes
  [48] libmwbridge.so:mnParser(0xb7cc0e8b "@@@", 0xb7cc0f7b "mnParser", 1, 0) + 
436 bytes
  [49] libmwmcr.so:mcrInstance::mnParser()(0x0809e228, 0, 0xbfb8d7a8, 0x0804a90e
) + 96 bytes
  [50] MATLAB:mcrMain(int, char**)(1, 0xbfb8d854 ", 0xbfb8d7c8, 0xb775d7b0) + 30
8 bytes
  [51] MATLAB:main(1, 0xbfb8d854 ", 0xbfb8d85c, 0xb7f1c820 ") + 23 bytes
  [52] libc.so.6:__libc_start_main~(0x0804a7d0, 1, 0xbfb8d854 ", 0x0804a3e4) + 2
24 bytes


Segmentation violation occurred within signal handler.
Unable to complete stack trace (stack was probably corrupted)



```

Thanks!!

---

### Post by tmain on 2008-08-12
i have same problem like above post. there it seems a bug at matlab-linux, not the jvm or anything else

some of the guys says "now it works perfect" but try type:

>>demos

and select one of the demos and than click the "Run this Demo" top corner on frame.

i try these and unluckily it sometimes worked sometimes not. it's so weird

Another problem is; if there is a problem using matlab on linux(lots of bugs) one can working on comprehensive works (not simple jobs like matrix manipulation) would be deal with these errors and presumably driving crazy.

i prefer using matlab linux other other platforms because of system accessibility (i want to integrate matlab with other app) but it seems for the present out-of-season

---

### Post by ecedinesh on 2008-09-02
> **daschmidty said:**
> i think there are google posts about this..i got it working once. I'll try to find it, but it has to do with simulink using java JRE and it links to the wrong directory for java6 in ubuntu, you have to edit the launch script, but i have since reinstalled and i don't remember the details.
hello friends i want to download full verget it pa

---

### Post by myquidproquo on 2008-10-18
Hi!

I'm using Matlab 2008. The export MATLAB_JAVA worked well to fix simulink for me but it's still better to run without compiz.

I am using "metacity --replace &" in the matlab script file. Is there any way to run compiz automatically after closing matlab?

---

### Post by myquidproquo on 2008-10-18
Solved. Sorry,it's easy just make a script to start matlab.

---

### Post by alan888 on 2008-12-17
Hi:

I had installed MATLAB 2007a in my Ubuntu because I need to use the library for write .mat files.

I make a file in /etc/ld.so.conf.d/ directory, matlab.conf with /usr/local/matlab2007a/bin/glnx86 inside.

When I run ldconfig a lot of messages appear. Somthing like this (spanish version of ubuntu):

/sbin/ldconfig.real: /usr/local/matlab2007a/bin/glnx86/libmwdservices.so.csf no es un archivo ELF - los bytes mÃ¡gicos del principio son incorrectos.

What can I do for solve this "problem", is a problem? I don't like to see it.

Thanks

---

