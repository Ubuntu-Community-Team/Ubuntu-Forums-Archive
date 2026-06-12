---
title: "installing cowpatty  buffer overflow  (8.10)"
date: 2009-04-01
forum: General Help
---

### Post by evrkusd on 2009-04-01
i'm trying to install cowpatty and i'm getting this error. there was another post about this but none of the solutions helped solve my problem.

cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o sha1.o sha1.c
In function ‘memcpy’,
    inlined from ‘hmac_sha1_vector’ at sha1.c:111:
/usr/include/bits/string3.h:52: warning: call to __builtin___memcpy_chk will always overflow destination buffer
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o utils.o utils.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o cowpatty.o cowpatty.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o genpmk.o genpmk.c
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result
genpmk.c:278: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:279: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:280: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb genpmk.c -o genpmk utils.o sha1.o -lpcap -lcrypto
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result
genpmk.c:278: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:279: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
genpmk.c:280: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result

when i try to run cowpatty i get the result:

genpmk 1.0 - WPA-PSK precomputation attack. <jwright@hasborg.com>
File /home/qfqw/Desktop/hash exists, appending new data.
*** buffer overflow detected ***: ./genpmk terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x427e86d8]
/lib/tls/i686/cmov/libc.so.6[0x427e6800]
./genpmk[0x8049c27]
./genpmk[0x8049efc]
./genpmk[0x804a028]
./genpmk[0x8049262]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x42704685]
./genpmk[0x8048bb1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:04 1958307    /home/qfqw/cowpatty-4.2/genpmk
0804b000-0804c000 r--p 00002000 08:04 1958307    /home/qfqw/cowpatty-4.2/genpmk
0804c000-0804d000 rw-p 00003000 08:04 1958307    /home/qfqw/cowpatty-4.2/genpmk
09b8e000-09baf000 rw-p 09b8e000 00:00 0          [heap]
426cf000-426e9000 r-xp 00000000 08:02 129300     /lib/ld-2.8.90.so
426ea000-426eb000 r--p 0001a000 08:02 129300     /lib/ld-2.8.90.so
426eb000-426ec000 rw-p 0001b000 08:02 129300     /lib/ld-2.8.90.so
426ee000-42846000 r-xp 00000000 08:02 145540     /lib/tls/i686/cmov/libc-2.8.90.so
42846000-42848000 r--p 00158000 08:02 145540     /lib/tls/i686/cmov/libc-2.8.90.so
42848000-42849000 rw-p 0015a000 08:02 145540     /lib/tls/i686/cmov/libc-2.8.90.so
42849000-4284c000 rw-p 42849000 00:00 0 
4284e000-42850000 r-xp 00000000 08:02 145774     /lib/tls/i686/cmov/libdl-2.8.90.so
42850000-42851000 r--p 00001000 08:02 145774     /lib/tls/i686/cmov/libdl-2.8.90.so
42851000-42852000 rw-p 00002000 08:02 145774     /lib/tls/i686/cmov/libdl-2.8.90.so
42854000-4287d000 r-xp 00000000 08:02 202978     /usr/lib/libpcap.so.0.9.8
4287d000-4287e000 r--p 00028000 08:02 202978     /usr/lib/libpcap.so.0.9.8
4287e000-4287f000 rw-p 00029000 08:02 202978     /usr/lib/libpcap.so.0.9.8
429b4000-429c8000 r-xp 00000000 08:02 202898     /usr/lib/libz.so.1.2.3.3
429c8000-429ca000 rw-p 00013000 08:02 202898     /usr/lib/libz.so.1.2.3.3
42b63000-42b70000 r-xp 00000000 08:02 129354     /lib/libgcc_s.so.1
42b70000-42b71000 r--p 0000c000 08:02 129354     /lib/libgcc_s.so.1
42b71000-42b72000 rw-p 0000d000 08:02 129354     /lib/libgcc_s.so.1
438b1000-439ec000 r-xp 00000000 08:02 234851     /usr/lib/i686/cmov/libcrypto.so.0.9.8
439ec000-439ed000 ---p 0013b000 08:02 234851     /usr/lib/i686/cmov/libcrypto.so.0.9.8
439ed000-439f4000 r--p 0013b000 08:02 234851     /usr/lib/i686/cmov/libcrypto.so.0.9.8
439f4000-43a02000 rw-p 00142000 08:02 234851     /usr/lib/i686/cmov/libcrypto.so.0.9.8
43a02000-43a06000 rw-p 43a02000 00:00 0 
b80bf000-b80c1000 rw-p b80bf000 00:00 0 
b80cf000-b80d4000 rw-p b80cf000 00:00 0 
b80d4000-b80d5000 r-xp b80d4000 00:00 0          [vdso]
bfac0000-bfad5000 rw-p bffeb000 00:00 0          [stack]
Aborted

i have libssl-dev
and libpcap0.8 dev installed
i tried an older version of gcc
i have libdigest-hmac-perl installed.
i'm not sure what else to do. any suggestions would be appreciated.

---

### Post by ibuclaw on 2009-04-01
> 
**/usr/include/bits/string3.h:52: warning: call to __builtin___memcpy_chk will always overflow destination buffer**


That may be your issue ...

Where did you get the source code from?

Regards
Iain

---

### Post by evrkusd on 2009-04-01
i got the source code from the cowpatty site. i figured that that line was the problem but i don't really know what it means or how to fix it. any ideas?

---

### Post by ibuclaw on 2009-04-02
OK, I had a look. It appears that the **sizeof(context)** was far greater than the **sizeof(cached.k_opad)** and **sizeof(cached.k_ipad)**. So memcpy overflowed both char[] stacks.

I'm not sure what the state of SHA1 was a few years ago when this program seemed to be written, but the size of the struct SHA_CTX appears to have grown to 96, rather than 65 (the number that was hard coded into cowpatty).

Not that that means anything to you ;)

Here is a patch:
```

diff -Naur cowpatty-4.2/cowpatty.c cowpatty-patch/cowpatty.c
--- cowpatty-4.2/cowpatty.c	2009-04-02 17:04:06.000000000 +0100
+++ cowpatty-patch/cowpatty.c	2009-04-02 14:56:19.000000000 +0100
@@ -697,7 +697,7 @@
 		 */
 		if (fret < 8 || fret > 63) {
 			if (opt->verbose) {
-				printf("Invalid passphrase length: %s (%d).\n",
+				printf("Invalid passphrase length: %s (%ld).\n",
 				       passphrase, strlen(passphrase));
 			}
 			continue;
diff -Naur cowpatty-4.2/genpmk.c cowpatty-patch/genpmk.c
--- cowpatty-4.2/genpmk.c	2009-04-02 17:04:06.000000000 +0100
+++ cowpatty-patch/genpmk.c	2009-04-02 16:59:15.000000000 +0100
@@ -212,8 +212,8 @@
 		}
 		
 		printf("File %s exists, appending new data.\n", opt.hashfile);
-		fopen(opt.hashfile, "ab");
-		if (fopen == NULL) {
+		fpout = fopen(opt.hashfile, "ab");
+		if (fpout == NULL) {
 			perror("fopen");
 			exit(-1);
 		}
@@ -244,7 +244,7 @@
 		 */
 		if (fret < 8 || fret > 63) {
 			if (opt.verbose) {
-				printf("Invalid passphrase length: %s (%d).\n",
+				printf("Invalid passphrase length: %s (%ld).\n",
 				       passphrase, strlen(passphrase));
 			}
 			continue;
@@ -275,11 +275,15 @@
 			sizeof(rec.pmk));
 
 		/* Write the record contents to the file */
-		fwrite(&rec.rec_size, sizeof(rec.rec_size), 1, fpout);
-		fwrite(passphrase, strlen(passphrase), 1, fpout);
-		fwrite(rec.pmk, sizeof(rec.pmk), 1, fpout);
-
-	}
+        int fwsize = 0;
+        fwsize += fwrite(&rec.rec_size, sizeof(rec.rec_size), 1, fpout);
+        fwsize += fwrite(passphrase, strlen(passphrase), 1, fpout);
+        fwsize += fwrite(rec.pmk, sizeof(rec.pmk), 1, fpout);
+        /* Sanity check */
+        if(fwsize != 3) {
+            perror("fwrite");
+        }
+    }
 
 	fclose(fpin);
 	fclose(fpout);
diff -Naur cowpatty-4.2/sha1.c cowpatty-patch/sha1.c
--- cowpatty-4.2/sha1.c	2009-04-02 17:04:06.000000000 +0100
+++ cowpatty-patch/sha1.c	2009-04-02 16:27:39.000000000 +0100
@@ -58,8 +58,8 @@
 		      unsigned int *len, unsigned char *mac, int usecached)
 {
 	SHA1_CTX context;
-	unsigned char k_ipad[65];	/* inner padding - key XORd with ipad */
-	unsigned char k_opad[65];	/* outer padding - key XORd with opad */
+	unsigned char k_ipad[96];	/* inner padding - key XORd with ipad */
+	unsigned char k_opad[96];	/* outer padding - key XORd with opad */
 	int i;
 
 	/* the HMAC_SHA1 transform looks like:
@@ -67,8 +67,8 @@
 	 * SHA1(K XOR opad, SHA1(K XOR ipad, text))
 	 *
 	 * where K is an n byte key
-	 * ipad is the byte 0x36 repeated 64 times
-	 * opad is the byte 0x5c repeated 64 times
+	 * ipad is the byte 0x36 repeated 95 times
+	 * opad is the byte 0x5c repeated 95 times
 	 * and text is the data being protected */
 
 	if (usecached == NOCACHED || !cached.k_ipad_set || !cached.k_opad_set) {
@@ -82,7 +82,7 @@
 		memcpy(k_opad, key, key_len);
 
 		/* XOR key with ipad and opad values */
-		for (i = 0; i < 64; i++) {
+		for (i = 0; i < 95; i++) {
 			k_ipad[i] ^= 0x36;
 			k_opad[i] ^= 0x5c;
 		}
diff -Naur cowpatty-4.2/sha1.h cowpatty-patch/sha1.h
--- cowpatty-4.2/sha1.h	2009-04-02 16:46:57.000000000 +0100
+++ cowpatty-patch/sha1.h	2009-04-02 17:02:15.000000000 +0100
@@ -44,8 +44,8 @@
 #define NOCACHED 0
 
 typedef struct {
-	unsigned char k_ipad[65];
-	unsigned char k_opad[65];
+	unsigned char k_ipad[96];
+	unsigned char k_opad[96];
 	unsigned char k_ipad_set;
 	unsigned char k_opad_set;
 } SHA1_CACHE;

```
All I've done is increased the size of the char array from 65 to 96.
Also, I am a bit of a gcc warning/grammar Nazi, so I silenced all warnings for fopen and fwrite too.

To apply it, create a file in the cowpatty directory.
ie:
```
gedit cowpatty.patch
```
Paste it inside, then Save+Quit.

Then run:
```
patch -p1 < cowpatty.patch
```

Then:
```
make clean && make
```

I went to the liberty of testing it beforehand, and it still works as it's expected to.

Regards
Iain

---

### Post by evrkusd on 2009-04-02
hey, thanks a lot for the reply/ the work you put into it. it now installs with no errors :) 

i'mstill having some issues with compiling other things but i'm not sure if they're related and i guess i'll leave those for another day. heh. 

thanks again.

---

### Post by gavshouse on 2009-09-03
hey i had this problem as thanks tinivole, just thought id post a thank you

---

### Post by funkyeah on 2009-10-07
your status is right, man, you should've gone to university.

there'd be other smart fellows like yourself.  you're good.

---

### Post by SamPz3r on 2009-10-21
Thanks a lot! It worked perfectly, I completely agree with funkyeah.

---

### Post by werzy33 on 2010-07-01
Thanks, solved the buffer overflow problem for me.  FYI, problem still exists in Ubuntu Lucid 10.04, for anyone trying resolve this issue.

---

