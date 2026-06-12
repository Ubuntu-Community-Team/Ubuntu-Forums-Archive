---
title: "android ndk error"
date: 2012-10-10
forum: Desktop Environments
---

### Post by mIXpRo on 2012-10-10
hi guys ,
i'm using ubuntu 12.10 beta 2.
before with ubuntu 12.04 i have used android ndk r8 
and it was working just fine .
now with 12.10 beta 2 i tried ndk r8b and ndk r8 , with both producing the same error when trying to build sample code .
the error :
```

:~/Android/android-ndk/samples/san-angeles/jni$ ndk-build 
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
Compile thumb  : sanangeles <= importgl.c
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
make: *** [/home/mixpro/Android/android-ndk/samples/san-angeles/obj/local/armeabi/objs/sanangeles/importgl.o] Error 127

```   

i'm asking this here cause i think its an ubuntu problem .
can someone help pls.
cause until now nobody can answer me .

---

### Post by DeceptiveHornet on 2012-10-10
> **mIXpRo said:**
> hi guys ,
i'm using ubuntu 12.10 beta 2.
before with ubuntu 12.04 i have used android ndk r8 
and it was working just fine .
now with 12.10 beta 2 i tried ndk r8b and ndk r8 , with both producing the same error when trying to build sample code .
the error :
```

:~/Android/android-ndk/samples/san-angeles/jni$ ndk-build 
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
Compile thumb  : sanangeles <= importgl.c
make: /home/mixpro/Android/android-ndk/toolchains/arm-linux-androideabi-4.6/prebuilt/linux-x86/bin/arm-linux-androideabi-gcc: Command not found
make: *** [/home/mixpro/Android/android-ndk/samples/san-angeles/obj/local/armeabi/objs/sanangeles/importgl.o] Error 127

```i'm asking this here cause i think its an ubuntu problem .
can someone help pls.
cause until now nobody can answer me .

Considered trying Ubuntu 12.04 RC instead of the BETA?

---

### Post by mIXpRo on 2012-10-11
u mean 12.10 rc , it's not out yet .

---

### Post by mIXpRo on 2012-10-13
i solved the problem ,
the default compress file manager in ubuntu wasn't extracting symbolic links ,
so i tried : tar jxf filename.tar.bz2
to untar the ndk.tar.bz2 and now it works fine

---

