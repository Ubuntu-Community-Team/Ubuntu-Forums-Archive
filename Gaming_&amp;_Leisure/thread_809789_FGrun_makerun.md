---
title: "FGrun make/run"
date: 2008-05-27
forum: Gaming &amp; Leisure
---

### Post by frankstrudel on 2008-05-27
Hi, running Hardy, got fgfs working, would love fgrun to work.

First tried compiling it, but it refused to make... 
./configure seemed to go fine;

....
configure: creating ./config.status
config.status: creating po/Makefile.in
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile

make then goes crazy, doing tons of stuff similar to;

wizard.cxx:309: error: &#8216;Fl_Help_View&#8217; was not declared in this scope
wizard.cxx:309: error: &#8216;about_&#8217; was not declared in this scope
wizard.cxx:309: error: expected type-specifier before &#8216;Fl_Help_View&#8217;
wizard.cxx:309: error: expected `;' before &#8216;Fl_Help_View&#8217;
wizard.cxx:310: error: &#8216;FL_NO_LABEL&#8217; was not declared in this scope
wizard.cxx:312: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;
AirportBrowser.h:37: error: forward declaration of &#8216;struct Fl_Input&#8217;
wizard.cxx:313: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;
AirportBrowser.h:37: error: forward declaration of &#8216;struct Fl_Input&#8217;
wizard.cxx:314: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;
AirportBrowser.h:37: error: forward declaration of &#8216;struct Fl_Input&#8217;
wizard.cxx:315: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;
AirportBrowser.h:37: error: forward declaration of &#8216;struct Fl_Input&#8217;
wizard.cxx:316: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;
AirportBrowser.h:37: error: forward declaration of &#8216;struct Fl_Input&#8217;
wizard.cxx:316: error: &#8216;Fl_Callback&#8217; was not declared in this scope
wizard.cxx:316: error: expected primary-expression before &#8216;)&#8217; token
wizard.cxx:317: error: invalid use of incomplete type &#8216;struct Fl_Input&#8217;

...

wizard.cxx:634: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:635: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:636: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:636: error: &#8216;Fl_Callback&#8217; was not declared in this scope
wizard.cxx:636: error: expected primary-expression before &#8216;)&#8217; token
wizard.cxx:638: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:639: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:640: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:640: error: &#8216;Fl_Callback&#8217; was not declared in this scope
wizard.cxx:640: error: expected primary-expression before &#8216;)&#8217; token
wizard.cxx:642: error: &#8216;Fl_Box&#8217; was not declared in this scope
wizard.cxx:642: error: expected type-specifier before &#8216;Fl_Box&#8217;
wizard.cxx:642: error: expected `;' before &#8216;Fl_Box&#8217;
wizard.cxx:643: error: &#8216;Fl_Group&#8217; is not a class or namespace
wizard.cxx:645: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:646: error: invalid use of incomplete type &#8216;struct Fl_Button&#8217;
AirportBrowser.h:39: error: forward declaration of &#8216;struct Fl_Button&#8217;
wizard.cxx:646: error: &#8216;Fl_Callback&#8217; was not declared in this scope
wizard.cxx:646: error: expected primary-expression before &#8216;)&#8217; token
wizard.cxx: At global scope:
wizard.cxx:654: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
make[2]: *** [wizard.o] Error 1
make[2]: Leaving directory `/home/frank/Desktop/fgrun-1.0.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/frank/Desktop/fgrun-1.0.1/src'
make: *** [all-recursive] Error 1

but that is all that i can copy across...

Then I got rid of that, having found the viciouslime deb for fgrun. That just hangs at

(Reading database ... 135213 files and directories currently installed.)
Preparing to replace fgrun 0.4.8-0ubuntu1 (using .../fgrun_0.4.8-0ubuntu1_i386.deb) ...
Unpacking replacement fgrun ...
Setting up fgrun (0.4.8-0ubuntu1) ...

Although, there does appear to be a new FlightGear icon/launcher in Applications/Games... doesn't do anything insofar as i can tell though.

I can't help but feel I've screwed something up... can anyone fathom what it is? Even better, does anyone know how to fix it?

Thanks

Frank

---

### Post by frankstrudel on 2008-05-27
P.S. Sorry for the super-long error dump 8-[

---

