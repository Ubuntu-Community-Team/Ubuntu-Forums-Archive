---
title: "Installing a program (does it have to be THIS hard???)"
date: 2006-01-09
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-01-09
All I wanted to do was install [vtuner]("http://rr.sote.hu/vtuner/index-angol.html").

I downloaded the source code (vtuner-en-0.1-4.tar.gz) and extracted it to my home folder.  In the vtuner folder, I found a file called INSTALL that told me to install EZWGL first.  So I downloaded EZWGL-1.40c-src.tgz from the same page and extracted it to my home folder.  The first step, according to the README file, was to run ```
make shared;
``` and ```
make install-shared  #
``` as root.  So I typed in ```
sudo make shared;
``` and pressed enter... and my terminal window was suddenly flooded with line after line of "warning" and "error" messages (the window couldn't/wouldn't even hold all of them; these are only the last few):

```
EZ_Widget.h:3819: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromXPixmap’
EZ_Widget.h:3819: warning: data definition has no type or storage class
EZ_Widget.h:3821: error: syntax error before ‘*’ token
EZ_Widget.h:3821: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromXpmFile’
EZ_Widget.h:3821: warning: data definition has no type or storage class
EZ_Widget.h:3822: error: syntax error before ‘*’ token
EZ_Widget.h:3822: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromXpmData’
EZ_Widget.h:3822: warning: data definition has no type or storage class
EZ_Widget.h:3823: error: syntax error before ‘*’ token
EZ_Widget.h:3823: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromRawRGB’
EZ_Widget.h:3823: warning: data definition has no type or storage class
EZ_Widget.h:3824: error: syntax error before ‘*’ token
EZ_Widget.h:3824: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromStaticRawRGB’
EZ_Widget.h:3824: warning: data definition has no type or storage class
EZ_Widget.h:3825: error: syntax error before ‘*’ token
EZ_Widget.h:3825: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromXBitmapFile’
EZ_Widget.h:3825: warning: data definition has no type or storage class
EZ_Widget.h:3826: error: syntax error before ‘*’ token
EZ_Widget.h:3826: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromXBitmapData’
EZ_Widget.h:3826: warning: data definition has no type or storage class
EZ_Widget.h:3827: error: syntax error before ‘*’ token
EZ_Widget.h:3827: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateLabelPixmapFromImageFile’
EZ_Widget.h:3827: warning: data definition has no type or storage class
EZ_Widget.h:3828: error: syntax error before ‘*’ token
EZ_Widget.h:3829: error: syntax error before ‘pixmap’
EZ_Widget.h:3835: error: syntax error before ‘win’
EZ_Widget.h:3839: error: syntax error before ‘window’
EZ_Widget.h:3843: error: syntax error before ‘*’ token
EZ_Widget.h:3843: warning: type defaults to ‘int’ in declaration of ‘EZ_GetBitmapFromFile’
EZ_Widget.h:3843: warning: data definition has no type or storage class
EZ_Widget.h:3845: error: syntax error before ‘*’ token
EZ_Widget.h:3845: warning: type defaults to ‘int’ in declaration of ‘EZ_GetBitmapFromData’
EZ_Widget.h:3845: warning: data definition has no type or storage class
EZ_Widget.h:3846: error: syntax error before ‘*’ token
EZ_Widget.h:3846: warning: type defaults to ‘int’ in declaration of ‘EZ_GetPixmapFromData’
EZ_Widget.h:3846: warning: data definition has no type or storage class
EZ_Widget.h:3847: error: syntax error before ‘*’ token
EZ_Widget.h:3847: warning: type defaults to ‘int’ in declaration of ‘EZ_GetPixmapFromRawRGB’
EZ_Widget.h:3847: warning: data definition has no type or storage class
EZ_Widget.h:3848: error: syntax error before ‘*’ token
EZ_Widget.h:3848: warning: type defaults to ‘int’ in declaration of ‘EZ_GetPixmapFromStaticRawRGB’
EZ_Widget.h:3848: warning: data definition has no type or storage class
EZ_Widget.h:3849: error: syntax error before ‘*’ token
EZ_Widget.h:3849: error: syntax error before ‘pix’
EZ_Widget.h:3849: warning: type defaults to ‘int’ in declaration of ‘EZ_GetPixmapFromPixmap’
EZ_Widget.h:3849: warning: data definition has no type or storage class
EZ_Widget.h:3850: error: syntax error before ‘*’ token
EZ_Widget.h:3850: error: syntax error before ‘pix’
EZ_Widget.h:3850: warning: type defaults to ‘int’ in declaration of ‘EZ_GetPixmapFromPermPixmap’
EZ_Widget.h:3850: warning: data definition has no type or storage class
EZ_Widget.h:3851: error: syntax error before ‘*’ token
EZ_Widget.h:3851: warning: type defaults to ‘int’ in declaration of ‘EZ_GetImageFromFile’
EZ_Widget.h:3851: warning: data definition has no type or storage class
EZ_Widget.h:3852: error: syntax error before ‘*’ token
EZ_Widget.h:3852: warning: type defaults to ‘int’ in declaration of ‘EZ_GetAnyPixmapFromFile’
EZ_Widget.h:3852: warning: data definition has no type or storage class
EZ_Widget.h:3853: error: syntax error before ‘*’ token
EZ_Widget.h:3854: error: syntax error before ‘*’ token
EZ_Widget.h:3858: error: syntax error before ‘*’ token
EZ_Widget.h:3862: error: syntax error before ‘*’ token
EZ_Widget.h:3862: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateBackgroundPixmapsFromImageFile’
EZ_Widget.h:3862: warning: data definition has no type or storage class
EZ_Widget.h:3863: error: syntax error before ‘*’ token
EZ_Widget.h:3863: error: syntax error before ‘pix’
EZ_Widget.h:3863: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateBackgroundPixmapsFromXPixmap’
EZ_Widget.h:3863: warning: data definition has no type or storage class
EZ_Widget.h:3865: error: syntax error before ‘*’ token
EZ_Widget.h:3865: error: syntax error before ‘pix’
EZ_Widget.h:3865: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateBackgroundPixmapsFromXPixmapX’
EZ_Widget.h:3865: warning: data definition has no type or storage class
EZ_Widget.h:3869: error: syntax error before ‘*’ token
EZ_Widget.h:3869: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateBackgroundPixmapsFromRawRGB’
EZ_Widget.h:3869: warning: data definition has no type or storage class
EZ_Widget.h:3871: error: syntax error before ‘*’ token
EZ_Widget.h:3871: error: syntax error before ‘*’ token
EZ_Widget.h:3871: warning: type defaults to ‘int’ in declaration of ‘EZ_CheckBGPixmap’
EZ_Widget.h:3871: warning: data definition has no type or storage class
EZ_Widget.h:3872: error: syntax error before ‘*’ token
EZ_Widget.h:3872: error: syntax error before ‘*’ token
EZ_Widget.h:3872: warning: type defaults to ‘int’ in declaration of ‘EZ_ScaleLabelPixmap’
EZ_Widget.h:3872: warning: data definition has no type or storage class
EZ_Widget.h:3875: error: syntax error before ‘*’ token
EZ_Widget.h:3876: error: syntax error before ‘*’ token
EZ_Widget.h:3881: error: syntax error before ‘pixmap’
EZ_Widget.h:3924: error: syntax error before ‘XEvent’
EZ_Widget.h:3955: error: syntax error before ‘XEvent’
EZ_Widget.h:3965: error: syntax error before ‘*’ token
EZ_Widget.h:3965: warning: type defaults to ‘int’ in declaration of ‘EZ_Read3DCanvas2XImage’
EZ_Widget.h:3965: warning: data definition has no type or storage class
EZ_Widget.h:3969: error: syntax error before ‘*’ token
EZ_Widget.h:3969: error: syntax error before ‘d’
EZ_Widget.h:3969: warning: type defaults to ‘int’ in declaration of ‘EZ_ReadDrawable2XImage’
EZ_Widget.h:3969: warning: data definition has no type or storage class
EZ_Widget.h:3970: error: syntax error before ‘*’ token
EZ_Widget.h:3971: error: syntax error before ‘*’ token
EZ_Widget.h:3982: error: syntax error before ‘XEvent’
EZ_Widget.h:4052: error: syntax error before ‘XEvent’
EZ_Widget.h:4053: error: syntax error before ‘XEvent’
EZ_Widget.h:4062: error: syntax error before ‘XEvent’
EZ_Widget.h:4068: error: syntax error before ‘XPoint’
EZ_Widget.h:4073: error: syntax error before ‘XPoint’
EZ_Widget.h:4078: error: syntax error before ‘Drawable’
EZ_Widget.h:4079: error: syntax error before ‘Drawable’
EZ_Widget.h:4083: error: syntax error before ‘Drawable’
EZ_Widget.h:4087: error: syntax error before ‘drawable’
EZ_Widget.h:4097: error: syntax error before ‘XPoint’
EZ_Widget.h:4101: error: syntax error before ‘GC’
EZ_Widget.h:4105: error: syntax error before ‘GC’
EZ_Widget.h:4109: error: syntax error before ‘Drawable’
EZ_Widget.h:4117: error: syntax error before ‘*’ token
EZ_Widget.h:4117: warning: type defaults to ‘int’ in declaration of ‘EZ_GetWidgetFont’
EZ_Widget.h:4117: warning: data definition has no type or storage class
EZ_Widget.h:4118: error: syntax error before ‘*’ token
EZ_Widget.h:4118: warning: type defaults to ‘int’ in declaration of ‘EZ_GetFontFromId’
EZ_Widget.h:4118: warning: data definition has no type or storage class
EZ_Widget.h:4119: error: syntax error before ‘*’ token
EZ_Widget.h:4119: error: syntax error before ‘font’
EZ_Widget.h:4119: warning: type defaults to ‘int’ in declaration of ‘EZ_GetFontFromXFontId’
EZ_Widget.h:4119: warning: data definition has no type or storage class
EZ_Widget.h:4120: error: syntax error before ‘*’ token
EZ_Widget.h:4120: warning: type defaults to ‘int’ in declaration of ‘EZ_GetFontFromName’
EZ_Widget.h:4120: warning: data definition has no type or storage class
EZ_Widget.h:4123: error: syntax error before ‘*’ token
EZ_Widget.h:4125: error: syntax error before ‘*’ token
EZ_Widget.h:4136: error: syntax error before ‘*’ token
EZ_Widget.h:4137: error: syntax error before ‘XEvent’
EZ_Widget.h:4141: error: syntax error before ‘*’ token
EZ_Widget.h:4150: error: syntax error before ‘*’ token
EZ_Widget.h:4154: error: syntax error before ‘*’ token
EZ_Widget.h:4164: error: syntax error before ‘EZ_CreateGCFor3DCanvas’
EZ_Widget.h:4164: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateGCFor3DCanvas’
EZ_Widget.h:4164: warning: data definition has no type or storage class
EZ_Widget.h:4165: error: syntax error before ‘*’ token
EZ_Widget.h:4179: error: syntax error before ‘Pixmap’
EZ_Widget.h:4181: error: syntax error before ‘Pixmap’
EZ_Widget.h:4182: error: syntax error before ‘Pixmap’
EZ_Widget.h:4183: error: syntax error before ‘Pixmap’
EZ_Widget.h:4184: error: syntax error before ‘Pixmap’
EZ_Widget.h:4185: error: syntax error before ‘*’ token
EZ_Widget.h:4196: error: syntax error before ‘*’ token
EZ_Widget.h:4204: error: syntax error before ‘ITextLine’
EZ_Widget.h:4209: error: syntax error before ‘ITextLine’
EZ_Widget.h:4218: error: syntax error before ‘*’ token
EZ_Widget.h:4218: error: syntax error before ‘EZ_Bitmap’
EZ_Widget.h:4218: warning: type defaults to ‘int’ in declaration of ‘EZ_GetTextPropertyFromID’
EZ_Widget.h:4218: warning: data definition has no type or storage class
EZ_Widget.h:4224: error: syntax error before ‘*’ token
EZ_Widget.h:4224: error: syntax error before ‘*’ token
EZ_Widget.h:4224: warning: type defaults to ‘int’ in declaration of ‘EZ_CopyTextPropIgnoreSpecial’
EZ_Widget.h:4224: warning: data definition has no type or storage class
EZ_Widget.h:4232: error: syntax error before ‘*’ token
EZ_Widget.h:4235: error: syntax error before ‘*’ token
EZ_Widget.h:4237: error: syntax error before ‘*’ token
EZ_Widget.h:4238: error: syntax error before ‘*’ token
EZ_Widget.h:4248: error: syntax error before ‘XEvent’
EZ_Widget.h:4284: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4290: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4295: error: syntax error before ‘Window’
EZ_Widget.h:4295: error: syntax error before ‘)’ token
EZ_Widget.h:4299: error: syntax error before ‘XEvent’
EZ_Widget.h:4335: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4342: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4386: error: syntax error before ‘XEvent’
EZ_Widget.h:4394: error: syntax error before ‘Drawable’
EZ_Widget.h:4400: error: syntax error before ‘Drawable’
EZ_Widget.h:4406: error: syntax error before ‘Drawable’
EZ_Widget.h:4412: error: syntax error before ‘Drawable’
EZ_Widget.h:4430: error: syntax error before ‘Cursor’
EZ_Widget.h:4437: error: syntax error before ‘Pixmap’
EZ_Widget.h:4440: error: syntax error before ‘Pixmap’
EZ_Widget.h:4443: error: syntax error before ‘Pixmap’
EZ_Widget.h:4470: error: syntax error before ‘Pixmap’
EZ_Widget.h:4507: error: syntax error before ‘Drawable’
EZ_Widget.h:4522: error: syntax error before ‘XEvent’
EZ_Widget.h:4535: error: syntax error before ‘window’
EZ_Widget.h:4536: error: syntax error before ‘Window’
EZ_Widget.h:4545: error: syntax error before ‘*’ token
EZ_Widget.h:4548: error: syntax error before ‘hint’
EZ_Widget.h:4550: error: syntax error before ‘Window’
EZ_Widget.h:4565: error: syntax error before ‘window’
EZ_Widget.h:4566: error: syntax error before ‘window’
EZ_Widget.h:4567: error: syntax error before ‘window’
EZ_Widget.h:4581: error: syntax error before ‘XEvent’
EZ_Widget.h:4598: error: syntax error before ‘Pixmap’
EZ_Widget.h:4652: error: syntax error before ‘XEvent’
EZ_Widget.h:4704: error: syntax error before ‘XEvent’
EZ_Widget.h:4788: error: syntax error before ‘Drawable’
EZ_Widget.h:4794: error: syntax error before ‘Drawable’
EZ_Widget.h:4800: error: syntax error before ‘Drawable’
EZ_Widget.h:4828: error: syntax error before ‘Drawable’
EZ_Widget.h:4838: error: syntax error before ‘Drawable’
EZ_Widget.h:4849: error: syntax error before ‘Drawable’
EZ_Widget.h:4854: error: syntax error before ‘Drawable’
EZ_Widget.h:4890: error: syntax error before ‘Drawable’
EZ_Widget.h:4907: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4908: error: syntax error before ‘EZ_TextProperty’
EZ_Widget.h:4910: error: syntax error before ‘*’ token
EZ_Widget.h:4910: warning: type defaults to ‘int’ in declaration of ‘EZ_GetLabelItemPixmap’
EZ_Widget.h:4910: warning: data definition has no type or storage class
EZ_Widget.h:4914: error: syntax error before ‘*’ token
EZ_Widget.h:4917: error: syntax error before ‘EZ_FigPiece’
EZ_Widget.h:4918: error: syntax error before ‘EZ_FigPiece’
EZ_Widget.h:4920: error: syntax error before ‘EZ_FigPiece’
EZ_Widget.h:4921: error: syntax error before ‘*’ token
EZ_Widget.h:4921: error: syntax error before ‘GC’
EZ_Widget.h:4921: warning: type defaults to ‘int’ in declaration of ‘EZ_FigItemAddPiece’
EZ_Widget.h:4921: warning: data definition has no type or storage class
EZ_Widget.h:4925: error: syntax error before ‘EZ_FigPiece’
EZ_Widget.h:4928: error: syntax error before ‘EZ_GetGC’
EZ_Widget.h:4928: error: syntax error before ‘XGCValues’
EZ_Widget.h:4928: warning: type defaults to ‘int’ in declaration of ‘EZ_GetGC’
EZ_Widget.h:4928: warning: data definition has no type or storage class
EZ_Widget.h:4929: error: syntax error before ‘gc’
EZ_Widget.h:4938: error: syntax error before ‘Drawable’
EZ_Widget.h:4938: error: syntax error before ‘Drawable’
EZ_Widget.h:4938: error: syntax error before ‘Drawable’
EZ_Widget.h:5002: error: syntax error before ‘Drawable’
EZ_Widget.h:5022: error: syntax error before ‘*’ token
EZ_Widget.h:5035: error: syntax error before ‘XEvent’
EZ_Widget.h:5135: error: syntax error before ‘XEvent’
EZ_Widget.h:5141: error: syntax error before ‘XEvent’
EZ_Widget.h:5158: error: syntax error before ‘EZ_GetWritableGC’
EZ_Widget.h:5158: warning: type defaults to ‘int’ in declaration of ‘EZ_GetWritableGC’
EZ_Widget.h:5158: warning: data definition has no type or storage class
EZ_Widget.h:5166: error: syntax error before ‘Atom’
EZ_Widget.h:5169: error: syntax error before ‘Atom’
EZ_Widget.h:5171: error: syntax error before ‘Atom’
EZ_Widget.h:5174: error: syntax error before ‘Atom’
EZ_Widget.h:5178: error: syntax error before ‘Atom’
EZ_Widget.h:5181: error: syntax error before ‘Atom’
EZ_Widget.h:5183: error: syntax error before ‘Atom’
EZ_Widget.h:5186: error: syntax error before ‘Atom’
EZ_Widget.h:5189: error: syntax error before ‘*’ token
EZ_Widget.h:5189: error: syntax error before ‘*’ token
EZ_Widget.h:5189: warning: type defaults to ‘int’ in declaration of ‘EZ_FindEncoderGivenTarget’
EZ_Widget.h:5189: warning: data definition has no type or storage class
EZ_Widget.h:5190: error: syntax error before ‘*’ token
EZ_Widget.h:5190: error: syntax error before ‘*’ token
EZ_Widget.h:5190: warning: type defaults to ‘int’ in declaration of ‘EZ_FindDecoderGivenTarget’
EZ_Widget.h:5190: warning: data definition has no type or storage class
EZ_Widget.h:5196: error: syntax error before ‘EZ_GetAtom’
EZ_Widget.h:5196: warning: type defaults to ‘int’ in declaration of ‘EZ_GetAtom’EZ_Widget.h:5196: warning: data definition has no type or storage class
EZ_Widget.h:5205: error: syntax error before ‘Window’
EZ_Widget.h:5212: error: syntax error before ‘cwin’
EZ_Widget.h:5216: error: syntax error before ‘target’
EZ_Widget.h:5219: error: syntax error before ‘type’
EZ_Widget.h:5222: error: syntax error before ‘Window’
EZ_Widget.h:5238: error: syntax error before ‘*’ token
EZ_Widget.h:5240: error: syntax error before ‘*’ token
EZ_Widget.h:5244: error: syntax error before ‘cursor’
EZ_Widget.h:5246: error: syntax error before ‘XEvent’
EZ_Widget.h:5247: error: syntax error before ‘win’
EZ_Widget.h:5248: error: syntax error before ‘win’
EZ_Widget.h:5260: error: syntax error before ‘Atom’
EZ_Widget.h:5263: error: syntax error before ‘*’ token
EZ_Widget.h:5263: warning: type defaults to ‘int’ in declaration of ‘EZ_FindSpecialEncoder’
EZ_Widget.h:5263: warning: data definition has no type or storage class
EZ_Widget.h:5272: error: syntax error before ‘Pixmap’
EZ_Widget.h:5321: error: syntax error before ‘XEvent’
EZ_Widget.h:5366: error: syntax error before ‘XEvent’
EZ_Widget.h:5391: error: syntax error before ‘XEvent’
EZ_Widget.h:5414: error: syntax error before ‘EZ_Bitmap’
EZ_Widget.h:5420: error: syntax error before ‘Pixmap’
EZ_Widget.h:5427: error: syntax error before ‘Pixmap’
EZ_Widget.h:5447: error: syntax error before ‘EZ_GetCursor’
EZ_Widget.h:5447: warning: type defaults to ‘int’ in declaration of ‘EZ_GetCursor’
EZ_Widget.h:5447: warning: data definition has no type or storage class
EZ_Widget.h:5448: error: syntax error before ‘EZ_GetCursorByName’
EZ_Widget.h:5448: warning: type defaults to ‘int’ in declaration of ‘EZ_GetCursorByName’
EZ_Widget.h:5448: warning: data definition has no type or storage class
EZ_Widget.h:5449: error: syntax error before ‘csr’
EZ_Widget.h:5450: error: syntax error before ‘Cursor’
EZ_Widget.h:5451: error: syntax error before ‘Cursor’
EZ_Widget.h:5468: error: syntax error before ‘*’ token
EZ_Widget.h:5468: warning: type defaults to ‘int’ in declaration of ‘EZ_GetResourceDatabase’
EZ_Widget.h:5468: warning: data definition has no type or storage class
EZ_Widget.h:5469: error: syntax error before ‘XrmOptionDescRec’
EZ_Widget.h:5511: error: syntax error before ‘mtype’
EZ_Widget.h:5514: error: syntax error before ‘mtype’
EZ_Widget.h:5517: error: syntax error before ‘mtype’
EZ_Widget.h:5519: error: syntax error before ‘mtype’
EZ_Widget.h:5522: error: syntax error before ‘*’ token
EZ_Widget.h:5523: error: syntax error before ‘*’ token
EZ_Widget.h:5533: error: syntax error before ‘win’
EZ_Widget.h:5541: error: syntax error before ‘Drawable’
EZ_Widget.h:5546: error: syntax error before ‘*’ token
EZ_Widget.h:5546: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateRotateTextPixmap’
EZ_Widget.h:5546: warning: data definition has no type or storage class
EZ_Widget.h:5547: error: syntax error before ‘*’ token
EZ_Widget.h:5547: warning: type defaults to ‘int’ in declaration of ‘EZ_CreateRotateTextPixmapU’
EZ_Widget.h:5547: warning: data definition has no type or storage class
EZ_Widget.h:5559: error: syntax error before ‘*’ token
EZ_Widget.h:5559: warning: type defaults to ‘int’ in declaration of ‘EZ_GetTextProperty’
EZ_Widget.h:5559: warning: data definition has no type or storage class
EZ_Buffers.c: In function ‘EZ_LogicOp’:
EZ_Buffers.c:71: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c:72: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:79: error: ‘GXclear’ undeclared (first use in this function)
EZ_Buffers.c:79: error: (Each undeclared identifier is reported only once
EZ_Buffers.c:79: error: for each function it appears in.)
EZ_Buffers.c:80: error: ‘GXand’ undeclared (first use in this function)
EZ_Buffers.c:81: error: ‘GXandReverse’ undeclared (first use in this function)
EZ_Buffers.c:82: error: ‘GXcopy’ undeclared (first use in this function)
EZ_Buffers.c:83: error: ‘GXandInverted’ undeclared (first use in this function)
EZ_Buffers.c:84: error: ‘GXnoop’ undeclared (first use in this function)
EZ_Buffers.c:85: error: ‘GXxor’ undeclared (first use in this function)
EZ_Buffers.c:86: error: ‘GXor’ undeclared (first use in this function)
EZ_Buffers.c:87: error: ‘GXnor’ undeclared (first use in this function)
EZ_Buffers.c:88: error: ‘GXequiv’ undeclared (first use in this function)
EZ_Buffers.c:89: error: ‘GXinvert’ undeclared (first use in this function)
EZ_Buffers.c:90: error: ‘GXorReverse’ undeclared (first use in this function)
EZ_Buffers.c:91: error: ‘GXcopyInverted’ undeclared (first use in this function)EZ_Buffers.c:92: error: ‘GXorInverted’ undeclared (first use in this function)
EZ_Buffers.c:93: error: ‘GXnand’ undeclared (first use in this function)
EZ_Buffers.c:94: error: ‘GXset’ undeclared (first use in this function)
EZ_Buffers.c:100: warning: implicit declaration of function ‘XSetFunction’
EZ_Buffers.c:100: error: request for member ‘TheDisplay’ in something not a structure or union
EZ_Buffers.c:100: error: request for member ‘TheGC’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_SetBackBuffer’:
EZ_Buffers.c:110: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:114: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c:119: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_AutoSelectBackBuffer’:
EZ_Buffers.c:131: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_SelectFastBackBuffer’:
EZ_Buffers.c:152: error: request for member ‘hasshm’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_DrawBuffer’:
EZ_Buffers.c:163: error: request for member ‘CompileMode’ in something not a structure or union
EZ_Buffers.c:170: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:174: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:176: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:177: error: request for member ‘TheDrawable’ in something not a structure or union
EZ_Buffers.c:177: error: request for member ‘TheWindow’ in something not a structure or union
EZ_Buffers.c:178: error: request for member ‘TheCanvas’ in something not a structure or union
EZ_Buffers.c:183: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:185: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:186: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c:188: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c:189: error: request for member ‘TheDrawable’ in something not a structure or union
EZ_Buffers.c:189: error: request for member ‘pixmap’ in something not a structure or union
EZ_Buffers.c:191: error: request for member ‘TheDrawable’ in something not a structure or union
EZ_Buffers.c:191: error: request for member ‘TheWindow’ in something not a structure or union
EZ_Buffers.c:192: error: request for member ‘TheCanvas’ in something not a structure or union
EZ_Buffers.c:196: error: request for member ‘doublebuffer’ in something not a structure or union
EZ_Buffers.c:198: error: request for member ‘TheDrawable’ in something not a structure or union
EZ_Buffers.c:198: error: request for member ‘pixmap’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_SwapBuffers’:
EZ_Buffers.c:213: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:215: error: request for member ‘frontbuffer’ in something not a structure or union
EZ_Buffers.c:216: error: request for member ‘swapbufferfunc’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_ClearColorf’:
EZ_Buffers.c:226: error: request for member ‘CompileMode’ in something not a structure or union
EZ_Buffers.c:235: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:237: error: request for member ‘backcolor’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_ClearIndex’:
EZ_Buffers.c:248: error: request for member ‘CompileMode’ in something not a structure or union
EZ_Buffers.c:254: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:255: error: request for member ‘backcolor’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_Clear’:
EZ_Buffers.c:261: error: request for member ‘CompileMode’ in something not a structure or union
EZ_Buffers.c:266: error: request for member ‘ExecuteMode’ in something not a structure or union
EZ_Buffers.c:268: error: request for member ‘clearfunc’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_SwapBuffers_XImage’:
EZ_Buffers.c:283: error: request for member ‘hasshm’ in something not a structure or union
EZ_Buffers.c:284: warning: implicit declaration of function ‘XShmPutImage’
EZ_Buffers.c:284: error: request for member ‘TheDisplay’ in something not a structure or union
EZ_Buffers.c:284: error: request for member ‘TheWindow’ in something not a structure or union
EZ_Buffers.c:284: error: request for member ‘TheGC’ in something not a structure or union
EZ_Buffers.c:284: error: request for member ‘Image’ in something not a structure or union
EZ_Buffers.c:286: error: request for member ‘WindowWidth’ in something not a structure or union
EZ_Buffers.c:287: error: request for member ‘WindowHeight’ in something not a structure or union
EZ_Buffers.c:287: error: ‘False’ undeclared (first use in this function)
EZ_Buffers.c:290: warning: implicit declaration of function ‘XPutImage’
EZ_Buffers.c:290: error: request for member ‘TheDisplay’ in something not a structure or union
EZ_Buffers.c:290: error: request for member ‘TheWindow’ in something not a structure or union
EZ_Buffers.c:290: error: request for member ‘TheGC’ in something not a structure or union
EZ_Buffers.c:290: error: request for member ‘Image’ in something not a structure or union
EZ_Buffers.c:292: error: request for member ‘WindowWidth’ in something not a structure or union
EZ_Buffers.c:293: error: request for member ‘WindowHeight’ in something not a structure or union
EZ_Buffers.c:294: warning: implicit declaration of function ‘XSync’
EZ_Buffers.c:294: error: request for member ‘TheDisplay’ in something not a structure or union
EZ_Buffers.c: In function ‘EZ_SwapBuffers_Pixmap’:
EZ_Buffers.c:303: warning: implicit declaration of function ‘XCopyArea’
EZ_Buffers.c:303: error: request for member ‘TheDisplay’ in something not a structure or union
EZ_Buffers.c:304: error: request for member ‘pixmap’ in something not a structure or union
EZ_Buffers.c:305: error: request for member ‘TheWindow’ in something not a structure or union
EZ_Buffers.c:306: error: request for member ‘TheGC’ in something not a structure or union
EZ_Buffers.c:308: error: request for member ‘WindowWidth’ in something not a structure or union
EZ_Buffers.c:308: error: request for member ‘WindowHeight’ in something not a structure or union
EZ_Buffers.c:310: error: request for member ‘TheDisplay’ in something not a structure or union
make[1]: *** [EZ_Buffers.o] Error 1
make[1]: Leaving directory `/home/jonathan/EZWGL-1.40c/lib'
make: *** [shared] Error 2
jonathan@jonathan:~/EZWGL-1.40c$

```

WHAT DID I DO WRONG?  Until someone can help me get this program installed, I'll be using Windows...!

---

### Post by zoiks on 2006-01-09
My guess is you are missing a prerequisite, probably a development package.  Carefully examine the requirements of the package you're trying to compile and make sure that the "-dev" versions are installed as well.  You might start with "xlibs-static-dev", but honestly I don't know.  The source tarball for EZWGL should document which packages it needs to have installed.  HTH

---

### Post by aysiu on 2006-01-09
I noticed on the vtuner website, there are RPM files for Red Hat. Have you tried installing those? Download it to the desktop and then type in these commands ```
sudo apt-get update
sudo apt-get install alien
cd Desktop
sudo alien -i vtuner-en-guitar-0.1-4.i386.rpm
```

---

### Post by rykel on 2006-01-09
[QUOTE=jmxhgyZN8wK7]All I wanted to do was install vtuner... WHAT DID I DO WRONG?  Until someone can help me get this program installed, I'll be using Windows...![/QUOTE]

one thing you can do is to contact the developers for vtuner, and request an autopackage (see [http://www.autopackage.org]("http://www.autopackage.org")) version of their program.

u can then install it easily like the way software is installed in windows.

installing programs is indeed a **frustrating** experience for many new linux users, altho' current technologies such as synaptic are making it easier. but still, synaptic will never be able to catch up with the vast number of new applications popping up out there in the world.

can u imagine microsoft "windows update" website trying to host the latest versions of ALL the software made for windows?!

microsoft will collapse at the mere weight of such an endeavour...   :rolleyes:

---

### Post by aysiu on 2006-01-09
[QUOTE=rykel]
installing programs is indeed a **frustrating** experience for many new linux users, altho' current technologies such as synaptic are making it easier. but still, synaptic will never be able to catch up with the vast number of new applications popping up out there in the world.[/QUOTE] Users who want obscure programs (I'd never heard of vtuner before reading this thread) and who don't like ./configure and all that will indeed be frustrated.

Users who have simple needs (users like me) will be more than happy with Synaptic, and love how it's all centralized, trustworthy, and easy to search.

Some users who want obscure programs are advanced enough that they not only aren't afraid of the ./configure--they embrace it; they love it.

---

### Post by mr_ed on 2006-01-10
On the vtuner webpage, it says "Usually you also need to download EZWGL"

Chances are that you didn't install that first (since the errors all start with EZ, like "EZ_Widget.h")

Unfortunately you have the exception to the rule.  Normally installing programs is quite easy with Synaptic.

---

### Post by rykel on 2006-01-10
[QUOTE=aysiu]Users who want obscure programs (I'd never heard of vtuner before reading this thread) and who don't like ./configure and all that will indeed be frustrated.

Users who have simple needs (users like me) will be more than happy with Synaptic, and love how it's all centralized, trustworthy, and easy to search.

Some users who want obscure programs are advanced enough that they not only aren't afraid of the ./configure--they embrace it; they love it.[/QUOTE]

i agree with you more or less... it will be a fantastic world if every program came as either source code (so that distros can package them into debs or rpms or watever they like) and autopackage (ie. binary; so everyone of us can install them easily).

tat day WILL come!!!   :KS

---

