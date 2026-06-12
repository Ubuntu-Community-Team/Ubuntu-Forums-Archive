---
title: "MATLAB plots + LaTeX"
date: 2008-06-04
forum: Education &amp; Science
---

### Post by tgrimley on 2008-06-04
Having some issues getting \phi and all the other greek letters to show up properly in Matlab under Ubuntu 8.04

You can see in the screenshot when I do

```
>> xlabel('$\tilde{\phi}_{C}$','FontSize',20,'Interpreter','latex') 
```

Instead of \phi it shows the A with an accent.  None of the others work.  Works fine when I compile using rubber.  Anyone have any idea why it's screwy?

```

>> ver
-------------------------------------------------------------------------------------
MATLAB Version 7.4.0.336 (R2007a)
MATLAB License Number: 283171
Operating System: Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Java VM Version: Java 1.6.0_06 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode, sharing
-------------------------------------------------------------------------------------
MATLAB                                                Version 7.4        (R2007a)
Simulink                                              Version 6.6        (R2007a)
Control System Toolbox                                Version 8.0        (R2007a)
Optimization Toolbox                                  Version 3.1.1      (R2007a)
Signal Processing Toolbox                             Version 6.7        (R2007a)
Statistics Toolbox                                    Version 6.0        (R2007a)
Symbolic Math Toolbox                                 Version 3.2        (R2007a)

Trademarks
------------------
MATLAB, Simulink, Stateflow, Handle Graphics, Real-Time Workshop, and xPC
TargetBox are registered trademarks and SimBiology, SimEvents, and
SimHydraulics are trademarks of The MathWorks, Inc. Other product or
brand names are trademarks or registered trademarks of their respective
holders. 

```

---

### Post by ppm on 2008-06-05
I have noticed the same problem. As a partial solution, you can use [FONT="Courier New"]tex[/FONT] as [FONT="Courier New"]Interpreter[/FONT]. However, you can't get any greek letters with *italic* style. :(

I hope someone will post a better solution...

---

### Post by Frenske on 2008-06-06
I had the same problem running on Windows. As I recall it when you changed it to the correct way to write it in the figure it was okay.

---

### Post by tgrimley on 2008-06-06
Frenske, not sure what you mean by that..

---

### Post by hugmenot on 2008-06-07
Try to embed the string in outer {} braces.

---

### Post by ahmatti on 2008-06-09
I think what you need is LaPrint function from Matlab file exchange. 

[http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file](http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file)

Description:

 	LaPrint is a MATLAB function to print MATLAB graphics for inclusion in LaTeX documents. LaPrint creates an eps-file and a tex-file. The tex-file contains the annotation of the figure such as titles, labels and texts. The eps-file contains the non-text part of the figure and is called by the tex-file.

The main advantage of using LaPrint is that the annotation can be neatly (e.g., including math mode and fancy font constructs) set within LaTeX. LaPrint can be used from the command line or via a graphical user interface (GUI).

---

### Post by jianboli on 2009-11-11
I am not sure if you still have this problem. In my case, I originally have this problem, but I find that install the fonts located at
$MATLAB/sys/fonts/ttf/cm/* 
solves it.

To do that
just using the following commands:

```
sudo ln -s $MATLAB/sys/fonts/ttf/cm/ /usr/share/fonts/
sudo fc-cache -f -v
```Of course, you need to replace the $MATLAB with the path of your matlab root folder.
Hope this can help.:)

---

### Post by ahmatti on 2009-11-12
You could also use Matplotlib to get better Latex output:

[http://www.scipy.org/Cookbook/Matplotlib/UsingTex](http://www.scipy.org/Cookbook/Matplotlib/UsingTex)
[http://www.scipy.org/Cookbook/Matplotlib/LaTeX_Examples](http://www.scipy.org/Cookbook/Matplotlib/LaTeX_Examples)

---

### Post by ezander on 2011-08-03
@ahmatti Sure, dumping matlab into the trash and taking a descent open source alternative like python+scipy+matplotlib solves a lot of problems, but I think not those of the OP ;-)

Neither mine, as I have the same problems, and as I want to get my thesis finished in a few days, I can't afford to rewrite some thousands of lines of matlab in python :-(

---

### Post by ezander on 2011-08-04
Ok, I haven't fixed the problem, but I've been able to find out about some things that are going on under the hood in matlab and may help to really track down the problem instead of just curing the symptoms.

So, if you specify text( ..., 'Interpreter', 'latex') matlab calls the function 'tex.m' in folder '$MATLABROOT/toolbox/matlab/graphics/' (from somewhere deep inside the UI stuff). This in turn calls 'texmex.mexglx' in the subfolder 'private'. texmex seems to be a full latex compiler compiled as a mex file, that can either write a dvi file, or just return the bytes of the dvi file in a uint8 array. Usually it just returns the byte array, but if you set a breakpoint at the correct line in 'tex.m', which looks something like 

```
[dvi,loginfo,err] = localCallTeXParser(tstr, doinitex, verbose, dofileio);
```    

you can change 'dofileio' to 'true' and look at the dvi file that is then created. If I do that and view the dvi file with xdvi (or whatever viewer you have at hand), it looks perfectly ok to me. 

So, I wanted to know, what is happening with the dvi byte array created. Therefore I parsed the byte array using the dvi file specs (see e.g. [http://www-users.math.umd.edu/~asnowden/comp-cont/dvi.html](http://www-users.math.umd.edu/~asnowden/comp-cont/dvi.html)) and changed all 'set_char_i opcodes' to render instead the character 'X' (Note: to do that, you have to copy the matlab stuff from '$MATLABROOT/toolbox/matlab/graphics' to some directory, where you can safely modify them). Indeed, matlab then displayed all X's at the locations where they should be (I used the standard integral example from the documentation), proving that matlab indeed used the same correct dvi file/byte array. 

The question for me is now, where is matlab interpreting and rendering the dvi file/bytes, and unsuccessfully tries to load the fonts. I haven't found that location yet (somehow I get no call stack, when I set the breakpoint in tex.m), but I think, if I could find that function, I could really get at the source of the error. Maybe somebody wants to join in?

---

### Post by ezander on 2011-08-04
Ok, I found a hack that works by intercepting the generation of the dvi files. It's not perfect but it works. First, you need to move the files 'tex.m' from '$MATLABROOT/toolbox/matlab/graphics' and the mex files from the subfolder 'private' to some local folder that is on your matlab path, and that you can modify. Then modify 'tex.m' such that it looks like
```
    [dvi,loginfo,err] = localCallTeXParser(tstr, doinitex, verbose, dofileio);
    dvi=dvimod(dvi);
end
```
after you've located the first line (the one with localCallTeXParser...).
Then you need to copy the file 'dvimod' in this folder. This function takes the dvi byte array, and everywhere a character is output, it inserts an opcode to move the current location some additional points to the right. This file is attached as dvimod.txt (as .m was not allowed to upload). The measurement for the additional spacing is a bit awkward, so you need to play around with it. Further, it can only be set for the whole figure, so pointsizes should not be too different. For an example see 'foo.txt'.

---

