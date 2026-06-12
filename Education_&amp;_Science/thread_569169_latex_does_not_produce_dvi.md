---
title: "latex does not produce dvi"
date: 2007-10-06
forum: Education &amp; Science
---

### Post by one_ro on 2007-10-06
Hey all,

I read quite a few posts regarding Ubuntu, Kile, LaTeX and DVI files.
My problem is somewhat similar, but I couldn't figure out a solution. As in other cases ([http://ubuntuforums.org/showthread.php?t=236130](http://ubuntuforums.org/showthread.php?t=236130)), my system won't produce DVI files, no matter if I run from Kile or from the command line.

I understand there is a problem with this configuration:
```
\usepackage[pdftex]{graphicx}
```What I don't understand is: how did it work very well (with the same configuration file) up until a couple of weeks ago?

I have no idea what I did, it simply stopped producing the DVI file. Only PDFLaTeX would correctly produce the PDF file, but I'd very much like to use DVI files as well.

Any hints would be greatly appreciated.
Adrian

---

### Post by euler_fan on 2007-10-07
Please post your preamble sans anything sensitive.

---

### Post by gnusci on 2007-10-08
try with:

[PHP]\usepackage{graphicx}[/PHP]

---

### Post by one_ro on 2007-10-11
Thanks euler_fan and gnusci, and sorry to be so slow.

I believe I solved it, indeed I used:
```
\usepackage{graphicx}
```

Previously I had used:
```
\usepackage[pdftex]{graphicx}
```

because of my LaTeX distribution not showing .eps files in the DVI output (I still have this problem).

All the best,
Adrian

---

### Post by crispus on 2007-10-15
one_ro,

this may or may not help, but have you tried putting

\usepackage{epsfig}

in your preamble? This may help RE: displaying EPS figures in your DVI output.

Just a thought.

---

### Post by one_ro on 2007-10-15
Hello crispus,

I just tried, with no avail :(

I believe my problem has something to do with my ghostscript configuration. For example, when I try to open an .eps file, I get this error in KGhostView:

```
CRIT: rangecheck in get
Operand stack:
          0
```These are some more information about my system (Kubuntu Feisty Fawn):

```
~$ convert --version
Version: ImageMagick 6.2.4 02/16/07 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2005 ImageMagick Studio LLC
```and 

```
~$  identify -list format
   Format  Module    Mode  Description
-------------------------------------------------------------------------------
        A* RAW       rw+   Raw alpha samples
      ART* ART       r--   PFS: 1st Publisher
           Format originally used on the Macintosh (MacPaint?) and later used
           for PFS: 1st Publisher clip art.  NOT the AOL ART format.
      AVI* AVI       r--   Microsoft Audio/Visual Interleaved
      AVS* AVS       rw+   AVS X image
        B* RAW       rw+   Raw blue samples
      BMP* BMP       rw-   Microsoft Windows bitmap image
     BMP2* BMP       -w-   Microsoft Windows bitmap image v2
     BMP3* BMP       -w-   Microsoft Windows bitmap image v3
        C* RAW       rw+   Raw cyan samples
    CACHE* CACHE     ---   Magick Persistent Cache image format
  CAPTION* CAPTION   r--   Image caption
      CIN* CIN       rw+   Cineon Image File
      CIP* CIP       -w-   Cisco IP phone image format
     CLIP* CLIP      -w+   Image Clip Mask
     CMYK* CMYK      rw+   Raw cyan, magenta, yellow, and black samples
    CMYKA* CMYK      rw+   Raw cyan, magenta, yellow, black, and opacity 
samples
      CUR* CUR       rw-   Microsoft icon
      CUT* CUT       r--   DR Halo
      DCM* DCM       r--   Digital Imaging and Communications in Medicine 
image
           DICOM is used by the medical community for images like X-rays.  The
           specification, "Digital Imaging and Communications in Medicine
           (DICOM)", is available at http://medical.nema.org/.  In particular,
           see part 5 which describes the image encoding (RLE, JPEG, JPEG-LS),
           and supplement 61 which adds JPEG-2000 encoding.
      DCX* PCX       rw+   ZSoft IBM PC multi-page Paintbrush
      DNG* DNG       r--   Digital Negative
      DPS  DPS       ---   Display Postscript Interpreter
      DPX* DPX       rw+   SMPTE 268M-2003 (DPX)
           File Format for Digital Moving-Picture Exchange (DPX) Version 2.0.
           See SMPTE 268M-2003 specification at http://www.smtpe.org

     EPDF  PDF       rw-   Encapsulated Portable Document Format
      EPI  PS        rw-   Encapsulated PostScript Interchange format
      EPS  PS        rw-   Encapsulated PostScript
     EPS2* PS2       -w-   Level II Encapsulated PostScript
     EPS3* PS3       -w+   Level III Encapsulated PostScript
     EPSF  PS        rw-   Encapsulated PostScript
     EPSI  PS        rw-   Encapsulated PostScript Interchange format
      EPT  EPT       rw-   Encapsulated PostScript with TIFF preview
     EPT2  EPT       rw-   Encapsulated PostScript Level II with TIFF preview
     EPT3  EPT       rw+   Encapsulated PostScript Level III with TIFF preview
      FAX* FAX       rw+   Group 3 FAX
           See TIFF format.  Note that FAX machines use non-square pixels 
which
           are 1.5 times wider than they are tall but computer displays use
           square pixels. FAX images may appear to be narrow unless they are
           explicitly resized using a resize specification of "150x100%".
     FITS* FITS      rw-   Flexible Image Transport System
  FRACTAL* PLASMA    r--   Plasma fractal image
        G* RAW       rw+   Raw green samples
       G3* FAX       rw-   Group 3 FAX
      GIF* GIF       rw+   CompuServe graphics interchange format
    GIF87* GIF       rw-   CompuServe graphics interchange format (version 
87a)
 GRADIENT* GRADIENT  r--   Gradual passing from one shade to another
     GRAY* GRAY      rw+   Raw gray samples
HISTOGRAM* HISTOGRAM -w-   Histogram of the image
      HTM* HTML      -w-   Hypertext Markup Language and a client-side image 
map
     HTML* HTML      -w-   Hypertext Markup Language and a client-side image 
map
      ICB* TGA       rw+   Truevision Targa image
      ICO* ICON      rw-   Microsoft icon
     ICON* ICON      rw-   Microsoft icon
     INFO  INFO      -w+   The image format and characteristics
      JNG* PNG       rw-   JPEG Network Graphics
           See http://www.libpng.org/pub/mng/ for details about the JNG 
format.
           The JNG 1.0 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/mng/documents/.
      JP2* JP2       rw-   JPEG-2000 File Format Syntax
      JPC* JPC       rw-   JPEG-2000 Code Stream Syntax
     JPEG* JPEG      rw-   Joint Photographic Experts Group JFIF format (62)
      JPG* JPEG      rw-   Joint Photographic Experts Group JFIF format
      JPX* JPX       rw-   JPEG-2000 File Format Syntax
        K* RAW       rw+   Raw black samples
    LABEL* LABEL     r--   Image label
        M* RAW       rw+   Raw magenta samples
      M2V  MPEG      rw+   MPEG Video Stream
      MAP* MAP       rw-   Colormap intensities and indices
      MAT* MAT       r--   MATLAB image format
    MATTE* MATTE     -w+   MATTE format
     MIFF* MIFF      rw+   Magick Image File Format
      MNG* PNG       rw+   Multiple-image Network Graphics (libpng 
1.2.15beta5)
           See http://www.libpng.org/pub/mng/ for details about the MNG 
format.
           The MNG 1.0 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/mng/documents/.
     MONO* MONO      rw-   Bi-level bitmap in least-significant-byte first 
order
      MPC* MPC       rw+   Magick Persistent Cache image format
     MPEG  MPEG      rw+   MPEG Video Stream
      MPG  MPEG      rw+   MPEG Video Stream
      MSL* MSL       rw+   Magick Scripting Language
      MTV* MTV       rw+   MTV Raytracing image format
      MVG* MVG       rw-   Magick Vector Graphics
     NULL* NULL      rw-   Constant image of uniform color
        O* RAW       rw+   Raw opacity samples
      OTB* OTB       rw-   On-the-air bitmap
      OTF* TTF       r--   Open Type font (Freetype 2.2.1)
       P7* PNM       rw+   Xv thumbnail format
      PAL* UYVY      rw-   16bit/pixel interleaved YUV
     PALM* PALM      rw+   Palm pixmap
  PATTERN* PATTERN   r--   Predefined pattern
      PBM* PNM       rw+   Portable bitmap format (black and white)
      PCD* PCD       rw-   Photo CD
     PCDS* PCD       rw-   Photo CD
      PCL* PCL       rw-   Printer Control Language
      PCT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PCX* PCX       rw-   ZSoft IBM PC Paintbrush
      PDB* PDB       rw+   Palm Database ImageViewer Format
      PDF  PDF       rw+   Portable Document Format
      PFA* TTF       r--   Postscript Type 1 font (ASCII) (Freetype 2.2.1)
      PFB* TTF       r--   Postscript Type 1 font (binary) (Freetype 2.2.1)
      PGM* PNM       rw+   Portable graymap format (gray scale)
      PGX* PGX       r--   JPEG-2000 VM Format
    PICON* XPM       rw-   Personal Icon
     PICT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PIX* PIX       r--   Alias/Wavefront RLE image format
    PJPEG* JPEG      rw-   Progessive Joint Photographic Experts Group JFIF
   PLASMA* PLASMA    r--   Plasma fractal image
      PNG* PNG       rw-   Portable Network Graphics (libpng 1.2.15beta5)
           See http://www.libpng.org/ for details about the PNG format.  The
           PNG 1.2 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/png/documents/.
    PNG24* PNG       rw-   24-bit RGB PNG, opaque only (zlib 1.2.3)
    PNG32* PNG       rw-   32-bit RGBA PNG, semitransparency OK
     PNG8* PNG       rw-   8-bit indexed PNG, binary transparency only
      PNM* PNM       rw+   Portable anymap
      PPM* PNM       rw+   Portable pixmap format (color)
  PREVIEW* PREVIEW   -w-   Show a preview an image enhancement, effect, or f/x
       PS  PS        rw+   PostScript
      PS2* PS2       -w+   Level II PostScript
      PS3* PS3       -w+   Level III PostScript
      PSD* PSD       rw+   Adobe Photoshop bitmap
     PTIF* TIFF      rw-   Pyramid encoded TIFF
      PWP* PWP       r--   Seattle Film Works
        R* RAW       rw+   Raw red samples
      RAS* SUN       rw+   SUN Rasterfile
      RGB* RGB       rw+   Raw red, green, and blue samples
     RGBA* RGB       rw+   Raw red, green, blue, and alpha samples
     RGBO* RGB       rw+   Raw red, green, blue, and opacity samples
      RLA* RLA       r--   Alias/Wavefront image
      RLE* RLE       r--   Utah Run length encoded image
      SCR* SCR       r--   ZX-Spectrum SCREEN$
      SCT* SCT       r--   Scitex HandShake
      SFW* SFW       r--   Seattle Film Works
      SGI* SGI       rw+   Irix RGB image
    SHTML* HTML      -w-   Hypertext Markup Language and a client-side image 
map
  STEGANO* STEGANO   r--   Steganographic image
      SUN* SUN       rw+   SUN Rasterfile
      SVG* SVG       rw+   Scalable Vector Graphics (XML 2.6.27)
     SVGZ* SVG       rw+   Compressed Scalable Vector Graphics (XML 2.6.27)
     TEXT* TXT       rw+   Text
      TGA* TGA       rw+   Truevision Targa image
      TIF* TIFF      rw+   Tagged Image File Format (42)
     TIFF* TIFF      rw+   Tagged Image File Format (42)
     TILE* TILE      r--   Tile image with a texture
      TIM* TIM       r--   PSX TIM
      TTC* TTF       r--   TrueType font collection (Freetype 2.2.1)
      TTF* TTF       r--   TrueType font (Freetype 2.2.1)
      TXT* TXT       rw+   Text
      UIL* UIL       -w-   X-Motif UIL table
     UYVY* UYVY      rw-   16bit/pixel interleaved YUV
      VDA* TGA       rw+   Truevision Targa image
    VICAR* VICAR     rw-   VICAR rasterfile format
      VID* VID       rw+   Visual Image Directory
     VIFF* VIFF      rw+   Khoros Visualization image
      VST* TGA       rw+   Truevision Targa image
     WBMP* WBMP      rw-   Wireless Bitmap (level 0) image
      WMF* WMF       ---   Windows Meta File
      WMZ* WMZ       ---   Compressed Windows Meta File
      WPG* WPG       r--   Word Perfect Graphics
        X* X         rw+   X Image
      XBM* XBM       rw-   X Windows system bitmap (black and white)
       XC* XC        r--   Constant image uniform color
      XCF* XCF       r--   GIMP image
      XPM* XPM       rw-   X Windows system pixmap (color)
       XV* VIFF      rw+   Khoros Visualization image
      XWD* XWD       rw-   X Windows system window dump (color)
        Y* RAW       rw+   Raw yellow samples
    YCbCr* YCbCr     rw+   Raw Y, Cb, and Cr samples
   YCbCrA* YCbCr     rw+   Raw Y, Cb, Cr, and opacity samples
      YUV* YUV       rw-   CCIR 601 4:1:1 or 4:2:2

* native blob support

identify: unable to open module file 
`/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/magick.la': No such file or 
directory.
```

The end of the **identify -list format** says it is unable to open the magick.la file from ImageMagick, but I don't know how to fix this.

Thanks in advance for any further hint,
Adrian

---

