---
title: "Problem with compiz-fusion extra plugins"
date: 2009-02-25
forum: Desktop Environments
---

### Post by henryjm206 on 2009-02-25
Hi,

I have installed compiz, compiz fusion, compiz bcop, etc
Then I followed this guide 

[http://forum.compiz-fusion.org/showthread.php?p=56851](http://forum.compiz-fusion.org/showthread.php?p=56851)

to add more of the compiz plugins. Everything went smoothly until I went to compile the plugins. 
This is what happened:
```
henry@my:~/compiz/cubemodel$ make
convert   : cubemodel.xml.in -> build/cubemodel.xml
bcop'ing  : build/cubemodel.xml -> build/cubemodel_options.h
bcop'ing  : build/cubemodel.xml -> build/cubemodel_options.c
schema    : build/cubemodel.xml -> build/compiz-cubemodel.schema
compiling : cubemodel.c -> build/cubemodel.lo
compiling : loadModel.c -> build/loadModel.lo
compiling : build/cubemodel_options.c -> build/cubemodel_options.loIn file included from build/cubemodel_options.c:19:
build/cubemodel_options.h:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:81: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:111: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.h:115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRescaleWidth’
build/cubemodel_options.h:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRenderFrontAndBack’
build/cubemodel_options.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRotateLighting’
build/cubemodel_options.c:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsVTable’
build/cubemodel_options.c:48: error: array type has incomplete element type
build/cubemodel_options.c: In function ‘cubemodelGetGlobalModelScaleFactor’:
build/cubemodel_options.c:56: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:56: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:58: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelGetGlobalModelScaleFactorOption’:
build/cubemodel_options.c:62: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:62: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:64: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetGlobalModelScaleFactorNotify’:
build/cubemodel_options.c:68: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:68: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:72: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelFilenameOption’:
build/cubemodel_options.c:80: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:80: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:82: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelFilenameNotify’:
build/cubemodel_options.c:86: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:86: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelScaleFactorOption’:
build/cubemodel_options.c:98: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:98: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:100: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelScaleFactorNotify’:
build/cubemodel_options.c:104: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:104: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelXOffsetOption’:
build/cubemodel_options.c:116: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:116: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:118: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelXOffsetNotify’:
build/cubemodel_options.c:122: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:122: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelYOffsetOption’:
build/cubemodel_options.c:134: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:134: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:136: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelYOffsetNotify’:
build/cubemodel_options.c:140: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:140: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:144: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelZOffsetOption’:
build/cubemodel_options.c:152: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:152: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:154: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelZOffsetNotify’:
build/cubemodel_options.c:158: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:158: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelRotationPlaneMask’:
build/cubemodel_options.c:170: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:170: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetModelRotationPlaneOption’:
build/cubemodel_options.c:176: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:176: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:178: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelRotationPlaneNotify’:
build/cubemodel_options.c:182: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:182: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelRotationRateOption’:
build/cubemodel_options.c:194: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:194: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:196: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelRotationRateNotify’:
build/cubemodel_options.c:200: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:200: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:204: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelAnimationMask’:
build/cubemodel_options.c:212: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:212: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetModelAnimationOption’:
build/cubemodel_options.c:218: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:218: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:220: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelAnimationNotify’:
build/cubemodel_options.c:224: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:224: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/cubemodel_options.c: In function ‘cubemodelGetModelFpsOption’:
build/cubemodel_options.c:236: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:236: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:238: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetModelFpsNotify’:
build/cubemodel_options.c:242: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:242: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:246: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRescaleWidth’
build/cubemodel_options.c: In function ‘cubemodelGetRescaleWidthOption’:
build/cubemodel_options.c:254: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:254: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:256: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetRescaleWidthNotify’:
build/cubemodel_options.c:260: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:260: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:264: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRenderFrontAndBack’
build/cubemodel_options.c: In function ‘cubemodelGetRenderFrontAndBackOption’:
build/cubemodel_options.c:272: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:272: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:274: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetRenderFrontAndBackNotify’:
build/cubemodel_options.c:278: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:278: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:282: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelGetRotateLighting’
build/cubemodel_options.c: In function ‘cubemodelGetRotateLightingOption’:
build/cubemodel_options.c:290: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:290: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:292: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetRotateLightingNotify’:
build/cubemodel_options.c:296: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:296: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetLightInclination’:
build/cubemodel_options.c:302: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:302: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:304: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelGetLightInclinationOption’:
build/cubemodel_options.c:308: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:308: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:310: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetLightInclinationNotify’:
build/cubemodel_options.c:314: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:314: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetLightAmbient’:
build/cubemodel_options.c:320: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:320: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:322: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelGetLightAmbientOption’:
build/cubemodel_options.c:326: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:326: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:328: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetLightAmbientNotify’:
build/cubemodel_options.c:332: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:332: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetLightDiffuse’:
build/cubemodel_options.c:338: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:338: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:340: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelGetLightDiffuseOption’:
build/cubemodel_options.c:344: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:344: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:346: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetLightDiffuseNotify’:
build/cubemodel_options.c:350: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:350: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetLightSpecular’:
build/cubemodel_options.c:356: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:356: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:358: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelGetLightSpecularOption’:
build/cubemodel_options.c:362: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:362: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:364: warning: control reaches end of non-void function
build/cubemodel_options.c: In function ‘cubemodelSetLightSpecularNotify’:
build/cubemodel_options.c:368: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:368: error: dereferencing pointer to incomplete type
build/cubemodel_options.c: In function ‘cubemodelGetScreenOption’:
build/cubemodel_options.c:374: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:374: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:376: warning: control reaches end of non-void function
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:378: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsScreenOptionInfo’
build/cubemodel_options.c:398: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsSetScreenOption’
build/cubemodel_options.c: In function ‘cubemodelOptionsGetScreenOptions’:
build/cubemodel_options.c:563: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:563: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:566: warning: control reaches end of non-void function
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:568: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsInitScreen’
build/cubemodel_options.c: In function ‘cubemodelOptionsFiniScreen’:
build/cubemodel_options.c:604: error: ‘cubemodelPluginVTable’ undeclared (first use in this function)
build/cubemodel_options.c:604: error: (Each undeclared identifier is reported only once
build/cubemodel_options.c:604: error: for each function it appears in.)
build/cubemodel_options.c:605: warning: ‘return’ with a value, in function returning void
build/cubemodel_options.c:607: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:607: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:610: warning: implicit declaration of function ‘compFiniScreenOptions’
build/cubemodel_options.c:610: warning: nested extern declaration of ‘compFiniScreenOptions’
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:615: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsInitDisplay’
build/cubemodel_options.c: In function ‘cubemodelOptionsFiniDisplay’:
build/cubemodel_options.c:640: error: ‘cubemodelPluginVTable’ undeclared (first use in this function)
build/cubemodel_options.c:641: warning: ‘return’ with a value, in function returning void
build/cubemodel_options.c:643: error: dereferencing pointer to incomplete type
build/cubemodel_options.c:645: warning: implicit declaration of function ‘freeScreenPrivateIndex’
build/cubemodel_options.c:645: warning: nested extern declaration of ‘freeScreenPrivateIndex’
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:649: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cubemodelOptionsInit’
build/cubemodel_options.c: In function ‘cubemodelOptionsFini’:
build/cubemodel_options.c:666: error: ‘cubemodelPluginVTable’ undeclared (first use in this function)
build/cubemodel_options.c:667: warning: ‘return’ with a value, in function returning void
build/cubemodel_options.c:670: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
build/cubemodel_options.c:670: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
build/cubemodel_options.c: At top level:
build/cubemodel_options.c:681: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/cubemodel_options.lo] Error 1

``` 
I have had this problem before and solved it but I can't remember how.:(
Can anyone help me? or refer me to a thread which could help?

thanks 
henry

---

