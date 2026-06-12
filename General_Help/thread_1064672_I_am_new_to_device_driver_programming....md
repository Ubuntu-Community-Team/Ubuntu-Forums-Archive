---
title: "I am new to device driver programming..."
date: 2009-02-09
forum: General Help
---

### Post by manasR on 2009-02-09
Hi 
  I am new to device driver programming in Linix. So could you please let me know the general steps required for above development. 

currently i am going through the bootloader.c file..i am not able to understand.....could you please briefly explain the code below....

```
/*
2  * Copyright (C) 2008 The Android Open Source Project
3  * All rights reserved.
4  *
5  * Redistribution and use in source and binary forms, with or without
6  * modification, are permitted provided that the following conditions
7  * are met:
8  *  * Redistributions of source code must retain the above copyright
9  *    notice, this list of conditions and the following disclaimer.
10  *  * Redistributions in binary form must reproduce the above copyright
11  *    notice, this list of conditions and the following disclaimer in
12  *    the documentation and/or other materials provided with the 
13  *    distribution.
14  *
15  * THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
16  * "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
17  * LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
18  * FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
19  * COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
20  * INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
21  * BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
22  * OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED 
23  * AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
24  * OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT
25  * OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
26  * SUCH DAMAGE.
27  */
28 
29 #include <boot/boot.h>
30 #include <boot/flash.h>
31 #include <boot/board.h>
32 #include <boot/usb.h>
33 
34 #include <boot/bootimg.h>
35 #include <boot/tags.h>
36 
37 #include <boot/gpio.h>
38 
39 #define VERSION "0.5"
40 
41 #define REQUIRE_SIGNATURE 0
42 
43 #if REQUIRE_SIGNATURE
44 unsigned key_engineering[2 + 64 + 64] = {
45     64,0x5b022317,-60769447,648742897,-13657530,585562035,591851935,
46     454860199,-1809625305,1868200692,-155297008,-1688439840,-1333607631,
47     -483027189,-2051438457,1030069735,819944365,2133377257,-1978924214,
48     2109678622,1974978919,-1811463608,765849268,1984092281,921245328,
49     -1055062768,1487475997,1209618652,871985152,-611178965,-2057018571,
50     335641539,-1196119550,1550548229,-356223887,1909799623,1281016007,
51     957001635,1005656532,-1027634024,-1576447610,-1917246637,589192795,
52     -1137386186,-1958135372,1933245070,64958951,-1820428322,-1577697840,
53     1824253519,555306239,-1588272058,-1925773018,1205934271,-836584444,
54     -1140961670,-185198349,1293769947,37045923,1516796974,-297288651,
55     651582073,-1337054592,-543971216,-1706823885,-1040652818,-594113104,
56     260093481,-1277656496,56493468,1577037283,773995876,244894933,
57     -2075797967,783894843,880611008,-1433369702,380946504,-2081431477,
58     1377832804,2089455451,-410001201,1245307237,-1228170341,-2062569137,
59     -1327614308,-1671042654,1242248660,-418803721,40890010,-1806767460,
60     -1468529145,-1058158532,1243817302,-527795003,175453645,-210650325,
61     -827053868,-571422860,886300657,2129677324,846504590,-1413102805,
62     -1287448511,-1991140134,56194155,1375685594,-129884114,1393568535,
63     -1098719620,-935279550,1717137954,-1782544741,272581921,-669183778,
64     584824755,1434974827,-1122387971,-810584927,-2147338547,-937541680,
65     -313561073,5506366,-1594059648,-1744451574,1896015834,1496367069,
66     1742853908,508461291,1905056764
67 };
68 #endif
69 
70 const char *get_fastboot_version(void)
71 {
72     return VERSION;
73 }
74 
75 unsigned linux_type = 0;
76 unsigned linux_tags = 0;
77 
78 unsigned ramdisk_addr = 0x10400000;
79 unsigned ramdisk_size = 0;
80 unsigned kernel_addr = 0x10008000;
81 unsigned kernel_size = 0;
82 
83 static void fixup_tags(unsigned *tags, unsigned *out, const char *cmdline)
84 {
85     unsigned *newtags = (unsigned *) 0x10004000;
86     unsigned *np = newtags;
87     unsigned n;
88     char *oldcmdline = "";
89     
90     if(cmdline == 0) cmdline = "";
91 
92         /* CORE */
93     *np++ = 2;
94     *np++ = 0x54410001;
95 
96     if(tags != 0) {
97         while(*tags) {
98             if(tags[1] == 0x54410001) {
99                     /* skip core tag */
100                 tags += tags[0];
101             } else if((tags[1] == 0x54420005) && (ramdisk_size != 0)) {
102                     /* skip ramdisk if we have one of our own */
103                 tags += tags[0];
104             } else if((tags[1] == 0x54410009) && (cmdline[0])) {
105                     /* skip existing cmdline so we can replace it */
106                 oldcmdline = (char*) (tags + 2);
107                 tags += tags[0];
108             } else {
109                     /* copy any unknown tags */
110                 n = tags[0];
111                 while(n-- > 0) {
112                     *np++ = *tags++;
113                 }
114             }
115         }
116     }
117 
118         /* create a ramdisk tag if we need to */
119     if(ramdisk_size) {
120         *np++ = 4;
121         *np++ = 0x54420005;
122         *np++ = ramdisk_addr;
123         *np++ = ramdisk_size;
124     }
125 
126     dprintf("cmdline: '%s'\n", oldcmdline);
127     dprintf("cmdline: '%s'\n", cmdline);
128     
129         /* create a cmdline tag if we need to */
130     if(cmdline[0]) {
131         int len;
132         char *str = (char*) (np + 2);
133         
134         len = strlen(oldcmdline);
135         if(len) {
136             memcpy(str, oldcmdline, len);
137             str += len;
138             *str++ = ' ';
139         }
140 
141         len = strlen(cmdline);
142         memcpy(str, cmdline, len);
143         str += len;
144         *str++ = 0;
145         
146             /* length in words */
147         len = ((str - ((char*) (np + 2))) + 3) / 4;
148 
149         dprintf("CMDLINE: '%s'\n", ((char*) (np + 2)));
150         
151         *np++ = 2 + len;
152         *np++ = 0x54410009;
153         
154         np += len;
155     }
156 
157         /* add footer tag */
158     *np++ = 0;
159     *np++ = 0;
160     
161         /* copy it all back to the original tags area */
162     while(newtags < np) {
163         *out++ = *newtags++;
164     }
165 }
166 
167 static char cmdline[BOOT_ARGS_SIZE];
168 
169 static void boot_linux(void)
170 {
171     unsigned *tags = (unsigned*) 0x10000100;
172     void (*entry)(unsigned,unsigned,unsigned) = (void*) kernel_addr;
173 
174     if(linux_type == 0) {
175         linux_type = board_machtype();
176     }
177     
178     fixup_tags((unsigned*) linux_tags, tags, cmdline);    
179 
180     entry(0, linux_type, tags);
181     
182     for(;;);
183 }
184 
185 /* convert a boot_image at kernel_addr into a kernel + ramdisk + tags */
186 static int init_boot_linux(void)
187 {
188     boot_img_hdr *hdr = (void*) kernel_addr;
189     unsigned page_mask = 2047;
190     unsigned kernel_actual;
191     unsigned ramdisk_actual;
192     unsigned second_actual;
193     
194     if((kernel_size < 2048) || memcmp(hdr->magic, BOOT_MAGIC, BOOT_MAGIC_SIZE)){
195         dprintf("bootimg: bad header\n");
196         return -1;
197     }
198 
199     if(hdr->page_size != 2048) {
200         dprintf("bootimg: invalid page size\n");
201         return -1;
202     }
203 
204     kernel_actual = (hdr->kernel_size + page_mask) & (~page_mask);
205     ramdisk_actual = (hdr->ramdisk_size + page_mask) & (~page_mask);
206     second_actual = (hdr->second_size + page_mask) & (~page_mask);
207     
208     if(kernel_size != (kernel_actual + ramdisk_actual + second_actual + 2048)) {
209         dprintf("bootimg: invalid image size");
210         return -1;
211     }
212 
213         /* XXX process commandline here */
214     if(hdr->cmdline[0]){
215         hdr->cmdline[BOOT_ARGS_SIZE - 1] = 0;
216         memcpy(cmdline, hdr->cmdline, BOOT_ARGS_SIZE);
217     }
218 
219         /* XXX how to validate addresses? */
220     ramdisk_addr = hdr->ramdisk_addr;
221     ramdisk_size = hdr->ramdisk_size;
222 
223     kernel_addr = hdr->kernel_addr;
224     kernel_size = hdr->kernel_size;
225     
226     dprintf("bootimg: kernel addr=%x size=%x\n",
227             kernel_addr, kernel_size);
228     dprintf("bootimg: ramdisk addr=%x size=%x\n",
229             ramdisk_addr, ramdisk_size);
230     
231     memcpy((void*) ramdisk_addr, 
232            hdr->magic + 2048 + kernel_actual,
233            ramdisk_size);
234     
235     memcpy((void*) kernel_addr,
236            hdr->magic + 2048,
237            kernel_size);
238     
239     return 0; 
240 }
241 
242 static struct usb_endpoint *ep1in, *ep1out;
243 static struct usb_request *rx_req, *tx_req;
244 static unsigned rx_addr;
245 static unsigned rx_length;
246 
247 static char *cmdbuf;
248 
249 static void usb_rx_cmd_complete(struct usb_request *req, unsigned actual, int status);
250 static void usb_rx_data_complete(struct usb_request *req, unsigned actual, int status);
251 
252 static void rx_cmd(void)
253 {
254     struct usb_request *req = rx_req;
255     req->buf = cmdbuf;
256     req->length = 4096;
257     req->complete = usb_rx_cmd_complete;
258     usb_queue_req(ep1out, req);
259 }
260 
261 static void rx_data(void)
262 {
263     struct usb_request *req = rx_req;
264     req->buf = (void*) rx_addr;
265     req->length = (rx_length > 4096) ? 4096 : rx_length;
266     req->complete = usb_rx_data_complete;
267     usb_queue_req(ep1out, req);
268 }
269 
270 static void tx_status(const char *status)
271 {
272     struct usb_request *req = tx_req;
273     int len = strlen(status);
274 //    dprintf("tx_status('%s')\n", status);
275     memcpy(req->buf, status, len);
276     req->length = len;
277     req->complete = 0;
278     usb_queue_req(ep1in, req);
279 }
280 
281 static void usb_rx_data_complete(struct usb_request *req, unsigned actual, int status)
282 {
283     if(status != 0) return;
284 
285     if(actual > rx_length) {
286         actual = rx_length;
287     }
288 
289     rx_addr += actual;
290     rx_length -= actual;
291     
292     if(rx_length > 0) {
293         rx_data();
294     } else {
295         tx_status("OKAY");
296         rx_cmd();
297     }
298 }
299 
300 static unsigned hex2unsigned(char *x)
301 {
302     unsigned n = 0;
303 
304     while(*x) {
305         switch(*x) {
306         case '0': case '1': case '2': case '3': case '4':
307         case '5': case '6': case '7': case '8': case '9':
308             n = (n << 4) | (*x - '0');
309             break;
310         case 'a': case 'b': case 'c':
311         case 'd': case 'e': case 'f':
312             n = (n << 4) | (*x - 'a' + 10);
313             break;
314         case 'A': case 'B': case 'C':
315         case 'D': case 'E': case 'F':
316             n = (n << 4) | (*x - 'A' + 10);
317             break;
318         default:
319             return n;
320         }
321         x++;
322     }
323 
324     return n;
325 }
326 
327 static void num_to_hex8(unsigned n, char *out)
328 {
329     static char tohex[16] = "0123456789abcdef";
330     int i;
331     for(i = 7; i >= 0; i--) {
332         out[i] = tohex[n & 15];
333         n >>= 4;
334     }
335     out[8] = 0;
336 }
337 
338 extern char serialno[];
339 
340 static char signature[SIGNATURE_SIZE];
341 
342 static void usb_rx_cmd_complete(struct usb_request *req, unsigned actual, int status)
343 {
344     if(status != 0) return;
345     
346     if(actual > 4095) actual = 4095;    
347     cmdbuf[actual] = 0;
348 
349     dprintf("\n> %s\n",cmdbuf);
350     
351 //    dprintf("usb_rx_cmd_complete() '%s'\n", cmdbuf);  
352     
353     if(memcmp(cmdbuf, "reboot", 6) == 0) {
354         tx_status("OKAY");
355         rx_cmd();
356         mdelay(100);
357         board_reboot();
358     }
359 #if 0
360     if(memcmp(cmdbuf, "debug:", 6) == 0) {
361         void debug(char *cmd, char *resp);
362         memcpy(cmdbuf, "OKAY", 5);
363         tx_status(cmdbuf);
364         rx_cmd();
365         mdelay(5000);
366         dprintf("NOW!\n");
367         debug(cmdbuf + 6, cmdbuf + 4);
368         return;
369     }
370 #endif
371     if(memcmp(cmdbuf, "getvar:", 7) == 0) {
372         char response[64];
373         strcpy(response,"OKAY");
374         
375         if(!strcmp(cmdbuf + 7, "version")) {
376             strcpy(response + 4, VERSION);
377         } else if(!strcmp(cmdbuf + 7, "product")) {
378             strcpy(response + 4, PRODUCTNAME);
379         } else if(!strcmp(cmdbuf + 7, "serialno")) {
380             strcpy(response + 4, serialno);
381         } else {
382             board_getvar(cmdbuf + 7, response + 4);
383         }
384         tx_status(response);
385         rx_cmd();
386         return;
387     }
388 
389     if(memcmp(cmdbuf, "download:", 9) == 0) {
390         char status[16];
391         rx_addr = kernel_addr;
392         rx_length = hex2unsigned(cmdbuf + 9);
393         if (rx_length > (64*1024*1024)) {
394             tx_status("FAILdata too large");
395             rx_cmd();
396             return;
397         }
398         kernel_size = rx_length;
399         dprintf("recv data addr=%x size=%x\n", rx_addr, rx_length); 
400         strcpy(status,"DATA");
401         num_to_hex8(rx_length, status + 4);
402         tx_status(status);
403         rx_data();
404         return;
405     }
406 
407     if(memcmp(cmdbuf, "erase:", 6) == 0){
408         struct ptentry *ptn;
409         ptn = flash_find_ptn(cmdbuf + 6);
410         if(ptn == 0) {
411             tx_status("FAILpartition does not exist");
412             rx_cmd();
413             return;
414         }
415         dprintf("erasing '%s'\n", ptn->name);
416         cprintf("erasing '%s'", ptn->name);
417         if(flash_erase(ptn)) {
418             tx_status("FAILfailed to erase partition");
419             rx_cmd();
420             cprintf(" - FAIL\n");
421             return;
422         } else {
423             dprintf("partition '%s' erased\n", ptn->name);
424             cprintf(" - OKAY\n");
425         }
426         tx_status("OKAY");
427         rx_cmd();
428         return;
429     }
430 
431     if(memcmp(cmdbuf, "flash:", 6) == 0){
432         struct ptentry *ptn;
433         int extra = 0;
434         ptn = flash_find_ptn(cmdbuf + 6);
435         if(kernel_size == 0) {
436             tx_status("FAILno image downloaded");
437             rx_cmd();
438             return;
439         }
440         if(ptn == 0) {
441             tx_status("FAILpartition does not exist");
442             rx_cmd();
443             return;
444         }
445         if(!strcmp(ptn->name,"boot") || !strcmp(ptn->name,"recovery")) {
446             if(memcmp((void*) kernel_addr, BOOT_MAGIC, BOOT_MAGIC_SIZE)) {
447                 tx_status("FAILimage is not a boot image");
448                 rx_cmd();
449                 return;
450             }
451         }
452 #if REQUIRE_SIGNATURE
453         {
454             unsigned char digest[DIGEST_SIZE];
455             compute_digest((void*) kernel_addr, kernel_size, digest);
456             if (is_signature_okay(digest, signature, key_engineering)) {
457                 dprintf("verified by engineering key\n");
458             } else {
459                 tx_status("FAILsignature did not verify");
460                 rx_cmd();
461                 return;
462             }
463         }
464 #endif
465         if(!strcmp(ptn->name,"system") || !strcmp(ptn->name,"userdata")) {
466             extra = 64;
467         } else {
468             kernel_size = (kernel_size + 2047) & (~2047);
469         }
470         dprintf("writing %d bytes to '%s'\n", 
471                 kernel_size, ptn->name);
472         cprintf("writing '%s' (%d bytes)", ptn->name, kernel_size);
473         if(flash_write(ptn, extra, (void*) kernel_addr, kernel_size)) {
474             tx_status("FAILflash write failure");
475             rx_cmd();
476             cprintf(" - FAIL\n");
477             return;
478         } else {
479             dprintf("partition '%s' updated\n", ptn->name);
480             cprintf(" - OKAY\n");
481         }
482         tx_status("OKAY");
483         rx_cmd();
484         return;
485     }
486     if(memcmp(cmdbuf, "boot", 4) == 0) {
487         if(init_boot_linux()) {
488             tx_status("FAILinvalid boot image");
489             rx_cmd();
490             return;
491         }
492         dprintf("booting linux...\n");
493         cprintf("\nbooting linux...\n");
494         tx_status("OKAY");
495         mdelay(10);
496         usb_shutdown();
497         boot_linux();
498         return;
499     }
500     if(memcmp(cmdbuf, "signature", 9) == 0) {
501         if (kernel_size != SIGNATURE_SIZE) {
502             tx_status("FAILsignature not 256 bytes long");
503             rx_cmd();
504             return;
505         }
506         memcpy(signature, (void*)kernel_addr, SIGNATURE_SIZE);
507         tx_status("OKAY");
508         rx_cmd();
509         return;
510     }
511 
512     tx_status("FAILinvalid command");
513     rx_cmd();
514 }
515 
516 void usb_status(unsigned online, unsigned highspeed)
517 {
518     if(online) {
519         dprintf("usb: online (%s)\n", highspeed ? "highspeed" : "fullspeed");
520         rx_cmd();
521     }
522 }
523 
524 void usbloader_init(void)
525 {
526     usb_init();
527 
528     ep1out = usb_endpoint_alloc(1, 0, 512);
529     ep1in = usb_endpoint_alloc(1, 1, 512);
530     rx_req = usb_request_alloc(4096);
531     tx_req = usb_request_alloc(4096);
532     cmdbuf = rx_req->buf;
533 
534     boot_register_poll_func(usb_poll);
535 }

```

Thanks in advance
Manas R

---

