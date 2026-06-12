---
title: "Engage doesn't work"
date: 2006-11-08
forum: Desktop Environments
---

### Post by L3oN on 2006-11-08
Hi, i've just installed engage from this repository: ```
deb http://soulmachine.net/breezy/ unstable/
```

This is procedure:```
sudo apt-get install engage edb-tools edje0-bin embryo0-bin epeg0-bin esmart0-bin evas0-bin ewl0-bin epsilon0-bin

```And created the .e/ and .engage/ directory with the new **.desktop** files.

It should be all right, but when i tried to start engage, it broken:```
l3on@SubMission:~$ engage 
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_engine_new();

Given engine name dosen't exist.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_init();

Unable to initialize engine.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_destroy();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_title_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_name_class_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_borderless_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_shaped_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_post_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_pre_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_delete_request_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_in_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_focus_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_get()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!

Segmentation fault
l3on@SubMission:~$ 
```

Please HELP me ](*,)

---

