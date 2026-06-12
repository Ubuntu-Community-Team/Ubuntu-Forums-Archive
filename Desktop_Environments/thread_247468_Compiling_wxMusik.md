---
title: "Compiling wxMusik"
date: 2006-08-30
forum: Desktop Environments
---

### Post by pihbar on 2006-08-30
I got most of the dependencies from the repos, and turned off monkeys audio.
I followed the [compile instructions]("http://musik.berlios.de/?id=compileonlin") and the ccmake part is set up like this:
```
CMAKE_BACKWARDS_COMPATIBILITY    2.2
 CMAKE_BUILD_TYPE                 RelWithDebInfo
 CMAKE_INSTALL_PREFIX             /usr/local
 EXECUTABLE_OUTPUT_PATH
 FLAC_LIBRARY                     /usr/lib/libFLAC.so.7.0.0
 FMOD_LIBRARY                     /usr/local/lib/libfmodex.so.4.04.26
 LIBRARY_OUTPUT_PATH
 MAC_LIBRARY                      OFF
 MUSEPACK_LIBRARY                 /usr/lib/libmpcdec.so.3.1.1
 OPTION_SUPPORT_APE               ON
 OPTION_SUPPORT_FLAC              ON
 OPTION_SUPPORT_MPC               ON
 SQLITE_LIBRARY                   /usr/lib/libsqlite.so.0.8.6
 WXWINDOWS_USE_DEBUG_LIBS         ON
 WXWINDOWS_USE_SHARED_LIBS        OFF
 WXWINDOWS_USE_UNICODE            ON
```

However when I run sudo make, I get this:
```
Scanning dependencies of target replaygain_synthesis
Building C object MUSIKEngine/3rd-Party/replaygain_synthesis/CMakeFiles/replaygain_synthesis.dir/replaygain_synthesis.o
In file included from /home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:40:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:23:27: error: FLAC/ordinals.h: No such file or directory
In file included from /home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:40:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:36: error: syntax error before ‘FLAC__uint64’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:36: warning: no semicolon at end of struct or union
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:44: error: syntax error before ‘}’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:44: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:46: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/../include/share/replaygain_synthesis.h:49: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:41:25: error: FLAC/assert.h: No such file or directory
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:209: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: In function ‘FLAC__replaygain_synthesis__init_dither_context’:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:216: error: ‘shapingtype’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:216: error: (Each undeclared identifier is reported only once/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:216: error: for each function it appears in.)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:218: error: ‘d’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:219: error: ‘bits’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:227: error: ‘FLAC__uint64’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:229: error: ‘FLAC__int64’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:229: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: At top level:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:237: error: syntax error before ‘dither_output_’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:237: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: In function ‘dither_output_’:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:240: error: ‘FLAC__int64’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:240: error: syntax error before ‘val’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:244: error: ‘do_dithering’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:245: error: ‘shapingtype’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:246: error: ‘d’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:247: error: ‘k’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:249: error: ‘Sum’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:250: error: ‘val’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:250: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:250: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:253: error: ‘i’ undeclared (first use in this function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:256: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:256: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:262: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:262: error: syntax error before numeric constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: At top level:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:298: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: In function ‘FLAC__replaygain_synthesis__apply_gain’:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:300: error: syntax error before ‘conv_factors_’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c: At top level:
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:335: error: syntax error before ‘hard_clip_factors_’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:368: error: ‘FLAC__int64’ undeclared here (not in a function)/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:369: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:370: error: syntax error before ‘conv_factor’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:370: error: ‘conv_factors_’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:370: error: ‘target_bps’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:370: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:371: error: syntax error before ‘hard_clip_factor’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:371: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:378: error: ‘scale’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:378: error: ‘source_bps’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:380: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:380: error: ‘data_out’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:380: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:382: error: syntax error before ‘*’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:382: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:385: error: ‘dither_context’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:387: error: syntax error before ‘val64’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:387: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:388: error: syntax error before ‘val32’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:388: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:389: error: syntax error before ‘uval32’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:389: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:390: error: syntax error before ‘twiggle’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:390: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:392: error: syntax error before ‘>’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:392: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:393: error: syntax error before ‘>=’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:393: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:394: error: syntax error before ‘>=’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:394: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:395: error: syntax error before ‘<=’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:395: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:396: error: syntax error before ‘<’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:396: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:397: error: syntax error before ‘(’ token
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:401: warning: initialization makes integer from pointer without a cast
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:401: error: initializer element is not constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:401: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:402: error: conflicting types for ‘input_’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:382: error: previous declaration of ‘input_’ was here
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:402: error: ‘input’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:402: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:403: error: syntax error before ‘for’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:415: error: ‘do_dithering’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:415: error: initializer element is not constant
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:415: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:417: error: ‘FLAC__int32’ undeclared here (not in a function)/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:417: error: syntax error before ‘val64’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:423: error: ‘FLAC__uint32’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:423: error: syntax error before ‘val32’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:444: error: conflicting types for ‘data_out’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:401: error: previous definition of ‘data_out’ was here
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:444: error: ‘FLAC__byte’ undeclared here (not in a function)
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:444: warning: data definition has no type or storage class
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:445: error: conflicting types for ‘data_out’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:444: error: previous definition of ‘data_out’ was here
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:445: error: syntax error before ‘uval32’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:449: error: conflicting types for ‘data_out’
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:445: error: previous definition of ‘data_out’ was here
/home/perun/temp/wxMusik-0.4.2.1/MUSIKEngine/3rd-Party/replaygain_synthesis/replaygain_synthesis.c:449: error: syntax error before ‘uval32’
make[2]: *** [MUSIKEngine/3rd-Party/replaygain_synthesis/CMakeFiles/replaygain_synthesis.dir/replaygain_synthesis.o] Error 1
make[1]: *** [MUSIKEngine/3rd-Party/replaygain_synthesis/CMakeFiles/replaygain_synthesis.dir/all] Error 2
make: *** [all] Error 2
```

I dont really know about this replaygain_synthesis and ive tried disabling flac in ccmake, to no avail. I dont think I'll get a soln, but its worth a shot :P

EDIT:
If you have a deb package, I'll take it :)

---

