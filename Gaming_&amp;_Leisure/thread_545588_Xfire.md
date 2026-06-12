---
title: "Xfire"
date: 2007-09-07
forum: Gaming &amp; Leisure
---

### Post by diablo7806 on 2007-09-07
I have followed this tutorial best i can:

```
http://ubuntuforums.org/showthread.php?t=226456&highlight=xfire
```

No matter what i do, i get this:

```
ubuntu@ubuntu:~/Desktop/gaim-xfire-0.5.8$ make
make  all-recursive
make[1]: Entering directory `/home/ubuntu/Desktop/gaim-xfire-0.5.8'
Making all in src
make[2]: Entering directory `/home/ubuntu/Desktop/gaim-xfire-0.5.8/src'
/bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"      -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include            -Wall -g3 -c xfire.c
xfire.c:20:22: error: internal.h: No such file or directory
In file included from xfire.c:37:
x_packets.h:32:49: warning: no newline at end of file
xfire.c: In function 'xfire_update_buddy':
xfire.c:113: warning: implicit declaration of function 'serv_got_update'
xfire.c:115: error: 'UC_UNAVAILABLE' undeclared (first use in this function)
xfire.c:115: error: (Each undeclared identifier is reported only once
xfire.c:115: error: for each function it appears in.)
xfire.c: At top level:
xfire.c:122: error: expected declaration specifiers or '...' before 'GaimConvImFlags'
xfire.c: In function 'xfire_send_im':
xfire.c:141: warning: implicit declaration of function 'strlen'
xfire.c:141: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:148: warning: implicit declaration of function 'strncpy'
xfire.c:148: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_login_salt':
xfire.c:192: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_check_buddy_im':
xfire.c:232: warning: implicit declaration of function 'memcmp'
xfire.c: In function 'xfire_check_buddy_status':
xfire.c:298: warning: implicit declaration of function 'strncmp'
xfire.c:298: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_get_im':
xfire.c:316: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:330: warning: implicit declaration of function 'memcpy'
xfire.c:330: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:359: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_buddy_online':
xfire.c:408: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:409: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c: In function 'xfire_read_buddys':
xfire.c:446: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:451: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:453: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:456: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_invitation':
xfire.c:496: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:502: warning: implicit declaration of function '_'
xfire.c:504: warning: passing argument 1 of 'g_strdup_printf' makes pointer from integer without a cast
xfire.c: In function 'xfire_new_buddy':
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_rem_buddy':
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_read_status':
xfire.c:565: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:570: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_game_status':
xfire.c:606: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:606: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:607: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:607: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:608: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:608: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:609: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:609: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c: In function 'xfire_login_check':
xfire.c:635: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:639: warning: implicit declaration of function 'strcmp'
xfire.c: In function 'xfire_packet_handler':
xfire.c:674: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:690: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c:712: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_login_connect':
xfire.c:833: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_login':
xfire.c:855: warning: passing argument 2 of 'gaim_connection_update_progress' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
xfire.c:861: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: error: too few arguments to function 'gaim_proxy_connect'
xfire.c:862: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_list_emblems':
xfire.c:878: error: 'GaimBuddy' has no member named 'present'
xfire.c:878: error: 'GAIM_BUDDY_OFFLINE' undeclared (first use in this function)
xfire.c: In function 'xfire_set_away':
xfire.c:917: warning: passing argument 2 of 'xfire_create_away' discards qualifiers from pointer target type
xfire.c:922: warning: passing argument 2 of 'xfire_create_away' makes pointer from integer without a cast
xfire.c: In function 'xfire_away_states':
xfire.c:943: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c:944: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c: In function 'xfire_prpl_tooltip_text':
xfire.c:970: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
xfire.c: At top level:
xfire.c:999: warning: initialization from incompatible pointer type
xfire.c:1001: warning: initialization from incompatible pointer type
xfire.c:1002: warning: initialization from incompatible pointer type
xfire.c:1008: warning: initialization from incompatible pointer type
xfire.c:1012: warning: initialization from incompatible pointer type
xfire.c:1067: error: 'VERSION' undeclared here (not in a function)
xfire.c:1069: warning: implicit declaration of function 'N_'
xfire.c:1069: error: initializer element is not constant
xfire.c:1069: error: (near initialization for 'info.summary')
xfire.c:1071: error: initializer element is not constant
xfire.c:1071: error: (near initialization for 'info.description')
xfire.c:1073: error: 'GAIM_WEBSITE' undeclared here (not in a function)
xfire.c: In function 'init_plugin':
xfire.c:1089: warning: passing argument 1 of 'gaim_account_option_string_new' makes pointer from integer without a cast
xfire.c:1092: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
xfire.c:1095: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
make[2]: *** [xfire.lo] Error 1
make[2]: Leaving directory `/home/ubuntu/Desktop/gaim-xfire-0.5.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/gaim-xfire-0.5.8'
make: *** [all-recursive-am] Error 2

```

I'm so confused.... :confused:

---

### Post by Cappy on 2007-09-07
Look here:
[http://ubuntuforums.org/showthread.php?t=504661](http://ubuntuforums.org/showthread.php?t=504661)

and here:
[http://ubuntuforums.org/showthread.php?t=540903](http://ubuntuforums.org/showthread.php?t=540903)

and here:
[http://ubuntuforums.org/showthread.php?t=535566](http://ubuntuforums.org/showthread.php?t=535566)

and customization information here:
[http://ubuntuforums.org/showthread.php?t=397255](http://ubuntuforums.org/showthread.php?t=397255)

---

