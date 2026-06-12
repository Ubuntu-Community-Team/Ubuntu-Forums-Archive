---
title: "Error when install StarDict"
date: 2006-02-17
forum: Desktop Environments
---

### Post by vn7xmen on 2006-02-17
Dear all
I want to install StarDict in Ubutun 5.10. There are some error when I type 'make'. Could you tell me how to fix error. Thanks for supporting.
Regards

-MP -MF ".deps/stardict-application-server.Tpo" -c -o stardict-application-serve r.o stardict-application-server.cpp; \
then mv -f ".deps/stardict-application-server.Tpo" ".deps/stardict-application-s erver.Po"; else rm -f ".deps/stardict-application-server.Tpo"; exit 1; fi
/usr/include/libintl.h:40: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:40: error: expected `)' before ‘const’
/usr/include/libintl.h:40: error: expected initializer before ‘const’
/usr/include/libintl.h:44: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:44: error: expected `)' before ‘const’
/usr/include/libintl.h:44: error: expected initializer before ‘const’
/usr/include/libintl.h:51: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:51: error: expected `)' before ‘const’
/usr/include/libintl.h:51: error: expected initializer before ‘const’
/usr/include/libintl.h:81: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:81: error: expected `)' before ‘const’
/usr/include/libintl.h:81: error: expected initializer before ‘const’
/usr/include/libintl.h:85: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:85: error: expected `)' before ‘const’
/usr/include/libintl.h:85: error: expected initializer before ‘const’
/usr/include/libintl.h:90: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:90: error: expected `)' before ‘const’
/usr/include/libintl.h:90: error: expected initializer before ‘const’
make[3]: *** [stardict-application-server.o] Error 1
make[3]: Leaving directory `/home/ubt/application/stardict/stardict-2.4.6/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ubt/application/stardict/stardict-2.4.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubt/application/stardict/stardict-2.4.6'
make: *** [all] Error 2

---

