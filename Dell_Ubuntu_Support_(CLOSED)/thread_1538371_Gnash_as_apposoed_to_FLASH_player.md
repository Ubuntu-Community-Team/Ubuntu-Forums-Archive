---
title: "Gnash as apposoed to FLASH player"
date: 2010-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dirkyboy on 2010-07-25
Ok.. maby someone can help. I keep getting pop ups to install flash 10 but I have a AMD 64 which isnt supported by flash ten release so I heard about Gnash and downloaded the package file. I tried a ./confugure and installed the necessary compilers that it came up with and then did a make check. Here is the error I am getting. I ran make then got the same error and did an make clean to get rid of the install to start clean. I wanted a flash player opperable from the browser so can anyone help to get the Gnash working
?
s/libgnashbase_la-curl_adapter.o
curl_adapter.cpp:74:23: error: curl/curl.h: No such file or directory
curl_adapter.cpp:114: error: ISO C++ forbids declaration of ‘CURLSH’ with no type
curl_adapter.cpp:114: error: expected ‘;’ before ‘*’ token
curl_adapter.cpp:116: error: expected ‘;’ before ‘private’
curl_adapter.cpp:136: error: ISO C++ forbids declaration of ‘CURLSH’ with no type
curl_adapter.cpp:136: error: expected ‘;’ before ‘*’ token
curl_adapter.cpp:169: error: ‘CURL’ has not been declared
curl_adapter.cpp:169: error: ‘curl_lock_data’ has not been declared
curl_adapter.cpp:170: error: ‘curl_lock_access’ has not been declared
curl_adapter.cpp:173: error: ‘CURL’ has not been declared
curl_adapter.cpp:173: error: ‘curl_lock_data’ has not been declared
curl_adapter.cpp:176: error: ‘CURL’ has not been declared
curl_adapter.cpp:176: error: ‘curl_lock_data’ has not been declared
curl_adapter.cpp:177: error: ‘curl_lock_access’ has not been declared
curl_adapter.cpp:184: error: ‘CURL’ has not been declared
curl_adapter.cpp:184: error: ‘curl_lock_data’ has not been declared
curl_adapter.cpp: In destructor ‘gnash::<unnamed>::CurlSession::~CurlSession()’:
curl_adapter.cpp:209: error: ‘CURLSHcode’ was not declared in this scope
curl_adapter.cpp:209: error: expected ‘;’ before ‘code’
curl_adapter.cpp:211: error: ‘code’ was not declared in this scope
curl_adapter.cpp:211: error: ‘_shandle’ was not declared in this scope
curl_adapter.cpp:211: error: ‘curl_share_cleanup’ was not declared in this scope
curl_adapter.cpp:211: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:216: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:220: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:223: error: ‘_shandle’ was not declared in this scope
curl_adapter.cpp:224: error: ‘curl_global_cleanup’ was not declared in this scope
curl_adapter.cpp: In constructor ‘gnash::<unnamed>::CurlSession::CurlSession()’:
curl_adapter.cpp:235: error: class ‘gnash::<unnamed>::CurlSession’ does not have any field named ‘_shandle’
curl_adapter.cpp:244: error: ‘CURL_GLOBAL_ALL’ was not declared in this scope
curl_adapter.cpp:244: error: ‘curl_global_init’ was not declared in this scope
curl_adapter.cpp:246: error: ‘_shandle’ was not declared in this scope
curl_adapter.cpp:246: error: ‘curl_share_init’ was not declared in this scope
curl_adapter.cpp:251: error: ‘CURLSHcode’ was not declared in this scope
curl_adapter.cpp:251: error: expected ‘;’ before ‘ccode’
curl_adapter.cpp:254: error: ‘ccode’ was not declared in this scope
curl_adapter.cpp:254: error: ‘CURLSHOPT_LOCKFUNC’ was not declared in this scope
curl_adapter.cpp:255: error: ‘curl_share_setopt’ was not declared in this scope
curl_adapter.cpp:256: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:257: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:261: error: ‘CURLSHOPT_UNLOCKFUNC’ was not declared in this scope
curl_adapter.cpp:263: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:264: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:268: error: ‘CURLSHOPT_SHARE’ was not declared in this scope
curl_adapter.cpp:268: error: ‘CURL_LOCK_DATA_COOKIE’ was not declared in this scope
curl_adapter.cpp:269: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:270: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:274: error: ‘CURL_LOCK_DATA_DNS’ was not declared in this scope
curl_adapter.cpp:275: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:276: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp:280: error: ‘CURLSHOPT_USERDATA’ was not declared in this scope
curl_adapter.cpp:281: error: ‘CURLSHE_OK’ was not declared in this scope
curl_adapter.cpp:282: error: ‘curl_share_strerror’ was not declared in this scope
curl_adapter.cpp: At global scope:
curl_adapter.cpp:289: error: variable or field ‘lockSharedHandle’ declared void
curl_adapter.cpp:289: error: ‘CURL’ was not declared in this scope
curl_adapter.cpp:289: error: ‘handle’ was not declared in this scope
curl_adapter.cpp:289: error: ‘curl_lock_data’ was not declared in this scope
curl_adapter.cpp:290: error: ‘curl_lock_access’ was not declared in this scope
curl_adapter.cpp:1426: error: expected ‘}’ at end of input
curl_adapter.cpp:1426: error: expected ‘}’ at end of input
make[2]: *** [libgnashbase_la-curl_adapter.lo] Error 1
make[2]: Leaving directory `/home/mshorts/Desktop/gnash-0.8.7/libbase'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/mshorts/Desktop/gnash-0.8.7'
make: *** [check] Error 2
:p

---

### Post by jarviser on 2010-07-25
Gnash is a movie player available from the Synaptic Package Manager or Ubuntu Software Manager. No need to compile, surely.

I assume you tried adobe-flashplugin from Synaptic?  Unless it needs to address more than 4GB of memory, I would have thought it would work.

The Ubuntu advice (which may be out of date now) on flash is

*Adobe's 64-bit trial has ended and the current version is not secure. Please use either flashplugin-nonfree (Hardy) or **flashplugin-installer** (Jaunty+) to install Flash on a 64 bit system. *

flashplugin-installer is also in Synaptic.

---

### Post by texaswriter on 2010-07-26
+1 

I second the advice to install flash nonfree or the other one..

I had a problem with GNASH and the other stuff it installs when you let firefox initiate the plugin find... 

I have no problems with flash plugin nonfree... <<<--- I usually use that one...

---

