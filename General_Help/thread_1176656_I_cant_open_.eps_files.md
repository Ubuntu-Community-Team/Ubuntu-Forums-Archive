---
title: "I cant open *.eps files"
date: 2009-06-02
forum: General Help
---

### Post by bilalshah on 2009-06-02
Hi all,
I am using geant4 on Ubuntu 9.04. Geant has geometry files which can be viewed using any postscript viewer. There seems to be a problem becasue I have installed gv, evince, and octave and none of them can show me the .eps file. when i open .eps file with gv and evince it open the window but shows nothing. However when i use octave it say:
syntax error

>>> /Times-Roman findfont 24 scalefont setfont
Can anyone help me. Thanks in advance.

---

### Post by blueridgedog on 2009-06-02
Try open office draw...

[http://blenderartists.org/forum/showthread.php?t=93940](http://blenderartists.org/forum/showthread.php?t=93940)

You can then save it to a native inkscape format for editing.

---

### Post by Chronon on 2009-06-02
> **bilalshah said:**
> Hi all,
I am using geant4 on Ubuntu 9.04. Geant has geometry files which can be viewed using any postscript viewer. There seems to be a problem becasue I have installed gv, evince, and octave and none of them can show me the .eps file. when i open .eps file with gv and evince it open the window but shows nothing. However when i use octave it say:
syntax error


Are you sure the .eps files are well formed?  I have had issues with wrong bounding boxes before with .eps and it might explain what you're seeing.  If the bounding box doesn't contain the content you wish to see then you may only see a blank page.  You can open the .eps file in a text editor to check the bounding box.  (It's usually specified in the second line of the file.)

---

### Post by bilalshah on 2009-06-03
> **Chronon said:**
> Are you sure the .eps files are well formed?  I have had issues with wrong bounding boxes before with .eps and it might explain what you're seeing.  If the bounding box doesn't contain the content you wish to see then you may only see a blank page.  You can open the .eps file in a text editor to check the bounding box.  (It's usually specified in the second line of the file.)

Thanks for replying. I get the following when i open my eps file with text editor

%!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: 56.6929134 56.6929134 538.582677 785.19685
% FILE: g4_01.eps

% DEFAULT FONT:
/Times-Roman findfont 24 scalefont setfont 

% DEFAULT COLOR:
0 0 0 setrgbcolor

% DEFAULT LINE:
0.283464567 setlinewidth
[1.41732283] 0 setdash

% DEFINE PostScript Functions:
/PATH
{/POINT 0 def
 /X 0 def
 newpath
 {X 1 eq{POINT 0 eq{moveto
                    /POINT 1 def
                  }{lineto }ifelse
         /X 0 def
       }{/X X 1 add def}ifelse
 }forall
} def
/FILLPOLYGON{ PATH closepath fill }def
/DRAWFILLPOLYGON{ PATH closepath gsave stroke grestore fill }def
/DRAWPOLYGON{ PATH closepath stroke }def
/DRAWPATH { PATH stroke } def
/BOXPATH
{/X 0 def
 {X 0 eq{/LLX exch def}if
  X 1 eq{/LLY exch def}if
  X 2 eq{/URX exch def}if
  X 3 eq{/URY exch def}if
  /X X 1 add def
 }forall
 LLX LLY moveto
 URX LLY lineto
 URX URY lineto
 LLX URY lineto
 closepath
}def

% CLIPPING:
[56.6929134 56.6929134 538.582677 785.19685] BOXPATH clip

---

### Post by Chronon on 2009-06-03
Hmm.. It was quite a while ago.  I think I may have used ghostview to alternate between showing bounding box behaviors.

The coordinates of the bounding box at least look plausible:

```
1. The x-coordinate of the lower-left corner of the BoundingBox  == 56.6929134 
2. The y-coordinate of the lower-left corner of the BoundingBox == 56.6929134 
3. The x-coordinate of the upper-right corner of the BoundingBox == 538.582677 
4. The y-coordinate of the upper-right corner of the BoundingBox ==785.19685 
```

---

