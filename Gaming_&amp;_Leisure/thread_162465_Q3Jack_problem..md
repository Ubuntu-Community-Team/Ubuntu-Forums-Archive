---
title: "Q3Jack problem."
date: 2006-04-19
forum: Gaming &amp; Leisure
---

### Post by psibaboon on 2006-04-19
Hi.

I installed Quake 3 on my machine (Ubuntu 5.10, kernel 2.6.12-9-386) today. In order to enable sound, I tried installing q3jack. First, I installed the packages jackd (jackd_0.99.0-2ubuntu1_i386.deb), libjack0.80.0-0 (libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb), and libsamplerate0 (libsamplerate0_0.1.2-2_i386.deb). I then tried installing q3jack 0.2. This is what make spat out:

```

gcc -O2 -fPIC -c -Wall -DHAVE_IOCTL_INT_ULONG_DOTS  -o q3jack.o q3jack.c
q3jack.c:53:23: error: jack/jack.h: No such file or directory
q3jack.c:54:29: error: jack/ringbuffer.h: No such file or directory
q3jack.c:55:24: error: samplerate.h: No such file or directory
q3jack.c:95: error: syntax error before ‘*’ token
q3jack.c:95: warning: type defaults to ‘int’ in declaration of ‘client’
q3jack.c:95: warning: data definition has no type or storage class
q3jack.c:96: error: syntax error before ‘*’ token
q3jack.c:96: warning: type defaults to ‘int’ in declaration of ‘out’
q3jack.c:96: warning: data definition has no type or storage class
q3jack.c:97: error: syntax error before ‘*’ token
q3jack.c:97: warning: type defaults to ‘int’ in declaration of ‘src_state’
q3jack.c:97: warning: data definition has no type or storage class
q3jack.c:199: error: syntax error before ‘*’ token
q3jack.c: In function ‘q3jack_output’:
q3jack.c:201: error: ‘jack_default_audio_sample_t’ undeclared (first use in this  function)
q3jack.c:201: error: (Each undeclared identifier is reported only once
q3jack.c:201: error: for each function it appears in.)
q3jack.c:201: error: ‘jack_out’ undeclared (first use in this function)
q3jack.c:201: error: syntax error before ‘)’ token
q3jack.c:203: error: ‘nframes’ undeclared (first use in this function)
q3jack.c:204: error: ‘data’ undeclared (first use in this function)
q3jack.c: At top level:
q3jack.c:208: error: syntax error before ‘nframes’
q3jack.c: In function ‘q3jack_process’:
q3jack.c:212: warning: implicit declaration of function ‘src_callback_read’
q3jack.c:212: error: ‘nframes’ undeclared (first use in this function)
q3jack.c: At top level:
q3jack.c:221: error: syntax error before ‘jackrate’
q3jack.c: In function ‘q3jack_set_sample_rate’:
q3jack.c:223: error: ‘jackrate’ undeclared (first use in this function)
q3jack.c: In function ‘q3jack_xrun’:
q3jack.c:233: warning: implicit declaration of function ‘jack_get_buffer_size’
q3jack.c: In function ‘q3jack_close’:
q3jack.c:249: warning: implicit declaration of function ‘jack_client_close’
q3jack.c:250: warning: implicit declaration of function ‘src_delete’
q3jack.c: In function ‘q3jack_open’:
q3jack.c:285: warning: implicit declaration of function ‘src_callback_new’
q3jack.c:285: error: ‘SRC_SINC_FASTEST’ undeclared (first use in this function)
q3jack.c:285: warning: assignment makes pointer from integer without a cast
q3jack.c:301: warning: implicit declaration of function ‘jack_client_new’
q3jack.c:301: warning: assignment makes pointer from integer without a cast
q3jack.c:308: warning: implicit declaration of function ‘jack_set_process_callba ck’
q3jack.c:309: warning: implicit declaration of function ‘jack_set_sample_rate_ca llback’
q3jack.c:310: warning: implicit declaration of function ‘jack_set_xrun_callback’
q3jack.c:311: warning: implicit declaration of function ‘jack_on_shutdown’
q3jack.c:313: warning: implicit declaration of function ‘jack_port_register’
q3jack.c:313: error: ‘JACK_DEFAULT_AUDIO_TYPE’ undeclared (first use in this fun ction)
q3jack.c:313: error: ‘JackPortIsOutput’ undeclared (first use in this function)
q3jack.c:313: warning: assignment makes pointer from integer without a cast
q3jack.c:314: warning: assignment makes pointer from integer without a cast
q3jack.c:316: warning: implicit declaration of function ‘jack_get_sample_rate’
q3jack.c:319: warning: implicit declaration of function ‘jack_activate’
q3jack.c:342: warning: implicit declaration of function ‘jack_get_ports’
q3jack.c:342: error: ‘JackPortIsTerminal’ undeclared (first use in this function )
q3jack.c:342: error: ‘JackPortIsInput’ undeclared (first use in this function)
q3jack.c:342: warning: assignment makes pointer from integer without a cast
q3jack.c:361: warning: implicit declaration of function ‘jack_connect’
q3jack.c:361: warning: implicit declaration of function ‘jack_port_name’
make: *** [q3jack.so] Error 1

```

I then tried joss 0.3. Got nearly identical output...

```

gcc -O2 -fPIC -c -Wall -DHAVE_IOCTL_INT_ULONG_DOTS  -o joss.o joss.c
joss.c:54:23: error: jack/jack.h: No such file or directory
joss.c:55:29: error: jack/ringbuffer.h: No such file or directory
joss.c:56:24: error: samplerate.h: No such file or directory
joss.c:104: error: syntax error before ‘*’ token
joss.c:104: warning: type defaults to ‘int’ in declaration of ‘client’
joss.c:104: warning: data definition has no type or storage class
joss.c:105: error: syntax error before ‘*’ token
joss.c:105: warning: type defaults to ‘int’ in declaration of ‘out’
joss.c:105: warning: data definition has no type or storage class
joss.c:106: error: syntax error before ‘*’ token
joss.c:106: warning: type defaults to ‘int’ in declaration of ‘src_state’
joss.c:106: warning: data definition has no type or storage class
joss.c:230: error: syntax error before ‘*’ token
joss.c: In function ‘joss_output’:
joss.c:232: error: ‘jack_default_audio_sample_t’ undeclared (first use in this function)
joss.c:232: error: (Each undeclared identifier is reported only once
joss.c:232: error: for each function it appears in.)
joss.c:232: error: ‘jack_out’ undeclared (first use in this function)
joss.c:232: error: syntax error before ‘)’ token
joss.c:234: error: ‘nframes’ undeclared (first use in this function)
joss.c:235: error: ‘data’ undeclared (first use in this function)
joss.c: At top level:
joss.c:239: error: syntax error before ‘nframes’
joss.c: In function ‘joss_process’:
joss.c:243: warning: implicit declaration of function ‘src_callback_read’
joss.c:243: error: ‘nframes’ undeclared (first use in this function)
joss.c: At top level:
joss.c:252: error: syntax error before ‘jackrate’
joss.c: In function ‘joss_set_sample_rate’:
joss.c:254: error: ‘jackrate’ undeclared (first use in this function)
joss.c: In function ‘joss_xrun’:
joss.c:264: warning: implicit declaration of function ‘jack_get_buffer_size’
joss.c: In function ‘joss_close’:
joss.c:280: warning: implicit declaration of function ‘jack_client_close’
joss.c:281: warning: implicit declaration of function ‘src_delete’
joss.c: In function ‘joss_open’:
joss.c:333: warning: implicit declaration of function ‘src_callback_new’
joss.c:333: error: ‘SRC_SINC_FASTEST’ undeclared (first use in this function)
joss.c:333: warning: assignment makes pointer from integer without a cast
joss.c:349: warning: implicit declaration of function ‘jack_client_new’
joss.c:349: warning: assignment makes pointer from integer without a cast
joss.c:356: warning: implicit declaration of function ‘jack_set_process_callback’
joss.c:357: warning: implicit declaration of function ‘jack_set_sample_rate_callback’
joss.c:358: warning: implicit declaration of function ‘jack_set_xrun_callback’
joss.c:359: warning: implicit declaration of function ‘jack_on_shutdown’
joss.c:361: warning: implicit declaration of function ‘jack_port_register’
joss.c:361: error: ‘JACK_DEFAULT_AUDIO_TYPE’ undeclared (first use in this function)
joss.c:361: error: ‘JackPortIsOutput’ undeclared (first use in this function)
joss.c:361: warning: assignment makes pointer from integer without a cast
joss.c:362: warning: assignment makes pointer from integer without a cast
joss.c:364: warning: implicit declaration of function ‘jack_get_sample_rate’
joss.c:367: warning: implicit declaration of function ‘jack_activate’
joss.c:390: warning: implicit declaration of function ‘jack_get_ports’
joss.c:390: error: ‘JackPortIsTerminal’ undeclared (first use in this function)
joss.c:390: error: ‘JackPortIsInput’ undeclared (first use in this function)
joss.c:390: warning: assignment makes pointer from integer without a cast
joss.c:409: warning: implicit declaration of function ‘jack_connect’
joss.c:409: warning: implicit declaration of function ‘jack_port_name’
make: *** [joss.so] Error 1

```

Am I missing something?

---

### Post by joft on 2006-04-19
Hi,

did you install the package libjack0.80.0-dev before this compilation? Your log files say, that there are missing some header files, which come with such *-dev packages.

---

### Post by psibaboon on 2006-04-19
@joft

No. I'm downloading the package (libjack0.80.0-dev_0.99.0-2ubuntu1_i386.deb) now. I'll keep you posted!

Thanks.

---

### Post by psibaboon on 2006-04-25
@joft

 Very sorry for the delay... I was out of station for some time.

 Your idea worked, but I had to install the libsamplerate0-dev package as well.

 Thanks anyway.

---

