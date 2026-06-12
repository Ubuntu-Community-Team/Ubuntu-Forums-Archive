---
title: "seamonkey compile"
date: 2005-12-31
forum: General Help
---

### Post by ram32 on 2005-12-31
hi all!! happy new year!! good luck for everyone!! ;) 

my problem: i try to compile seamonkey beta, i have my .mozconf file from official site script, and when i try to```
make -f client.mk build
``` it prints:
```
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:554: warning: implicit declaration of function ‘XtAppCreateShell’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:555: error: ‘applicationShellWidgetClass’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:556: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:558: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:562: error: ‘args’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:562: error: ‘XtNheight’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:563: error: ‘XtNwidth’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:566: warning: implicit declaration of function ‘XtVaCreateWidget’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:567: error: ‘compositeWidgetClass’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:573: error: ‘XtNvisual’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:573: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:574: error: ‘XtNdepth’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:574: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:575: error: ‘XtNcolormap’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:575: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:576: error: ‘XtNborderWidth’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:579: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:580: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:585: warning: implicit declaration of function ‘XtRegisterDrawable’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:585: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:592: warning: implicit declaration of function ‘XtRealizeWidget’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:595: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:600: warning: implicit declaration of function ‘XtManageChild’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:601: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:604: warning: implicit declaration of function ‘XtAddEventHandler’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:607: error: ‘XtEventHandler’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:607: error: syntax error before ‘xt_client_event_handler’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:611: error: syntax error before ‘xt_client_focus_listener’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:613: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_unrealize’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:620: warning: implicit declaration of function ‘XtUnregisterDrawable’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:620: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:621: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:629: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:631: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:631: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:632: warning: implicit declaration of function ‘XtUnrealizeWidget’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:632: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_destroy’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:638: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:639: warning: implicit declaration of function ‘XtRemoveEventHandler’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:639: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:640: error: ‘XtEventHandler’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:640: error: syntax error before ‘xt_client_event_handler’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:641: warning: implicit declaration of function ‘XtDestroyWidget’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:641: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:642: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:647: error: syntax error before ‘xtplug’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_set_info’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:651: warning: implicit declaration of function ‘XtDisplay’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:651: error: ‘xtplug’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:651: warning: passing argument 1 of ‘XInternAtom’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:654: error: ‘flags’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:659: warning: passing argument 1 of ‘XChangeProperty’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:663: error: syntax error before ‘w’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_handle_xembed_message’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:665: error: ‘client_data’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:666: error: ‘event’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:694: warning: implicit declaration of function ‘memset’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:694: warning: incompatible implicit declaration of built-in function ‘memset’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:709: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:710: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:710: warning: assignment makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:711: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:714: warning: passing argument 1 of ‘XSendEvent’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:715: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:715: warning: passing argument 1 of ‘XSync’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:724: error: syntax error before ‘w’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_event_handler’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:726: error: ‘client_data’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:728: error: ‘event’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:733: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:734: warning: passing argument 1 of ‘XInternAtom’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:735: error: ‘w’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘send_xembed_message’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:771: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:772: error: dereferencing pointer to incomplete type
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:775: warning: incompatible implicit declaration of built-in function ‘memset’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:824: error: syntax error before ‘w’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_client_focus_listener’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:826: error: ‘w’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:826: warning: initialization makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:827: error: ‘user_data’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:830: error: ‘event’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:834: error: ‘Widget’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:834: error: syntax error before ‘child’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:835: error: ‘child’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:845: error: syntax error before ‘child’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:869: error: syntax error before ‘w’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_add_focus_listener’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:873: error: ‘user_data’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:877: error: ‘w’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:877: warning: passing argument 1 of ‘XGetWindowAttributes’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:881: warning: passing argument 1 of ‘XSelectInput’ makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:886: error: ‘XtEventHandler’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:886: error: syntax error before ‘xt_client_focus_listener’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:892: error: syntax error before ‘w’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_remove_focus_listener’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:897: error: ‘w’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:898: error: ‘XtEventHandler’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:898: error: syntax error before ‘xt_client_focus_listener’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: At top level:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:904: error: syntax error before ‘treeroot’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c: In function ‘xt_add_focus_listener_tree’:
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:906: error: ‘treeroot’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:909: warning: initialization makes pointer from integer without a cast
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:913: error: ‘user_data’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:925: error: ‘Widget’ undeclared (first use in this function)
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:925: error: syntax error before ‘child’
/home/ram32/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:926: error: ‘child’ undeclared (first use in this function)
make[3]: *** [gtk2xtbin.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[3]: Leaving directory `/home/ram32/mozilla/obj-i686-pc-linux-gnu/widget/src/gtkxtbin'
make[2]: *** [tier_9] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[2]: Leaving directory `/home/ram32/mozilla/obj-i686-pc-linux-gnu'
make[1]: *** [default] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: Leaving directory `/home/ram32/mozilla/obj-i686-pc-linux-gnu'
make: *** [build] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2


```

---

### Post by Sef on 2006-01-04
Have you checked the Seamonkey IRC to see if someone can help you?

[http://wiki.mozilla.org/SeaMonkey:Supporters]("http://wiki.mozilla.org/SeaMonkey:Supporters")

---

### Post by ram32 on 2006-01-04
thanks, i have already soluted this problem!
Mozilla/5.0 (X11; U; Linux i686; ru-RU; rv:1.8) Gecko/20060103 SeaMonkey/1.0b :)

---

### Post by Sef on 2006-01-08
How did you solve the problem?

---

### Post by DaMasta on 2006-01-08
I didn't have to compile mine. It's like firefox, uncompress and ./seamonkey.

---

### Post by ram32 on 2006-01-09
2 Sef: I didn't remember. I opened Synaptic and install smth. 
2 DaMasta: No, I have downloaded sources!
Sorry for my English :)

---

### Post by Jakanden on 2006-02-02
I am attemtpting to install the newest Seamonkey and I ran gunzip to turn it into a tar file but when I run tar -x it just hangs. I attempt to doubleclick the file and I get the following:

In Nautilus: "Couldn't display "/home/jakanden/seamonkey-1.0.en-US.linux-i686.installer.tar"
In Rox: "No run action specified for files of this type (application/x-tar) - you can set a run action by choosing `Set Run Action' from the File menu, or you can just drag the file to an application"

I am using XFCE due to full ubuntu running slow on my Laptop. Any ideas? I tried searching the repositories for seamonkey and could not locate it,

---

### Post by z_diver on 2006-02-02
If you want to do it from the command line, just run >tar -xf.  However, I just downloaded seamonkey from mozilla's site and UNZIPPED it in my bin directory inside my home directory.  I then made a custom launcher for the executable file (/home/myhome/bin/seamonkeyseamonkey) and it works great.

---

### Post by Jakanden on 2006-02-02
Unfortunately that is my problem as said above. I am unable to unzip it =)

---

