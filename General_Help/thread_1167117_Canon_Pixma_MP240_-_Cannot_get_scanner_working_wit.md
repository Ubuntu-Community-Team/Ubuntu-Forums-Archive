---
title: "Canon Pixma MP240 - Cannot get scanner working with xsane"
date: 2009-05-22
forum: General Help
---

### Post by sumpm1 on 2009-05-22
Hey guys. I am running 9.04 and am trying to get my Pixma MP240 working as a scanner with xsane. I had this working in 8.10, I followed these directions: [http://ubuntuforums.org/showpost.php?p=6607862&postcount=27](http://ubuntuforums.org/showpost.php?p=6607862&postcount=27)

I have installed sane and xsane. I download sane-scm-latest.tar.gz from the link, extract and run the ./configure command; works fine, no errors.

Then I run make and get this error:

```
Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-teco2.la  libsane_teco2_la-teco2-s.lo ../lib/liblib.la libteco2.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo ../sanei/sanei_config2.lo sane_strstatus.lo ../sanei/sanei_scsi.lo  
rm -f teco3-s.c
ln -s ./stubs.c teco3-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=teco3 -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_teco3_la-teco3-s.lo -MD -MP -MF .deps/libsane_teco3_la-teco3-s.Tpo -c -o libsane_teco3_la-teco3-s.lo `test -f 'teco3-s.c' || echo './'`teco3-s.c
mv -f .deps/libsane_teco3_la-teco3-s.Tpo .deps/libsane_teco3_la-teco3-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=teco3 -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libteco3_la-teco3.lo -MD -MP -MF .deps/libteco3_la-teco3.Tpo -c -o libteco3_la-teco3.lo `test -f 'teco3.c' || echo './'`teco3.c
teco3.c: In function ‘teco_init_options’:
teco3.c:1064: warning: cast discards qualifiers from pointer target type
mv -f .deps/libteco3_la-teco3.Tpo .deps/libteco3_la-teco3.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libteco3.la  libteco3_la-teco3.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-teco3.la  libsane_teco3_la-teco3-s.lo ../lib/liblib.la libteco3.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo ../sanei/sanei_config2.lo sane_strstatus.lo ../sanei/sanei_scsi.lo  
rm -f test-s.c
ln -s ./stubs.c test-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=test -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_test_la-test-s.lo -MD -MP -MF .deps/libsane_test_la-test-s.Tpo -c -o libsane_test_la-test-s.lo `test -f 'test-s.c' || echo './'`test-s.c
mv -f .deps/libsane_test_la-test-s.Tpo .deps/libsane_test_la-test-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=test -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libtest_la-test.lo -MD -MP -MF .deps/libtest_la-test.Tpo -c -o libtest_la-test.lo `test -f 'test.c' || echo './'`test.c
mv -f .deps/libtest_la-test.Tpo .deps/libtest_la-test.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libtest.la  libtest_la-test.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-test.la  libsane_test_la-test-s.lo ../lib/liblib.la libtest.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo  sane_strstatus.lo ../sanei/sanei_thread.lo  
rm -f u12-s.c
ln -s ./stubs.c u12-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=u12 -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_u12_la-u12-s.lo -MD -MP -MF .deps/libsane_u12_la-u12-s.Tpo -c -o libsane_u12_la-u12-s.lo `test -f 'u12-s.c' || echo './'`u12-s.c
mv -f .deps/libsane_u12_la-u12-s.Tpo .deps/libsane_u12_la-u12-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=u12 -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libu12_la-u12.lo -MD -MP -MF .deps/libu12_la-u12.Tpo -c -o libu12_la-u12.lo `test -f 'u12.c' || echo './'`u12.c
u12.c: In function ‘reader_process’:
u12.c:365: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
mv -f .deps/libu12_la-u12.Tpo .deps/libu12_la-u12.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libu12.la  libu12_la-u12.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-u12.la  libsane_u12_la-u12-s.lo ../lib/liblib.la libu12.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo  sane_strstatus.lo ../sanei/sanei_usb.lo ../sanei/sanei_thread.lo -lm   
rm -f umax-s.c
ln -s ./stubs.c umax-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_umax_la-umax-s.lo -MD -MP -MF .deps/libsane_umax_la-umax-s.Tpo -c -o libsane_umax_la-umax-s.lo `test -f 'umax-s.c' || echo './'`umax-s.c
mv -f .deps/libsane_umax_la-umax-s.Tpo .deps/libsane_umax_la-umax-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libumax_la-umax.lo -MD -MP -MF .deps/libumax_la-umax.Tpo -c -o libumax_la-umax.lo `test -f 'umax.c' || echo './'`umax.c
mv -f .deps/libumax_la-umax.Tpo .deps/libumax_la-umax.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libumax.la  libumax_la-umax.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-umax.la  libsane_umax_la-umax-s.lo ../lib/liblib.la libumax.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo ../sanei/sanei_config2.lo sane_strstatus.lo ../sanei/sanei_usb.lo ../sanei/sanei_thread.lo ../sanei/sanei_scsi.lo ../sanei/sanei_pv8630.lo -lm    
rm -f umax_pp-s.c
ln -s ./stubs.c umax_pp-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax_pp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_umax_pp_la-umax_pp-s.lo -MD -MP -MF .deps/libsane_umax_pp_la-umax_pp-s.Tpo -c -o libsane_umax_pp_la-umax_pp-s.lo `test -f 'umax_pp-s.c' || echo './'`umax_pp-s.c
mv -f .deps/libsane_umax_pp_la-umax_pp-s.Tpo .deps/libsane_umax_pp_la-umax_pp-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax_pp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libumax_pp_la-umax_pp.lo -MD -MP -MF .deps/libumax_pp_la-umax_pp.Tpo -c -o libumax_pp_la-umax_pp.lo `test -f 'umax_pp.c' || echo './'`umax_pp.c
umax_pp.c: In function ‘sane_umax_pp_exit’:
umax_pp.c:1002: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
umax_pp.c:1003: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
umax_pp.c:1004: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
mv -f .deps/libumax_pp_la-umax_pp.Tpo .deps/libumax_pp_la-umax_pp.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax_pp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libumax_pp_la-umax_pp_low.lo -MD -MP -MF .deps/libumax_pp_la-umax_pp_low.Tpo -c -o libumax_pp_la-umax_pp_low.lo `test -f 'umax_pp_low.c' || echo './'`umax_pp_low.c
mv -f .deps/libumax_pp_la-umax_pp_low.Tpo .deps/libumax_pp_la-umax_pp_low.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax_pp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libumax_pp_la-umax_pp_mid.lo -MD -MP -MF .deps/libumax_pp_la-umax_pp_mid.Tpo -c -o libumax_pp_la-umax_pp_mid.lo `test -f 'umax_pp_mid.c' || echo './'`umax_pp_mid.c
mv -f .deps/libumax_pp_la-umax_pp_mid.Tpo .deps/libumax_pp_la-umax_pp_mid.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libumax_pp.la  libumax_pp_la-umax_pp.lo libumax_pp_la-umax_pp_low.lo libumax_pp_la-umax_pp_mid.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-umax_pp.la  libsane_umax_pp_la-umax_pp-s.lo ../lib/liblib.la libumax_pp.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo  sane_strstatus.lo -lm  
rm -f umax1220u-s.c
ln -s ./stubs.c umax1220u-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax1220u -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_umax1220u_la-umax1220u-s.lo -MD -MP -MF .deps/libsane_umax1220u_la-umax1220u-s.Tpo -c -o libsane_umax1220u_la-umax1220u-s.lo `test -f 'umax1220u-s.c' || echo './'`umax1220u-s.c
mv -f .deps/libsane_umax1220u_la-umax1220u-s.Tpo .deps/libsane_umax1220u_la-umax1220u-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=umax1220u -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libumax1220u_la-umax1220u.lo -MD -MP -MF .deps/libumax1220u_la-umax1220u.Tpo -c -o libumax1220u_la-umax1220u.lo `test -f 'umax1220u.c' || echo './'`umax1220u.c
mv -f .deps/libumax1220u_la-umax1220u.Tpo .deps/libumax1220u_la-umax1220u.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libumax1220u.la  libumax1220u_la-umax1220u.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-umax1220u.la  libsane_umax1220u_la-umax1220u-s.lo ../lib/liblib.la libumax1220u.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo  sane_strstatus.lo ../sanei/sanei_usb.lo ../sanei/sanei_pv8630.lo -lm   
rm -f xerox_mfp-s.c
ln -s ./stubs.c xerox_mfp-s.c
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=xerox_mfp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_xerox_mfp_la-xerox_mfp-s.lo -MD -MP -MF .deps/libsane_xerox_mfp_la-xerox_mfp-s.Tpo -c -o libsane_xerox_mfp_la-xerox_mfp-s.lo `test -f 'xerox_mfp-s.c' || echo './'`xerox_mfp-s.c
mv -f .deps/libsane_xerox_mfp_la-xerox_mfp-s.Tpo .deps/libsane_xerox_mfp_la-xerox_mfp-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=xerox_mfp -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libxerox_mfp_la-xerox_mfp.lo -MD -MP -MF .deps/libxerox_mfp_la-xerox_mfp.Tpo -c -o libxerox_mfp_la-xerox_mfp.lo `test -f 'xerox_mfp.c' || echo './'`xerox_mfp.c
xerox_mfp.c: In function ‘sane_xerox_mfp_init’:
xerox_mfp.c:941: warning: ISO C forbids conversion of function pointer to object pointer type
mv -f .deps/libxerox_mfp_la-xerox_mfp.Tpo .deps/libxerox_mfp_la-xerox_mfp.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs  -o libxerox_mfp.la  libxerox_mfp_la-xerox_mfp.lo  
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-xerox_mfp.la  libsane_xerox_mfp_la-xerox_mfp-s.lo ../lib/liblib.la libxerox_mfp.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo  sane_strstatus.lo ../sanei/sanei_usb.lo -lm   
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DLIBDIR="/usr/lib/sane" -DBACKEND_NAME=dll -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT libsane_dll_la-dll-s.lo -MD -MP -MF .deps/libsane_dll_la-dll-s.Tpo -c -o libsane_dll_la-dll-s.lo `test -f 'dll-s.c' || echo './'`dll-s.c
mv -f .deps/libsane_dll_la-dll-s.Tpo .deps/libsane_dll_la-dll-s.Plo
/bin/bash ../libtool --silent --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -Wl,-z,defs -rpath '/usr/lib/sane' -version-number 1:0:21 -module  -o libsane-dll.la -rpath /usr/lib/sane libsane_dll_la-dll-s.lo ../lib/liblib.la libdll.la ../sanei/sanei_init_debug.lo ../sanei/sanei_constrain_value.lo ../sanei/sanei_config.lo sane_strstatus.lo -ldl  
make[2]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/backend'
make[1]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/backend'
Making all in frontend
make[1]: Entering directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/frontend'
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT scanimage.o -MD -MP -MF .deps/scanimage.Tpo -c -o scanimage.o scanimage.c
scanimage.c: In function ‘auth_callback’:
scanimage.c:276: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scanimage.c: In function ‘main’:
scanimage.c:1859: warning: format not a string literal and no format arguments
scanimage.c:1873: warning: format not a string literal and no format arguments
mv -f .deps/scanimage.Tpo .deps/scanimage.Po
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT stiff.o -MD -MP -MF .deps/stiff.Tpo -c -o stiff.o stiff.c
mv -f .deps/stiff.Tpo .deps/stiff.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o scanimage scanimage.o stiff.o ../lib/liblib.la ../lib/libfelib.la ../backend/libsane.la 
mkdir .libs
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o .libs/scanimage scanimage.o stiff.o  ../lib/.libs/liblib.a ../lib/.libs/libfelib.a ../backend/.libs/libsane.so -ldl -lm -lpthread 
creating scanimage
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT saned.o -MD -MP -MF .deps/saned.Tpo -c -o saned.o saned.c
saned.c: In function ‘auth_callback’:
saned.c:358: warning: cast discards qualifiers from pointer target type
saned.c:368: warning: cast discards qualifiers from pointer target type
saned.c:379: warning: cast discards qualifiers from pointer target type
saned.c: In function ‘process_request’:
saned.c:1943: warning: cast discards qualifiers from pointer target type
saned.c: In function ‘run_standalone’:
saned.c:3010: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
mv -f .deps/saned.Tpo .deps/saned.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o saned saned.o ../sanei/libsanei.la ../lib/liblib.la ../lib/libfelib.la ../backend/libsane.la  
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o .libs/saned saned.o  ../sanei/.libs/libsanei.a ../lib/.libs/liblib.a ../lib/.libs/libfelib.a ../backend/.libs/libsane.so -ldl -lm -lpthread 
creating saned
make[1]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/frontend'
Making all in tools
make[1]: Entering directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/tools'
for subdir in hal hotplug hotplug-ng udev; do \
	  /bin/mkdir -p $subdir || exit 1; \
	  done
make  all-am
make[2]: Entering directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/tools'
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT sane-find-scanner.o -MD -MP -MF .deps/sane-find-scanner.Tpo -c -o sane-find-scanner.o sane-find-scanner.c
mv -f .deps/sane-find-scanner.Tpo .deps/sane-find-scanner.Po
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT check-usb-chip.o -MD -MP -MF .deps/check-usb-chip.Tpo -c -o check-usb-chip.o check-usb-chip.c
check-usb-chip.c:3400: warning: ISO C forbids an empty source file
mv -f .deps/check-usb-chip.Tpo .deps/check-usb-chip.Po
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT sane_strstatus.o -MD -MP -MF .deps/sane_strstatus.Tpo -c -o sane_strstatus.o `test -f '../backend/sane_strstatus.c' || echo './'`../backend/sane_strstatus.c
mv -f .deps/sane_strstatus.Tpo .deps/sane_strstatus.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o sane-find-scanner sane-find-scanner.o check-usb-chip.o sane_strstatus.o ../sanei/libsanei.la ../lib/liblib.la  
mkdir .libs
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o sane-find-scanner sane-find-scanner.o check-usb-chip.o sane_strstatus.o  ../sanei/.libs/libsanei.a ../lib/.libs/liblib.a  
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT gamma4scanimage.o -MD -MP -MF .deps/gamma4scanimage.Tpo -c -o gamma4scanimage.o gamma4scanimage.c
mv -f .deps/gamma4scanimage.Tpo .deps/gamma4scanimage.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o gamma4scanimage gamma4scanimage.o -lm 
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o gamma4scanimage gamma4scanimage.o  -lm  
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT sane-desc.o -MD -MP -MF .deps/sane-desc.Tpo -c -o sane-desc.o sane-desc.c
mv -f .deps/sane-desc.Tpo .deps/sane-desc.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o sane-desc sane-desc.o ../sanei/libsanei.la ../lib/liblib.la 
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o sane-desc sane-desc.o  ../sanei/.libs/libsanei.a ../lib/.libs/liblib.a  
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DBACKEND_NAME=umax_pp_low -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT umax_pp-umax_pp.o -MD -MP -MF .deps/umax_pp-umax_pp.Tpo -c -o umax_pp-umax_pp.o `test -f 'umax_pp.c' || echo './'`umax_pp.c
umax_pp.c: In function ‘main’:
umax_pp.c:328: warning: implicit declaration of function ‘putenv’
mv -f .deps/umax_pp-umax_pp.Tpo .deps/umax_pp-umax_pp.Po
gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I. -I../include -I../include -DBACKEND_NAME=umax_pp_low -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/etc/sane.d 	  -DPATH_SANE_DATA_DIR=/usr/share 	  -DPATH_SANE_LOCK_DIR=/var/lock/sane 	  -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -MT umax_pp-umax_pp_low.o -MD -MP -MF .deps/umax_pp-umax_pp_low.Tpo -c -o umax_pp-umax_pp_low.o `test -f '../backend/umax_pp_low.c' || echo './'`../backend/umax_pp_low.c
mv -f .deps/umax_pp-umax_pp_low.Tpo .deps/umax_pp-umax_pp_low.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi   -o umax_pp umax_pp-umax_pp.o umax_pp-umax_pp_low.o ../sanei/libsanei.la ../lib/liblib.la -lm 
gcc -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wreturn-type -Wstrict-prototypes -pedantic -ansi -o umax_pp umax_pp-umax_pp.o umax_pp-umax_pp_low.o  ../sanei/.libs/libsanei.a ../lib/.libs/liblib.a -lm  
ma1509.desc: Warning: Backend `ma1509': 1 USB devices without :usbid
epson2.desc: Warning: Backend `epson2': 1 USB devices without :usbid
unsupported.desc: Warning: Backend `unsupported': 34 USB devices without :usbid
snapscan.desc: Warning: Backend `SnapScan': 1 USB devices without :usbid
fujitsu.desc: Warning: Backend `fujitsu': 1 USB devices without :usbid
hp5400.desc: Warning: Backend `hp5400': 1 USB devices without :usbid
canon_dr.desc: Warning: Backend `canon_dr': 2 USB devices without :usbid
umax.desc: Warning: Backend `umax': 1 USB devices without :usbid
viceo.desc: Warning: Backend `viceo': 1 USB devices without :usbid
epkowa.desc: Warning: Backend `epkowa': `EPSON' `ES-1000C' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `GT-4000' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `GT-8500' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-7900CS' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9000CCH' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9000CCS' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9000CFH' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9500CCS' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9500CFH' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9500CH2' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9800CCH' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9800CCS' does not have an interface
epkowa.desc: Warning: Backend `epkowa': `EPSON' `LP-9800CFH' does not have an interface
epkowa.desc: Warning: Backend `epkowa': 8 USB devices without :usbid
brother2.desc: Warning: Backend `brother2': 9 USB devices without :usbid
brother.desc: Warning: Backend `brother': 1 USB devices without :usbid
samsung.desc: Warning: Backend `samsung': 7 USB devices without :usbid
make[2]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/tools'
make[1]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/tools'
Making all in doc
make[1]: Entering directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/doc'
Generating manpage scanimage.1...
Generating manpage sane-config.1...
Generating manpage sane-find-scanner.1...
Generating manpage gamma4scanimage.1...
Generating manpage sane.7...
Generating manpage saned.8...
Generating index for sane.tex...
make[1]: *** [sane.ind] Error 1
make[1]: Leaving directory `/home/dave/Desktop/sane-scm-2009-05-22/sane-backends/doc'
make: *** [all-recursive] Error 1
dave@dave-desktop:~/Desktop/sane-scm-2009-05-22/sane-backends$
```

Obviously "sudo make install" gives errors as well after this. Can anyone provide any insight here?

Thanks.

---

### Post by billybag on 2009-06-25
I too cant get my scanner to work.

---

### Post by EireMob on 2009-06-25
I 3

---

### Post by Shwaman on 2009-07-06
I got this from jmort253**[B]on the** [SOLVED] Canon MP240[/B] thread

open a terminal window and code:

sudo scangearmp

It scans !
I did install the scan drivers from the canon site previously.

I hope this thing with xsane gets addressed.  I am new to Ubuntu, so Im not sure who do ask.

---

