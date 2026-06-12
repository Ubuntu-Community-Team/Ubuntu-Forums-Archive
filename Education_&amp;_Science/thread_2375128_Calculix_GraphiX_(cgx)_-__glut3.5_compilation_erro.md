---
title: "Calculix GraphiX (cgx) -  glut3.5 compilation error"
date: 2017-10-22
forum: Education &amp; Science
---

### Post by cagataycobanoglu25 on 2017-10-22
Hi All,

[FONT=verdana]I am trying to compile the cgx_2.13 source on my Ubuntu 16.04 lts and I got some errors related with glut 3.5  during compilation. I posted some part of my terminal output because it was too long. I am not a frequent user of the forum. If there are any conveniences in the post, warn me please. [/FONT]
[FONT=verdana]  I could not find any solution about this problem on my internet search. It looks like compiler issue but I could clarify it. [/FONT]

```
cagatay@cagatay-PC:/usr/local/calculix/CalculiX/cgx_2.13/src$ sudo make
cc -O2 -Wall -I./ -I/usr/include -I/usr/include/GL -I../../libSNL/src -I../../glut-3.5/src -I/usr/X11/include    -c -o ../../glut-3.5/src/glut_input.o ../../glut-3.5/src/glut_input.c
../../glut-3.5/src/glut_input.c:29:1: error: unknown type name ‘XDevice’
 XDevice *__glutTablet = NULL;
 ^
../../glut-3.5/src/glut_input.c:30:1: error: unknown type name ‘XDevice’
 XDevice *__glutDials = NULL;
 ^
../../glut-3.5/src/glut_input.c:31:1: error: unknown type name ‘XDevice’
 XDevice *__glutSpaceball = NULL;
 ^
../../glut-3.5/src/glut_input.c: In function ‘queryTabletPos’:
../../glut-3.5/src/glut_input.c:99:3: error: unknown type name ‘XDeviceState’
   XDeviceState *state;
   ^
../../glut-3.5/src/glut_input.c:100:3: error: unknown type name ‘XInputClass’
   XInputClass *any;
   ^
../../glut-3.5/src/glut_input.c:101:3: error: unknown type name ‘XValuatorState’
   XValuatorState *v;
   ^
../../glut-3.5/src/glut_input.c:104:11: warning: implicit declaration of function ‘XQueryDeviceState’ [-Wimplicit-function-declaration]
   state = XQueryDeviceState(__glutDisplay, __glutTablet);
           ^
../../glut-3.5/src/glut_input.c:104:9: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
   state = XQueryDeviceState(__glutDisplay, __glutTablet);
         ^
../../glut-3.5/src/glut_input.c:105:14: error: request for member ‘data’ in something not a structure or union
   any = state->data;
              ^
../../glut-3.5/src/glut_input.c:106:24: error: request for member ‘num_classes’ in something not a structure or union
   for (i = 0; i < state->num_classes; i++) {
                        ^
../../glut-3.5/src/glut_input.c:107:16: error: request for member ‘class’ in something not a structure or union
     switch (any->class) {
                ^
../../glut-3.5/src/glut_input.c:109:12: error: ‘XValuatorState’ undeclared (first use in this function)
       v = (XValuatorState *) any;
            ^
../../glut-3.5/src/glut_input.c:109:12: note: each undeclared identifier is reported only once for each function it appears in
../../glut-3.5/src/glut_input.c:109:28: error: expected expression before ‘)’ token
       v = (XValuatorState *) any;
                            ^
../../glut-3.5/src/glut_input.c:110:12: error: request for member ‘num_valuators’ in something not a structure or union
       if (v->num_valuators < 2)
            ^
../../glut-3.5/src/glut_input.c:113:55: error: request for member ‘valuators’ in something not a structure or union
         window->tabletPos[0] = normalizeTabletPos(0, v->valuators[0]);
                                                       ^
../../glut-3.5/src/glut_input.c:115:55: error: request for member ‘valuators’ in something not a structure or union
         window->tabletPos[1] = normalizeTabletPos(1, v->valuators[1]);
                                                       ^
../../glut-3.5/src/glut_input.c:117:12: error: ‘XInputClass’ undeclared (first use in this function)
     any = (XInputClass *) ((char *) any + any->length);
            ^
../../glut-3.5/src/glut_input.c:117:25: error: expected expression before ‘)’ token
     any = (XInputClass *) ((char *) any + any->length);
                         ^
../../glut-3.5/src/glut_input.c:120:3: warning: implicit declaration of function ‘XFreeDeviceState’ [-Wimplicit-function-declaration]
   XFreeDeviceState(state);
   ^
../../glut-3.5/src/glut_input.c: In function ‘__glutProcessDeviceEvents’:
../../glut-3.5/src/glut_input.c:159:5: error: unknown type name ‘XDeviceMotionEvent’
     XDeviceMotionEvent *devmot = (XDeviceMotionEvent *) event;
     ^

```

---

