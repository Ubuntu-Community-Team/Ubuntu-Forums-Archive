---
title: "libpri bugs in jaunty"
date: 2009-06-09
forum: General Help
---

### Post by rbueno on 2009-06-09
gcc -Wall -Werror -Wstrict-prototypes -Wmissing-prototypes -g     -c -o q931.o q931.c
In file included from q931.c:27:
pri_internal.h:263: error: expected declaration specifiers or ‘...’ before ‘size_t’
q931.c: In function ‘receive_calling_party_number’:
q931.c:948: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘transmit_keypad_facility’:
q931.c:1424: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘q931_keypad_facility’:
q931.c:2491: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘pri_release_finaltimeout’:
q931.c:2666: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘q931_setup’:
q931.c:2815: error: too many arguments to function ‘libpri_copy_string’
q931.c:2818: error: too many arguments to function ‘libpri_copy_string’
q931.c:2835: error: too many arguments to function ‘libpri_copy_string’
q931.c:2852: error: too many arguments to function ‘libpri_copy_string’
q931.c:2858: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘q931_receive’:
q931.c:3312: error: too many arguments to function ‘libpri_copy_string’
q931.c:3313: error: too many arguments to function ‘libpri_copy_string’
q931.c:3314: error: too many arguments to function ‘libpri_copy_string’
q931.c:3316: error: too many arguments to function ‘libpri_copy_string’
q931.c:3317: error: too many arguments to function ‘libpri_copy_string’
q931.c:3318: error: too many arguments to function ‘libpri_copy_string’
q931.c:3319: error: too many arguments to function ‘libpri_copy_string’
q931.c:3320: error: too many arguments to function ‘libpri_copy_string’
q931.c:3321: error: too many arguments to function ‘libpri_copy_string’
q931.c:3322: error: too many arguments to function ‘libpri_copy_string’
q931.c:3349: error: too many arguments to function ‘libpri_copy_string’
q931.c:3379: error: too many arguments to function ‘libpri_copy_string’
q931.c:3393: error: too many arguments to function ‘libpri_copy_string’
q931.c:3394: error: too many arguments to function ‘libpri_copy_string’
q931.c:3480: error: too many arguments to function ‘libpri_copy_string’
q931.c:3508: error: too many arguments to function ‘libpri_copy_string’
q931.c:3543: error: too many arguments to function ‘libpri_copy_string’
q931.c:3571: error: too many arguments to function ‘libpri_copy_string’
q931.c:3597: error: too many arguments to function ‘libpri_copy_string’
q931.c:3605: error: too many arguments to function ‘libpri_copy_string’
q931.c:3606: error: too many arguments to function ‘libpri_copy_string’
q931.c: In function ‘pri_internal_clear’:
q931.c:3693: error: too many arguments to function ‘libpri_copy_string’
make: *** [q931.o] Error 1


i've got this error when i attempt to sudo make. anybody can help me on how to fix this pls.. thanks in advance

---

